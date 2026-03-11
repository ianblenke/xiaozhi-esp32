# ESP-VoCat

## Introduction

<div align="center">
    <a href="https://oshwhub.com/esp-college/echoear"><b> LCEDA Open Source Platform </b></a>
</div>

ESP-VoCat is a smart AI development kit featuring the ESP32-S3-WROOM-1 module, a 1.85-inch QSPI round touchscreen, dual-microphone array, and supporting offline voice wake-up and sound source localization algorithms. For hardware details, please refer to the [LCEDA Open Source Project](https://oshwhub.com/esp-college/echoear).

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
- `Xiaozhi Assistant` → `Board Type` → Select `Espressif ESP-VoCat`

### UI Style Selection

ESP-VoCat supports multiple different UI display styles, selectable through menuconfig configuration:

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
   https://dl.espressif.com/AE/wn9_nihaoxiaozhi_tts-font_puhui_common_20_4-echoear.bin
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

> **Note**: ESP-VoCat uses 16MB Flash and requires a dedicated partition table configuration to properly allocate storage space for the application, OTA updates, resource files, etc.

Press `S` to save, press `Q` to exit.

**Build**

```bash
idf.py build
```

**Flash**

Connect ESP-VoCat to your computer, **make sure to turn on the power**, and run:

```bash
idf.py flash
```