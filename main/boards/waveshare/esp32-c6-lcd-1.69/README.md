# Product Links

[Waveshare ESP32-C6-Touch-LCD-1.69](https://www.waveshare.net/shop/ESP32-C6-Touch-LCD-1.69.htm)
[Waveshare ESP32-C6-LCD-1.69](https://www.waveshare.net/shop/ESP32-C6-LCD-1.69.htm)

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
Xiaozhi Assistant -> Board Type -> Waveshare ESP32-C6-LCD-1.69
```

**Build**

```ba
idf.py build
```

**Flash and open serial monitor**

```bash
idf.py build flash monitor
```
# Button Operations
## BOOT Button
**Single click before connecting to server: Enter network configuration mode**
**Single click after connecting to server: Wake up / Interrupt**

## PWR Button
**Double click: Turn screen off / Turn screen on**
**Long press: Power on / Power off**