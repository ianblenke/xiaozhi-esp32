# DFRobot UNIHIKER K10

## Button Configuration
* A: Short press - Interrupt/Wake up, Long press 1s - Volume up
* B: Short press - Interrupt/Wake up, Long press 1s - Volume down

## Build Configuration Commands

**Set the build target to ESP32S3:**

```bash
idf.py set-target esp32s3
```

**Open menuconfig:**

```bash
idf.py menuconfig
```

**Select the board:**

```
Xiaozhi Assistant -> Board Type -> DFRobot UNIHIKER K10
```

**Modify PSRAM configuration:**

```
Component config -> ESP PSRAM -> SPI RAM config -> Mode (QUAD/OCT) -> Octal Mode PSRAM
```

**Enable camera buffer endianness swapping:**

```
Xiaozhi Assistant -> Camera Configuration -> Enable software camera buffer endianness swapping
```

**Configure camera:**
```
Component config -> Espressif Camera Sensors Configurations -> Camera Sensor Configuration -> Select and Set Camera Sensor -> GC2145 ->  Auto detect GC2145

```

```
Component config -> Espressif Camera Sensors Configurations -> Camera Sensor Configuration -> Select and Set Camera Sensor -> GC2145 ->  Select default output format for DVP interface (RGB565 800x600 20fps, DVP 8-bit, 20M input) -> RGB565 800x600 20fps, DVP 8-bit, 20M input

```

**Build:**

```bash
idf.py build
```



