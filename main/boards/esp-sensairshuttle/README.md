# ESP-SensairShuttle

## Introduction

<div align="center">
    <a href="https://docs.espressif.com/projects/esp-dev-kits/zh_CN/latest/esp32c5/esp-sensairshuttle/index.html">
        <b> Development Board Documentation </b>
    </a>
    |
    <a href="#sensor--shuttleboard-sub-board-support">
        <b> Sensor & <i>ShuttleBoard</i> Documentation </b>
    </a>
</div>

ESP-SensairShuttle is a development board jointly launched by Espressif and Bosch Sensortec for **motion sensing** and **large model human-machine interaction** scenarios.

ESP-SensairShuttle uses the Espressif ESP32-C5-WROOM-1-N16R8 module as its main controller, featuring 2.4 & 5 GHz dual-band Wi-Fi 6 (802.11ax), Bluetooth® 5 (LE), Zigbee, and Thread (802.15.4) wireless communication capabilities.

## Sensor & _ShuttleBoard_ Sub-board Support

Coming soon, stay tuned.

## Configuration and Build Commands

Since ESP-SensairShuttle requires many sdkconfig options to be configured, it is recommended to use the build script for compilation.

**Build**

```bash
python ./scripts/release.py esp-sensairshuttle
```

For manual compilation, please refer to `main/boards/esp-sensairshuttle/config.json` to modify the corresponding menuconfig options.

**Flash**

```bash
idf.py flash
```