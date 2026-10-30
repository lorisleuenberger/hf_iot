# 04I - Eigene Idee 1: Konfigurierbare WiFi Messung

**Anforderung:** Programm aus 4.1 Eigene Idee 2 für ein Programm

### Idee
Ich möchte die WiFi Qualität anzeigen auf dem Display, plus eine Qualitäts LED (grün=gut,rot=schlecht).
Den Threshold für die Qualität mache ich über den Knob Input konfigurierbar.

### Umsetzung
Die WiFi Messung war grösstenteils schon umgesetzt, ich habe aber den Input bei der LED ergänzt:
```yaml
sensor:  
  - platform: wifi_signal # Reports the WiFi signal strength/RSSI in dB
    name: "WiFi Signal Percent"
    icon: "mdi:signal-variant"
    id: wifi_signal_percent
    update_interval: 1s
    filters:
    #Signal von dB in % umrechnen
      - lambda: return min(max(2 * (x + 100.0), 0.0), 100.0);
    unit_of_measurement: "Signal %"
    on_value:
      then:
        - if:
            condition:
              lambda: return x <= id(wifi_quality_threshold).state;
            then:
              - switch.turn_on: LED1
              - switch.turn_off: LED2
            else:
              - switch.turn_off: LED1
              - switch.turn_on: LED2
```

Über den Knob lese ich den Threshold in % aus. Die Anzeige wird sowohl bei Messung als auch Knob Änderung aktualisiert.
```yaml
sensor:
  - platform: adc
    pin: GPIO32
    id: wifi_quality_threshold
    name: "WiFi Quality Threshold"
    icon: "mdi:gauge"
    unit_of_measurement: "%"
    update_interval: 500ms
    attenuation: 12db
    filters:
      - calibrate_linear:
          - 0.0 -> 0.0
          - 3.1 -> 100.0
      - clamp:
          min_value: 0
          max_value: 100
    on_value:
      then:
        - if:
            condition:
              lambda: return id(wifi_signal_percent).state <= x;
            then:
              - switch.turn_on: LED1
              - switch.turn_off: LED2
            else:
              - switch.turn_off: LED1
              - switch.turn_on: LED2
```

Die Ausgabe beim Screen wurde angepasst:
```yaml
display:
  - platform: tm1637
    id: tm1637_display
    clk_pin: GPIO18
    dio_pin: GPIO17
    inverted: false
    length: 4
    intensity: 5
    update_interval: 500ms

    lambda: |-
      it.printf("%.0f", id(wifi_signal_percent).state);
```
Auf dem Video sehen sie den erfolgreichen Test.