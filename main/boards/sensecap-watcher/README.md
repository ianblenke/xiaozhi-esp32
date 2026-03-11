# Build Commands

## One-Click Build

```bash
python scripts/release.py sensecap-watcher
```

## Manual Configuration and Build

```bash
idf.py set-target esp32s3
```

**Configuration**

```bash
idf.py menuconfig
```

Select the board

```
Xiaozhi Assistant -> Board Type -> SenseCAP Watcher
```

Some additional configuration options for the Watcher are listed below and need to be selected in menuconfig.

```
CONFIG_BOARD_TYPE_SEEED_STUDIO_SENSECAP_WATCHER=y
CONFIG_ESPTOOLPY_FLASHSIZE_32MB=y
CONFIG_PARTITION_TABLE_CUSTOM_FILENAME="partitions/v2/32m.csv"
CONFIG_BOOTLOADER_CACHE_32BIT_ADDR_QUAD_FLASH=y
CONFIG_ESPTOOLPY_FLASH_MODE_AUTO_DETECT=n
CONFIG_IDF_EXPERIMENTAL_FEATURES=y
```

## Build and Flash

```bash
idf.py -DBOARD_NAME=sensecap-watcher build flash
```

Note: If the device was shipped with SenseCAP firmware (non-Xiaozhi version), please be especially careful with the flash firmware partition addresses to avoid accidentally erasing the SenseCAP Watcher's own device information (EUI, etc.). Otherwise, even if the device is restored to SenseCAP firmware, it will not be able to connect to the SenseCraft server correctly! So before flashing firmware, please make sure to record the device's relevant essential information to ensure there is a way to recover!

You can use the following command to back up production information

```bash
# firstly backup the factory information partition which contains the credentials for connecting the SenseCraft server
esptool.py --chip esp32s3 --baud 2000000 --before default_reset --after hard_reset --no-stub read_flash 0x9000 204800 nvsfactory.bin

```