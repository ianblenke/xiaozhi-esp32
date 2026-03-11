# ESP-Hi

## Introduction

<div align="center">
    <a href="https://oshwhub.com/esp-college/esp-hi"><b> LCEDA Open Source Platform </b></a>
    |
    <a href="https://www.bilibili.com/video/BV1BHJtz6E2S"><b> Bilibili </b></a>
</div>

ESP-Hi is an ultra **low-cost** AI conversation robot based on ESP32C3, open-sourced by ESP Friends. ESP-Hi integrates a 0.96-inch color screen for displaying expressions, and the **robot dog supports dozens of actions**. By fully utilizing ESP32-C3 peripherals, audio capture and playback can be achieved with minimal board-level hardware. The software has also been optimized to reduce memory and Flash usage, enabling **wake word detection** and multiple peripheral drivers simultaneously under resource-constrained conditions. For hardware details, please refer to the [LCEDA Open Source Project](https://oshwhub.com/esp-college/esp-hi).

## WebUI

ESP-Hi x Xiaozhi has a built-in WebUI for controlling body movements. Connect your phone and ESP-Hi to the same Wi-Fi network, then visit `http://esp-hi.local/` on your phone to use it.

To disable this feature, uncheck `ESP_HI_WEB_CONTROL_ENABLED`, i.e., uncheck `Component config` → `Servo Dog Configuration` → `Web Control` → `Enable ESP-HI Web Control`.

## Configuration and Build Commands

Since ESP-Hi requires many sdkconfig options to be configured, it is recommended to use the build script for compilation.

**Build**

```bash
python ./scripts/release.py esp-hi
```

For manual compilation, please refer to `esp-hi/config.json` to modify the corresponding menuconfig options.

**Flash**

```bash
idf.py flash
```


> [!TIP]
>
> **Servo control will occupy ESP-Hi's USB Type-C interface**, making it unable to connect to a computer (cannot flash/view runtime logs). If you encounter this situation, follow these instructions:
>
> **Flashing**
>
> 1. Disconnect ESP-Hi's power, keep only the head, do not connect the body.
> 2. Hold ESP-Hi's button and connect to the computer.
>
> At this point, ESP-Hi (ESP32C3) should be in flashing mode, and you can use the computer to flash the program. After flashing, you may need to unplug and replug the power.
>
> **Viewing Logs**
>
> Please set `CONFIG_ESP_CONSOLE_USB_SERIAL_JTAG=y`, i.e., `Component config` → `ESP System Settings` → `Channel for console output` select `USB Serial/JTAG Controller`. This will also disable servo control functionality.