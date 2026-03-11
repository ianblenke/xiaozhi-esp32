# Wuming Technology Xingzhi ABS 2.0

## Introduction
Wuming Technology Xingzhi ABS 2.0 is a cost-effective AI voice interaction development board. It features a 1.54-inch LCD screen, independent physical buttons, and uses the **ML307R 4G communication module**, allowing you to have conversations with large language models anytime, anywhere, even without Wi-Fi.

## Core Features
- Dual network communication: Supports Wi-Fi and ML307R Cat.1 4G dual-mode switching, adaptable to multiple scenarios
- Display system: 1.54-inch 240x240 LCD screen, with custom UI layout optimization for the 1.54-inch square screen display
- Physical button interaction: Independent Boot function key, volume up/down keys, supporting single click, double click, long press, and five-click multi-level operations
- Expansion capability: Built-in Micro SD card slot for local storage expansion; vibration motor can be reserved for tactile feedback on button operations
- Complete power management: Supports battery level ADC detection, real-time charging status monitoring, automatic sleep and deep sleep power-saving control
- Ecosystem compatible: Fully compatible with Xiaozhi ESP32 project firmware, supports large models such as Qwen/DeepSeek, compatible with MCP protocol device control
- Due to hardware differences, the display positions of the bottom emoji and text on the UI have been slightly adjusted

## Core Differences from the Aluminum Alloy Version (XINGZHI_METAL_1_54_WIFI)
| Feature | xingzhi-abs-2.0 | Aluminum Alloy Version |
|----------|------------------|------------|
| Interaction Method | Independent physical buttons (Boot/Volume+/Volume-) | CST816 touch chip + touch interaction |
| Shell Material | ABS engineering plastic | Aluminum alloy |

>### Button Operations
>- **Power On**: In powered-off state, long press the power button for 3 seconds to automatically power on
>- **Power Off**: In powered-on state, long press the power button for 5 seconds to automatically power off
>- **Wake Up/Interrupt**: In normal call/standby state, single click the Boot function key to wake up the device or interrupt an ongoing voice conversation
>- **Re-configure Network**: Within 1 second after powering on, single click the Boot function key, the device will automatically restart and enter the network configuration screen
>- **Switch Network Mode**: In powered-on state, double click the Boot function key to switch between Wi-Fi and 4G network modes
>- **SD Card Status Detection**: In powered-on state, click the Boot function key five times to detect and display SD card mount status on screen
>- **Increase Volume**: In powered-on state, single click the Volume+ button to increase volume by 10%; long press the Volume+ button for 2s to directly increase volume to 100% maximum
>- **Decrease Volume**: In powered-on state, single click the Volume- button to decrease volume by 10%; long press the Volume- button for 2s to directly decrease volume to 0% mute

>### Sleep Operations
>- **Light Sleep**: After powering on, after maintaining standby state for 60s, enters light sleep (screen brightness adjusted to 1%)
>- **Deep Sleep**: After powering on, after maintaining standby state for 300s, automatically powers off
>- **Wake Up**: In light sleep state, single click any button to wake up the device (screen brightness restored)

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
- `Xiaozhi Assistant` → `Board Type` → Select `Wuming Technology Xingzhi ABS 2.0`
```

**Build**

```ba
idf.py build
```

**Flash and open serial monitor**

```bash
idf.py build flash monitor
```