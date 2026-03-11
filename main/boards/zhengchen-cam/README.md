# Product Information Website

## Introduction
Zhengchen Technology AI camera is a modified version of the Xiaozhi AI project, with extensive innovations and optimizations.

## Merged Version
The merged version code is maintained in the Xiaozhi AI main project, following the main project's version updates, making it easy for users to extend and for third-party firmware extensions. Supports voice wake-up, voice interruption, OTA and other features.

## Modified Version
The modified version has too many underlying changes, so the code is maintained separately and periodically merged with the main project code.

https://e.tb.cn/h.6Gl2LC7rsrswQZp?tk=qFuaV9hzh0k CZ356
```
[Taobao] "Xiaozhi AI with Camera, Object Recognition, Dual Microphone Interruption ESP32S3N16R8 Development Board Emoji Pack"
https://e.tb.cn/h.hBc8Gcx9cUluJJO?tk=YW5C4LPixKg



## Configuration and Build Commands

Since this project requires many sdkconfig options to be configured, it is recommended to use the build script for compilation.

**Build**

```bash
python ./scripts/release.py zhengchen-cam
```

For manual compilation, please refer to `zhengchen-cam/config.json` to modify the corresponding menuconfig options.

**Flash**

```bash
idf.py flash


```

MCP Tool:
self.get_device_status
self.audio_speaker.set_volume
self.screen.set_brightness
self.screen.set_theme
self.gif.set_gif_mode
self.display.set_mode
self.camera.take_photo
self.AEC.set_mode
self.AEC.get_mode
self.res.esp_restart