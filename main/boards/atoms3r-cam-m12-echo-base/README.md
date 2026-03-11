# AtomS3R CAM/M12 + Echo Base

## Introduction

<div align="center">
    <a href="https://docs.m5stack.com/zh_CN/core/AtomS3R%20Cam"><b> AtomS3R CAM Product Page </b></a>
    |
    <a href="https://docs.m5stack.com/zh_CN/core/AtomS3R-M12"><b> AtomS3R M12 Product Page </b></a>
    |
    <a href="https://docs.m5stack.com/zh_CN/atom/Atomic%20Echo%20Base"><b> Echo Base Product Page </b></a>
</div>

AtomS3R CAM and AtomS3R M12 are IoT programmable controllers based on ESP32-S3-PICO-1-N8R8 launched by M5Stack, equipped with a camera. Atomic Echo Base is a voice recognition base designed specifically for M5 Atom series hosts, featuring an integrated solution with ES8311 mono audio decoder, MEMS microphone, and NS4150B power amplifier.

Both development boards **have no screen and no additional buttons**, so voice wake-up is required. When necessary, use `idf.py monitor` to view logs to determine the running status.

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

- `Xiaozhi Assistant` → `Board Type` → Select `AtomS3R CAM/M12 + Echo Base`
- `Xiaozhi Assistant` → `IoT Protocol` → Select `MCP Protocol` to enable camera recognition functionality
- `Partition Table` → `Custom partition CSV file` → Delete the existing content and enter `partitions/v2/8m.csv`
- `Serial flasher config` → `Flash size` → Select `8 MB`

Press `S` to save, press `Q` to exit.

**Build**

```bash
idf.py build
```

**Flash**

Connect AtomS3R CAM/M12 to your computer, press and hold the side RESET button until the green LED below the RESET button starts flashing.

```bash
idf.py flash
```

After flashing is complete, press the RESET button once to restart.
