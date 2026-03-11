Hardware is based on the ESP32S3CAM development board, code is based on bread-compact-wifi-lcd modifications.
The camera used is OV2640.
Note: Because the camera uses many IOs, it occupies ESP32S3's USB pins 19 and 20.
Refer to the pin definitions in the config.h file for wiring.


# Build Configuration Commands

**Set the build target to ESP32S3:**

```bash
idf.py set-target esp32s3
```

**Open menuconfig:**

```bash
idf.py menuconfig
```

**Select the board:**

```bash
Xiaozhi Assistant -> Board Type -> Breadboard New Wiring (WiFi) + LCD + Camera
```

**Build and flash:**

```bash
idf.py build flash
```