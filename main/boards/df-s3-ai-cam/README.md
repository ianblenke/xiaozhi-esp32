# DFRobot ESP32-S3 AI Smart Camera Module

## Introduction
ESP32-S3 AI CAM is a smart camera module based on the ESP32-S3 chip, designed for video image processing and voice interaction, suitable for AI projects such as video surveillance, edge image recognition, and voice conversation.
![](https://ws.dfrobot.com.cn/FsTrGbrX2NZAwzWS8OSQGOGikuYA)

[Click to view detailed introduction](https://wiki.dfrobot.com.cn/SKU_DFR1154_ESP32_S3_AI_CAM)

[Click to view vision feature demo](https://www.bilibili.com/video/BV1ktjSzNEUU/)

# Features
* Uses PDM microphone
* Onboard OV3660 camera

## Button Configuration
* BOOT: Short press - Interrupt/Wake up

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
Xiaozhi Assistant -> Board Type -> DFRobot ESP32-S3 AI Smart Camera Module
```

**Modify PSRAM configuration:**

```
Component config -> ESP PSRAM -> SPI RAM config -> Mode (QUAD/OCT) -> Octal Mode PSRAM
```

**Modify WiFi TX power to 10:**

```
Component config -> PHY -> (10)Max WiFi TX power (dBm)
```

**Configure camera:**

* **OV3660**
```
Component config -> Espressif Camera Sensors Configurations -> Camera Sensor Configuration -> Select and Set Camera Sensor -> OV3660 ->  Auto detect OV3660

```

```
Component config -> Espressif Camera Sensors Configurations -> Camera Sensor Configuration -> Select and Set Camera Sensor -> OV3660 ->  Select default output format for DVP interface (YUV422 240x240 24fps, DVP 8-bit, 20M input)
```

* **OV2640**
```
Component config -> Espressif Camera Sensors Configurations -> Camera Sensor Configuration -> Select and Set Camera Sensor -> OV2640 ->  Auto detect OV2640

```

```
Component config -> Espressif Camera Sensors Configurations -> Camera Sensor Configuration -> Select and Set Camera Sensor -> OV2640 ->  Select default output format for DVP interface (YUV422 240x240 25fps, DVP 8-bit, 20M input)
```

**Build:**

```bash
idf.py build
```