# labplus Controller Board V3

## Onboard Resources
    MCU: ESP32-S3 with external 8MB PSRAM 16MB Flash
    Sensors:
        Buttons (A B buttons)	IO0 IO46
        Light sensor	I2C
        6-axis IMU	I2C
        Magnetometer	I2C
        Sound trigger	IO6
        Touch buttons  P Y T H O N
        Camera	I2C
    Actuators:
        Buzzer	IO21
        RGB LED	IO16
        Audio record/playback es8388	I2C
        TFT LCD	jd9853 SPI


## Build Configuration

### Set the build target to ESP32S3, USB JTAG download

```bash
idf.py set-target esp32s3
```

### menuconfig Configuration

```bash
idf.py menuconfig
```

***Select the board:***

```
Xiaozhi Assistant -> Board Type -> labplus mpython_v3 board
```

***Modify PSRAM configuration:***

```
Component config -> ESP PSRAM -> SPI RAM config -> Mode (QUAD/OCT) -> quad Mode PSRAM
```

**Build:**

```bash
idf.py build
```

**Firmware packaging:**

```bash
esptool.py -p /dev/ttyACM0 -b 1500000 --before default_reset --after hard_reset --chip esp32s3 write_flash --flash_mode dio --flash_freq 80m --flash_size 16MB 0x0 bootloader/bootloader.bin 0x100000 xiaozhi.bin 0x8000 partition_table/partition-table.bin 0xd000 ota_data_initial.bin 0x10000 srmodels/srmodels.bin
```

## Usage

### Button Configuration
* A: Short press - Interrupt/Wake up
