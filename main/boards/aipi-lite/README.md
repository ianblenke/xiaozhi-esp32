# Build Commands

## One-Click Build

```bash
python scripts/release.py aipi-lite
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
Xiaozhi Assistant -> Board Type -> AIPI-Lite
```

## Build and Flash

```bash
idf.py -DBOARD_NAME=aipi-lite build flash
```

Note: If the device was shipped with AiPi-Lite firmware (non-Xiaozhi version), please be especially careful with the flash firmware partition addresses to avoid accidentally erasing AiPi-Lite's own device information (EUI, etc.). Otherwise, even if the device is restored to Xorigin firmware, it will not be able to connect to the server correctly! So before flashing firmware, please make sure to record the device's relevant essential information to ensure there is a way to recover!

You can use the following command to back up production information

```bash
# firstly backup the factory information partition which contains the credentials for connecting the SenseCraft server
esptool.py --chip esp32s3 --baud 2000000 --before default_reset --after hard_reset --no-stub read_flash 0x9000 16384 nvsfactory.bin

```