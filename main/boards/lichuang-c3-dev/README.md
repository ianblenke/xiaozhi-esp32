## LiChuang ESP32-C3 Development Board

1. Development board documentation: https://wiki.lckfb.com/zh-hans/szpi-esp32c3

2. This development board has 8MB flash. Make sure to select the appropriate partition table when building:

```
Partition Table  --->
  Partition Table (Custom partition table CSV)  --->
  (partitions/v2/8m.csv) Custom partition CSV file
```
