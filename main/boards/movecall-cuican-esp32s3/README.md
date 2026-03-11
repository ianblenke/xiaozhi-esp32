# ESP32-S3 Build Configuration Guide

## Basic Commands

### Set the target chip

```bash
idf.py set-target esp32s3
```

### Open the configuration interface:

```bash
idf.py menuconfig
```
### Flash configuration:

```
Serial flasher config -> Flash size -> 8 MB
```

### Partition table configuration:

```
Partition Table -> Custom partition CSV file -> partitions/v2/8m.csv
```

### Board selection:

```
Xiaozhi Assistant -> Board Type -> Movecall CuiCan AI Pendant
```

### Enable build optimization:

```
Component config -> Compiler options -> Optimization Level -> Optimize for size (-Os)
```

### Build:

```bash
idf.py build
```