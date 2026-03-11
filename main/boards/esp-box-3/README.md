# ESP-BOX-3

## Introduction

<div align="center">
    <a href="https://github.com/espressif/esp-box"><b> ESP-BOX GitHub </b></a>
</div>

ESP-BOX-3 is an AIoT development kit officially developed by Espressif, featuring the ESP32-S3-WROOM-1 module, equipped with a 2.4-inch 320x240 ILI9341 display, dual-microphone array, and supporting offline voice wake-up and device-side echo cancellation (AEC).

## Hardware Features

- **Main Controller**: ESP32-S3-WROOM-1 (16MB Flash, 8MB PSRAM)
- **Display**: 2.4-inch IPS LCD (320x240, ILI9341)
- **Audio**: ES8311 Audio Codec + ES7210 Dual-Mic ADC
- **Audio Features**: Supports device-side AEC (Echo Cancellation)
- **Buttons**: Boot button (single-click/double-click functions)
- **Other**: USB-C power and communication

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

### Basic Configuration
- `Xiaozhi Assistant` → `Board Type` → Select `ESP BOX 3`

### UI Style Selection

ESP-BOX-3 supports multiple different UI display styles, selectable through menuconfig configuration:

- `Xiaozhi Assistant` → `Select display style` → Select display style

#### Available Styles

##### Emote Animation Style - Recommended
- **Configuration Option**: `USE_EMOTE_MESSAGE_STYLE`
- **Features**: Uses custom `EmoteDisplay` emote display system
- **Functionality**: Supports rich emote animations, eye animations, status icon display
- **Suitable for**: Smart assistant scenarios, providing more vivid human-machine interaction experience
- **Class**: `emote::EmoteDisplay`

**⚠️ Important**: Selecting this style requires additional custom resource file configuration:
1. `Xiaozhi Assistant` → `Flash Assets` → Select `Flash Custom Assets`
2. `Xiaozhi Assistant` → `Custom Assets File` → Enter the resource file URL:
   ```
   https://dl.espressif.com/AE/wn9_nihaoxiaozhi_tts-font_puhui_common_20_4-esp-box-3.bin
   ```

##### Default Message Style (Enable default message style)
- **Configuration Option**: `USE_DEFAULT_MESSAGE_STYLE` (default)
- **Features**: Uses standard message display interface
- **Functionality**: Traditional text and icon display interface
- **Suitable for**: Standard conversation scenarios
- **Class**: `SpiLcdDisplay`

##### WeChat Message Style (Enable WeChat Message Style)
- **Configuration Option**: `USE_WECHAT_MESSAGE_STYLE`
- **Features**: WeChat-like chat interface style
- **Functionality**: WeChat-like message bubble display
- **Suitable for**: Users who prefer WeChat style
- **Class**: `SpiLcdDisplay`

### Audio Feature Configuration

#### Device-Side Echo Cancellation (AEC)
- `Xiaozhi Assistant` → `Enable Device-Side AEC` → Enable

ESP-BOX-3 hardware supports device-side AEC functionality, which can effectively eliminate interference from speaker playback on the microphone, improving voice recognition accuracy.

**Runtime Toggle**: Double-click the Boot button to enable/disable AEC functionality at runtime.

> **Note**: Device-side AEC requires a clean speaker output reference path and good physical isolation between the microphone and speaker to work properly. ESP-BOX-3 hardware has been optimized for this purpose.

### Wake Word Configuration

ESP-BOX-3 supports multiple wake word implementation methods:

- `Xiaozhi Assistant` → `Wake Word Implementation Type` → Select wake word type

Recommended selection:
- **Wakenet model with AFE** (`USE_AFE_WAKE_WORD`) - Wake word detection with AEC support

Press `S` to save, press `Q` to exit.

**Build**

```bash
idf.py build
```

**Flash**

Connect the ESP-BOX-3 to your computer and run:

```bash
idf.py flash
```

## Button Description

### Boot Button Functions

#### Single Click
- **Network Configuration State**: Enter WiFi configuration mode
- **Idle State**: Start conversation
- **During Conversation**: Interrupt or stop the current conversation

#### Double Click (Requires device-side AEC enabled)
- **Idle State**: Toggle AEC on/off

## FAQ

### 1. Why is device-side AEC needed?
Device-side AEC can locally eliminate interference from speaker playback on the microphone in real time, allowing accurate voice command recognition even while playing music or TTS responses.

### 2. Emote animation style not displaying?
Please ensure that the correct custom resource file URL has been configured, and that the device can access the URL to download the resources.

### 3. How to restore factory settings?
Long press the Boot button for more than 3 seconds, and the device will clear all configurations and restart.