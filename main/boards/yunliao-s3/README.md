# Xiaozhi Yunliao S3

## Introduction

Xiaozhi Yunliao S3 is a modified version of the Xiaozhi AI project, and is the first mass-produced finished product with a 2.8-inch eye-protection large screen + large font + 2000mAh large battery, with extensive innovations and optimizations.

## Official Version

The official version code is maintained in the Xiaozhi AI main project, following the main project's version updates, making it easy for users to extend and for third-party firmware extensions. Supports voice wake-up, voice interruption, OTA, 4G free switching and other features.

> ### Button Operations
>
> - **Power On**: In powered-off state, long press for 1 second then release the button to automatically power on.
> - **Power Off**: In powered-on state, long press for 1 second then release the button, the title bar will display 'Please wait', then automatically powers off after 2 more seconds.
> - **Wake Up/Interrupt**: In normal call environment, single click the button.
> - **Switch 4G/Wi-Fi**: During startup or on the network configuration screen, double click the button within 1 second (requires 4G module installed).
> - **Switch Voice (AEC) Interrupt Mode**: After normal startup, in idle no-conversation mode, double click the button within 1 second to cycle through voice interrupt modes.
> - **Re-configure Network**: In powered-on state, triple click the button within 1 second, the device will automatically restart and enter the network configuration screen.

> ### Voice Commands
>
> - **Enable/Disable Voice (AEC) Interrupt Mode**: When playing music, you need to disable voice interrupt mode, otherwise it may interrupt music playback.
> - **Switch IPS Screen Display Mode**: The new version of Xiaozhi Yunliao S3 has been upgraded with an IPS screen. You need to switch the screen display mode for normal display. You can switch back and forth.

## Modified Version

The modified version has too many underlying changes, so the code is maintained separately and periodically merged with the main project code.

> ### Why It's Modified
>
> - First to implement WeChat QR code network configuration.
> - First to support single-phone network configuration.
> - First to support scanning QR code to access the console.
> - First to support Traditional Chinese, Japanese, and English interface.
> - First to have full voice control mode.
> - Exclusively provides one-click flashing scripts and multiple flashing methods.

## Version Differences

> | Feature | Official Version | Modified Version |
> | -------------- | ------ | ------ |
> | Voice Interruption | ✓ | ✓ |
> | 4G Function | ✓ | ✓ |
> | Auto Firmware Update | ✓ | X |
> | Third-party Firmware Support | ✓ | X |
> | Weather Standby Screen | X | ✓ |
> | Alarm Reminder | X | ✓ |
> | Online Music Playback | X | ✓ |
> | WeChat QR Network Config | X | ✓ |
> | Single-phone Network Config | X | ✓ |
> | QR Code Console Access | X | ✓ |
> | Traditional/Japanese/English Interface | X | ✓ |
> | Multi-language Support | Requires self-compilation | ✓ |
> | External Bluetooth Speaker/Headset | ✓ | ✓ |

# Build Configuration Commands

**Clone the project**

```bash
git clone https://github.com/78/xiaozhi-esp32.git
```

**Enter the project directory**

```bash
cd xiaozhi-esp32
```

**Set the build target to ESP32S3**

```bash
idf.py set-target esp32s3
```

**Open menuconfig**

```bash
idf.py menuconfig
```

**Select the board**

```bash
- `Xiaozhi Assistant` → `Board Type` → Select `Xiaozhi Yunliao-S3` → Select `Enable Device-Side AEC`
```

**Build**

```ba
idf.py build
```

**Flash and open serial monitor**

```bash
idf.py build flash monitor
```
