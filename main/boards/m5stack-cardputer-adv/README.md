# M5Stack Cardputer Adv

M5Stack Cardputer Adv is a card-sized computer based on ESP32-S3FN8 (Stamp-S3A).

## Hardware Specifications

| Component | Specification |
|------|------|
| MCU | ESP32-S3FN8 @ 240MHz |
| Flash | 8MB |
| Display | ST7789V2 1.14" 240x135 |
| Audio Codec | ES8311 |
| Amplifier | NS4150B |
| Microphone | MEMS |
| Keyboard | 56-key (TCA8418) |
| IMU | BMI270 |
| Battery | 1750mAh |

## Pin Definitions

### Display (ST7789V2)
| Function | GPIO |
|------|------|
| MOSI | GPIO35 |
| SCLK | GPIO36 |
| CS | GPIO37 |
| DC | GPIO34 |
| RST | GPIO33 |
| BL | GPIO38 |

### Audio (ES8311)
| Function | GPIO |
|------|------|
| I2C SDA | GPIO8 |
| I2C SCL | GPIO9 |
| I2S BCLK | GPIO41 |
| I2S LRCK | GPIO43 |
| I2S DOUT | GPIO46 |
| I2S DIN | GPIO42 |

## Usage

1. Press the BOOT button to enter network configuration mode
2. After connecting to WiFi, you can use the voice assistant functionality

## Reference Links

- [M5Stack Cardputer Adv Official Documentation](https://docs.m5stack.com/en/core/Cardputer-Adv)
