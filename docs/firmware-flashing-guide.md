# Beginner's Firmware Flashing Guide

This guide explains how to flash prebuilt firmware onto your XiaoZhi ESP32 device **without setting up a development environment**. It is intended for first-time users who want to get up and running quickly.

> This document is an English translation of the original [Feishu wiki guide](https://ccnphfhqs21z.feishu.cn/wiki/Zpz4wXBtdimBrLk25WdcXzxcnNS).

## Prerequisites

### Hardware

- A supported ESP32-S3 or ESP32-C3 development board
- A USB-C or Micro-USB **data** cable (charge-only cables will not work)
- A Windows, macOS, or Linux computer

### Software

- **Windows**: [Flash Download Tool 3.9.7](https://www.espressif.com/en/support/download/other-tools) (no installation required — just extract and run)
- **macOS / Linux**: Install `esptool.py` via pip:
  ```bash
  pip install esptool
  ```
- **USB Drivers** (Windows only): Install [CP210x](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers) or [CH340](http://www.wch-ic.com/downloads/CH341SER_EXE.html) drivers depending on your board

### Network

- A **2.4 GHz** WiFi network (ESP32 does not support 5 GHz)

## Step 1: Download the Firmware

Download the latest prebuilt firmware from the [GitHub Releases](https://github.com/78/xiaozhi-esp32/releases) page.

Select the firmware file that matches your specific hardware:

| Hardware | Firmware Pattern |
|----------|-----------------|
| Breadboard ESP32-S3 + WiFi (16MB, OLED 128x32) | `vX.X.X_bread-compact-wifi-n16r8-oled12832.bin` |
| Breadboard ESP32-S3 + WiFi (16MB, OLED 128x64) | `vX.X.X_bread-compact-wifi-n16r8-oled12864.bin` |
| Breadboard ESP32-S3 + WiFi (8MB, OLED 128x64) | `vX.X.X_bread-compact-wifi-n8r8-oled12864.bin` |
| Breadboard ESP32-S3 + 4G ML307 | `vX.X.X_bread-compact-ml307.bin` |
| ESP32-S3-BOX-3 | `vX.X.X_esp-box-3.bin` |
| M5Stack CoreS3 | `vX.X.X_m5stack-core-s3.bin` |
| AtomS3R + Echo Base | `vX.X.X_atoms3r-echo-base.bin` |
| LiChuang ESP32-S3 Dev Board | `vX.X.X_lichuang-dev.bin` |
| LiChuang ESP32-C3 Dev Board | `vX.X.X_lichuang-c3-dev.bin` |
| XiaoZhi Mini C3 | `vX.X.X_xmini-c3.bin` |

If you built your own board using the repository, firmware can also be found in the `releases/` directory after running the build scripts. Each board subdirectory contains a `merged-binary.bin`.

> **Important**: Do not place the firmware file or flashing tool in a directory path containing non-ASCII (e.g. Chinese) characters — this may cause file loading errors.

## Step 2: Connect Your Device

1. Connect the ESP32 board to your computer using a USB data cable.
2. If the device is not automatically detected, hold the **BOOT** button while plugging in the USB cable, then release the button after 2 seconds. This forces the device into download mode.

### Identify the Serial Port

- **Windows**: Open Device Manager → Ports (COM & LPT). Note the COM port number (e.g., `COM7`). If no port appears, install the USB drivers above.
- **Linux**: Run `ls /dev/ttyUSB* /dev/ttyACM*`
- **macOS**: Run `ls /dev/cu.usbserial*`

## Step 3: Flash the Firmware

### Method A: Windows — Flash Download Tool (Recommended for Beginners)

1. Extract and run the Flash Download Tool.
2. Configure the interface:
   - **ChipType**: Select your chip (e.g., `ESP32-S3`, `ESP32-C3`)
   - **WorkMode**: `Develop`
   - **LoadMode**: `UART`
3. Click the browse button (`...`) on the first line and select your downloaded `.bin` firmware file.
4. **Check the checkbox** next to the file path to enable it.
5. In the address field next to the file, enter: `0x0`
6. Select your COM port from the dropdown.
7. Click **START**.
8. Wait for the progress bar to complete and the status to show **FINISH**.

### Method B: macOS / Linux — esptool.py

```bash
esptool.py --chip esp32s3 --port /dev/ttyUSB0 -b 2000000 write_flash 0x0 merged-binary.bin
```

Adjust the parameters:
- `--chip`: Use `esp32s3` or `esp32c3` to match your board
- `--port`: Your serial port from Step 2
- `-b 2000000`: Baud rate (reduce to `115200` if you encounter errors)
- Last argument: Path to your firmware `.bin` file

A successful flash will show:
```
Hash of data verified.
Hard resetting via RTS pin...
```

### Method C: Web-Based Flashing

Espressif also provides browser-based flashing via [ESP Launchpad](https://espressif.github.io/esp-launchpad/) — a convenient alternative that works on any OS with a WebSerial-compatible browser (Chrome, Edge).

## Step 4: First Boot and WiFi Configuration

After flashing:

1. **Reset the device** — Press the RST button on the board, or disconnect and reconnect USB power.
2. **Check the LED indicator** — If the RGB LED flashes blue (or the on-board LED flashes white), the device has entered WiFi configuration mode.
3. **Connect to the device hotspot** — Using your phone or computer, look for a WiFi network named **`Xiaozhi-XXXXXX`** (where XXXXXX is derived from the device's MAC address). Connect to it (no password required).
4. **Open the configuration page** — A captive portal should open automatically. If it doesn't, open a browser and navigate to **http://192.168.4.1**.
5. **Select your WiFi network** — Choose your home or office **2.4 GHz** WiFi network from the scanned list, enter the password, and click **Connect**.
6. **Device reboots** — The device will restart and connect to your WiFi network automatically within a few seconds.

## Step 5: Register and Bind Your Device

The firmware connects to the official [xiaozhi.me](https://xiaozhi.me) server by default.

1. Visit [xiaozhi.me](https://xiaozhi.me) and register an account.
2. Add your device using the device's MAC address or the pairing code shown on the device display / announced via speaker.
3. Once bound, you can:
   - Configure the AI personality and system prompt
   - Select a TTS (text-to-speech) voice
   - View conversation history
   - Manage device settings

> For a detailed walkthrough of backend configuration, see the [bilibili video tutorial](https://www.bilibili.com/video/BV1jUCUY2EKM/).

## Step 6: Test Voice Interaction

### Activation Methods

- **Voice wake word** (ESP32-S3 only): Say the configured wake word (default varies by firmware language, e.g., "小智小智" for Chinese firmware).
- **Button**: Press the **BOOT** button on the board. This works on all boards including ESP32-C3.

### Your First Conversation

1. Wait for the device to reach idle state (steady or slow-breathing LED; display shows "Ready" or signal strength).
2. Activate the device using the wake word or BOOT button.
3. Speak your message clearly — audio streams to the server in real time.
4. Wait for the AI response to play back through the speaker.
5. The device returns to idle, ready for the next interaction.

### Supported Languages

The xiaozhi.me server supports voice recognition in: **Mandarin, Cantonese, English, Japanese, and Korean**.

## Troubleshooting

### Flashing Issues

| Problem | Cause | Solution |
|---------|-------|----------|
| Serial port not found | Device not detected | Check USB cable is a data cable; install USB drivers; try a different USB port |
| `Failed to connect` | Not in download mode | Hold BOOT while plugging in USB, then release after 2 seconds |
| Hash mismatch | Corrupted download | Re-download the firmware file and verify file size |
| `Not enough space` | Wrong flash size | Ensure your board has at least 4 MB flash; check you selected the correct firmware |
| Flashing takes very long | High baud rate issues | Reduce baud rate to `115200` |

### Boot Issues

| Problem | Cause | Solution |
|---------|-------|----------|
| No serial output | Wrong monitor baud rate | Use `115200` baud for serial monitor |
| Continuous reboot loop | Flash corruption | Re-flash with a lower baud rate (`115200`) |
| `Invalid header` error | Wrong firmware for board | Verify the firmware matches your exact hardware |
| Device won't start | Insufficient power | Use a 5V / 1A+ power source |

### WiFi Configuration Issues

| Problem | Cause | Solution |
|---------|-------|----------|
| `Xiaozhi-XXXX` hotspot not visible | Device not in config mode | Factory reset: hold BOOT for 10+ seconds |
| Cannot connect to hotspot | N/A | The hotspot has no password — just connect directly |
| Config page doesn't load | Browser cache | Clear cache or use incognito/private browsing |
| Won't connect to my WiFi | 5 GHz network selected | ESP32 only supports 2.4 GHz WiFi |

### Audio / Display Issues

| Problem | Cause | Solution |
|---------|-------|----------|
| No audio output | Speaker not connected or codec issue | Check speaker wiring; verify audio codec initialization in serial logs |
| No display output | Wrong firmware variant | Ensure firmware matches your display type (128x32 vs 128x64 OLED, LCD, etc.) |
| Display flickering | Loose wiring | Inspect screen wiring connections; replace display if connections are sound |
| No wake word detection | ESP32-C3 board | Wake word detection requires ESP32-S3; use button activation on C3 boards |

## Factory Reset

To erase all saved settings (WiFi credentials, etc.) and return to WiFi configuration mode:

**Hold the BOOT button for 10+ seconds**, then release. The device will restart in configuration mode.

## Over-the-Air (OTA) Updates

The device automatically checks for firmware updates on boot:

1. The device queries the OTA server for a newer firmware version.
2. If an update is available, it downloads and verifies the new firmware.
3. The device reboots into the updated firmware.
4. Visual and audio notifications indicate update progress.

No manual action is required — updates happen automatically when connected to WiFi.

## Next Steps

- **Customize your AI assistant**: Configure personality, voice, and features at [xiaozhi.me](https://xiaozhi.me)
- **Set up a development environment**: See the [Development Environment Setup](https://ccnphfhqs21z.feishu.cn/wiki/JIWGwSzFYi3lN1kSxbMcXEXknBb) section in the README
- **Build a custom board**: See [docs/custom-board.md](custom-board.md)
- **Explore the source code**: Clone the repository and run `idf.py menuconfig` to explore configuration options
