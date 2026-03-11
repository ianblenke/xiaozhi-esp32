# Usage Instructions

* [M5Stack Tab5 docs](https://docs.m5stack.com/zh_CN/core/Tab5)

## Quick Start

Go to [M5Burner](https://docs.m5stack.com/zh_CN/uiflow/m5burner/intro), select Tab5, search for Xiaozhi and download the firmware

## Basic Usage

* idf version: v6.0-dev

1. Adjust idf_component.yml

Change
```yaml
  espressif/esp_video:
    version: ==1.3.1   # for compatibility. update version may need to modify this project code.
    rules:
    - if: target not in [esp32]
```
To
```yaml
  espressif/esp_video:
    version: '==0.7.0'
    rules:
    - if: target not in [esp32]
  espressif/esp_ipa: '==0.1.0'
```

* idf version: v5.5.3

For ESP32-P4 Rev <3.0 users:
Make sure your sdkconfig.defaults includes:

CONFIG_ESP32P4_SELECTS_REV_LESS_V3=y

Otherwise, you will encounter the following error during flashing: 'bootloader/bootloader.bin' requires chip revision in range [v3.0 - v3.99] (this chip is revision v1.x)

2. Build using release.py

```shell
python ./scripts/release.py m5stack-tab5
```

For manual compilation, please refer to `m5stack-tab5/config.json` to modify the corresponding menuconfig options.

3. Build, flash, and monitor

```shell
idf.py flash monitor
```

> [!NOTE]
> To enter download mode: Long press the reset button (about 2 seconds) until the internal green LED indicator starts flashing rapidly, then release the button.


## log

@2025/05/17 Test issues

1. listening... needs to wait a few seconds before it can receive voice input???
2. Brightness adjustment is incorrect
3. Volume adjustment is incorrect

## TODO
