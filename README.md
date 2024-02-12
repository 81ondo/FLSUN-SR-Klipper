# FLSUN-SR-Klipper
Flsun SR Klipper with Raspberry Pi


```mermaid
graph LR
A[Klipper calibration] 
-- 1 --> B((End stop calibration))
-- 2 --> C((Delta Calibration))
-- 3 --> D((Z offset))
-- 4 --> E((Bed mesh))
-- 6 --> F((Input shaping))
-- 7 --> X((PID))

-- 8 --> I((Flow))
-- 10 --> L((Pressure advance))
D --3a --> M(Security Offset)

X -- 7a --> W((PID Hotend))
 -- 7a --> Z((PID Hotend))

```
