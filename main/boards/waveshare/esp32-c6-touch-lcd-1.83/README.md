
# Product Link
Waveshare ESP32-C6-Touch-LCD-1.83

(https://www.waveshare.net/shop/ESP32-C6-Touch-LCD-1.83.htm)

# Build Configuration Commands

**Clone the project**

```bash
git clone https://github.com/78/xiaozhi-esp32.git
```

**Enter the project directory**

```bash
cd xiaozhi-esp32
```

**Set the build target to ESP32C6**

```bash
idf.py set-target esp32c6
```

**Open menuconfig**

```bash
idf.py menuconfig
```

**Select the board**

```bash
Xiaozhi Assistant -> Board Type -> Waveshare ESP32-C6-Touch-LCD-1.83
```

**Build**

```ba
idf.py build
```

**Flash and open serial monitor**

```bash
idf.py build flash monitor
```
