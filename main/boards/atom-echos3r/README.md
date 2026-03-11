# AtomEchoS3R
## Introduction

AtomEchoS3R is an IoT programmable controller based on ESP32-S3-PICO-1-N8R8 launched by M5Stack, featuring an integrated solution with ES8311 mono audio decoder, MEMS microphone, and NS4150B power amplifier.

The development board **has no screen and no additional buttons**, so voice wake-up is required. When necessary, use `idf.py monitor` to view logs to determine the running status.

## Configuration and Build Commands

**Set the build target to ESP32S3**

```bash
idf.py set-target esp32s3
```

**Open menuconfig and configure**

```bash
idf.py menuconfig
```

Configure the following options respectively:

- `Xiaozhi Assistant` → `Board Type` → Select `AtomEchoS3R`
- `Partition Table` → `Custom partition CSV file` → Delete the existing content and enter `partitions/v2/8m.csv`
- `Serial flasher config` → `Flash size` → Select `8 MB`
- `Component config` → `ESP PSRAM` → `Support for external, SPI-connected RAM` → `SPI RAM config` → Select `Octal Mode PSRAM`

Press `S` to save, press `Q` to exit.

**Build**

```bash
idf.py build
```

**Flash**

Connect AtomEchoS3R to your computer, press and hold the side RESET button until the green LED below the RESET button starts flashing.

```bash
idf.py flash
```

After flashing is complete, press the RESET button once to restart the device.
