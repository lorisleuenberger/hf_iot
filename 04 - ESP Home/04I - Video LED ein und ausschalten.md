# 04I - Video LED ein und ausschalten

**Anforderung:** Programm aus 4.1 zum ein und ausschalten der LED mit Video belegt.

### LED Startzustand
Die LED's konfiguriere ich so, dass sie beim start alle aus sind:
```yaml
switch:
  - platform: gpio
    id: "LED1"
    name: "LED1"
    icon: "mdi:led-on"
    pin: GPIO25
    restore_mode: ALWAYS_OFF
  - platform: gpio
    id: "LED2"
    name: "LED2"
    icon: "mdi:led-on"
    pin: GPIO14
    restore_mode: ALWAYS_OFF
  - platform: gpio
    id: "LED3"
    name: "LED3"
    icon: "mdi:led-on"
    pin: GPIO13
    restore_mode: ALWAYS_OFF
  - platform: gpio
    id: "LED4"
    name: "LED4"
    icon: "mdi:led-on"
    pin: GPIO12
    restore_mode: ALWAYS_OFF
  - platform: restart
    name: "Restart"
```

### Button Konfiguration
Ich habe zwei verschiedene Konfigs ausprobiert. Button 1 steuert LED1 wie ein Lichtschalter (ein / aus).
Button 2 steuert LED2, aber sie leuchtet nur on hold, solange der Button gedrückt ist.

```yaml
binary_sensor:
  - platform: gpio
    id: "ButtonK1"
    name: "Button K1"
    device_class: door
    pin:
      number: GPIO23
      mode: INPUT_PULLUP
      inverted: true
    on_press:
      then:
        - switch.toggle: LED1
  - platform: gpio
    id: "ButtonK2"
    name: "Button K2"
    pin:
      number: GPIO19
      mode: INPUT_PULLUP
      inverted: true
    on_press:
      then:
        - switch.turn_on: LED2
    on_release:
      then:
        - switch.turn_off: LED2
```
