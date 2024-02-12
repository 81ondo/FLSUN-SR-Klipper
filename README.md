# FLSUN-SR-Klipper
Flsun SR Klipper with Raspberry Pi

```mermaid
graph LR
A[Klipper calibration] 
-- 1 --> B((End stop calibration))
-- 2 --> C((Z offset))
-- 3 --> D((Delta Calibration))
-- 4 --> E((Bed mesh))
-- 5 --> F((Input shaping))
-- 6 --> X((PID))
-- 7 --> I((Flow))
-- 8 --> L((Pressure advance))
X -- 7a --> W([PID Hotend]
W -- 7b --> Z([PID Hotend]
D --3a --> M(Security Offset)
```

# 1. End stop calibration
```
[gcode_macro ENDSTOPS_CALIBRATION]
description: Start Endstops Phase Calibration
gcode:
  {% if printer.idle_timeout.state == "Printing" %}
  RESPOND TYPE=error MSG="This macro cannot be used while printing!"
  {% else %}
  {% if printer.toolhead.homed_axes != "xyz" %}
  G28
  {% endif %}
  G91
  G1 Z-50 F1500
  G90
  G28
  G91
  G1 Z-50 F1500
  G90
  G28
  G91
  G1 Z-50 F1500
  G90
  G28
  G91
  G1 Z-50 F1500
  G90
  G28
  G91
  G1 Z-50 F1500
  G90
  G28
  ENDSTOP_PHASE_CALIBRATE stepper=stepper_a
  ENDSTOP_PHASE_CALIBRATE stepper=stepper_b
  ENDSTOP_PHASE_CALIBRATE stepper=stepper_c
  {% endif %}
```
