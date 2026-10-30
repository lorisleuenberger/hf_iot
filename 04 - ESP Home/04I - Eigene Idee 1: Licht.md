# 04I - Eigene Idee 1: Licht

**Anforderung:** Programm aus 4.1 Eigene Idee 1 für ein Programm

### Idee
Ich möchte den Lichtsensor benutzen, um eine Lampe (zu Testzwecken die LED4) automatisch anzuschalten, wenn der LDR unter 20% ist.

### Umsetzung
Mit folgendem Code konnte ich die Daten aus dem Lichsensor verarbeiten und dann die LED4 ansteuern:

```yaml
sensor:
  - platform: adc
    pin: GPIO34
    id: ldr
    name: "LDR"
    attenuation: 12db
    samples: 10
    sampling_mode: avg
    update_interval: 500ms

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
              lambda: 'return x < 20.0;'
            then:
              - switch.turn_on: LED4
            else:
              - switch.turn_off: LED4
```

Zu Testzwecken habe ich noch den LDR Wert auf dem Display ausgegeben:

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
      it.printf("%.0f", id(ldr).state);
```

Auf dem Video sehen sie den erfolgreichen Test.