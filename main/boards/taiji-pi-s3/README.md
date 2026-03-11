# Due to the original microphone model being discontinued, Taiji Pi (JC3636W518) produced after July 2025 has a replacement microphone and screen glass. Users with batch numbers greater than 2528 on the product label should select I2S Type PDM.

# Added dual-channel configuration

# Build Configuration Commands

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
Xiaozhi Assistant -> Board Type -> Taiji Pi ESP32S3

Xiaozhi Assistant -> TAIJIPAI_S3_CONFIG -> taiji-pi-S3 I2S Type -> I2S Type PDM
```

**If you need to select dual-channel:**
```

Xiaozhi Assistant -> TAIJIPAI_S3_CONFIG -> Enabel use 2 slot
```


**Modify PSRAM configuration:**

```
component config -> ESP PSRAM -> SPI RAM config -> Try to allocate memories of WiFi and LWIP in SPIRAM firstly. If failed, allocate internal memory

```

**Build:**

```bash
idf.py build
```
