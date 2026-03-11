# ESP-Spot

## Introduction

<div align="center">
    <a href="https://oshwhub.com/esp-college/esp-spot"><b> LCEDA Open Source Platform </b></a>
    |
    <a href="https://www.bilibili.com/video/BV1ekRAYVEZ1/"><b> Bilibili Demo </b></a>
</div>

ESP-Spot is a smart voice interaction box open-sourced by ESP Friends, with built-in microphone, speaker, and IMU inertial sensor, supporting battery power. ESP-Spot does not have a screen but has one RGB indicator light and two buttons. For hardware details, please refer to the [LCEDA Open Source Project](https://oshwhub.com/esp-college/esp-spot).

The ESP-Spot open source project uses the ESP32-S3-WROOM-1-N16R8 module or ESP32-C5-WROOM-1-N8R8. If you use a different Flash size when replicating, you need to modify the corresponding parameters.


## Configuration and Build Commands

**Set the build target**

```bash
idf.py set-target esp32s3 # Spot S3
# or
idf.py set-target esp32c5 # Spot C5
```

**Open menuconfig and configure**

```bash
idf.py menuconfig
```

Configure the following options respectively:

- `Xiaozhi Assistant` → `Board Type` → Select `ESP-Spot-S3` / `ESP-Spot-C5`

Press `S` to save, press `Q` to exit.

**Build**

```bash
idf.py build
```

**Flash**

```bash
idf.py flash
```

> [!TIP]
>
> **If your computer cannot find the ESP-Spot serial port, try the following steps:**
> 1. Open the front cover;
> 2. Pull out the PCB board with the module;
> 3. Hold <kbd>BOOT</kbd> while reinserting the PCB board, making sure not to reverse it;
>
> At this point, ESP-Spot should have entered download mode. After flashing, you may need to unplug and replug the PCB board.

## Low Power

ESP-Spot supports Deep Sleep low power mode.

After being in idle state for 10 minutes, ESP-Spot will automatically enter Deep Sleep mode. Press the Key button or shake ESP-Spot to wake it up.