# Wuming Technology Xingzhi 1.54 METAL (wifi)

## Introduction
Wuming Technology Xingzhi 1.54 METAL (wifi) is an upgraded version of the Xingzhi 1.54 molded edition, equipped with a 1.54-inch LCD screen and CST816 touch chip. It replaces physical buttons with touch interaction and upgrades the shell to aluminum alloy material, simultaneously optimizing the interaction experience and product texture and feel.

>### Button Operations
>- **Power On**: In powered-off state, long press the power button for 3 seconds to automatically power on (older hardware versions power on after 1s long press)
>- **Power Off**: In powered-on state, long press the power button for 5 seconds to automatically power off (older hardware versions will not auto power off when USB is plugged in)
>- **Wake Up/Interrupt**: In normal call environment, single click the center touch button
>- **Re-configure Network**: After powering on, single click the center touch button within 1 second, the device will automatically restart and enter the network configuration screen
>- **Increase Volume**: In powered-on state, single click the right touch button to increase volume. Long press the right touch button for 2s to continuously increase volume.
>- **Decrease Volume**: In powered-on state, single click the left touch button to decrease volume. Long press the left touch button for 2s to continuously decrease volume.

>### Sleep Operations
>- **Light Sleep**: After powering on, after maintaining standby state for 60s, enters light sleep (screen brightness adjusted to 1%)
>- **Deep Sleep**: After powering on, after maintaining standby state for 300s, enters deep sleep (automatic power off)
>- **Wake Up**: In light sleep state, single click the center touch button to wake up the device (screen brightness restored)

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
- `Xiaozhi Assistant` → `Board Type` → Select `Wuming Technology Xingzhi 1.54 METAL(wifi)`
```

**Build**

```ba
idf.py build
```

**Flash and open serial monitor**

```bash
idf.py build flash monitor
```