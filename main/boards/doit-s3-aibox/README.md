# DOIT AI Companion Box

# Features
* Uses PDM microphone
* Uses common anode LED

## Button Configuration
* BUTTON3: Short press - Interrupt/Wake up
* BUTTON1: Volume +
* BUTTON2: Volume -

## Build Configuration Commands

**Set the build target to ESP32S3:**

```bash
idf.py set-target esp32s3
```

**Open menuconfig:**

```bash
idf.py menuconfig
```

**Select the board:**

```
Xiaozhi Assistant -> Board Type -> DOIT AI Companion Box
```

**Modify PSRAM configuration:**

```
Component config -> ESP PSRAM -> SPI RAM config -> Mode (QUAD/OCT) -> Octal Mode PSRAM
```

**Build:**

```bash
idf.py build
```