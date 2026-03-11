# Build Configuration Guide

This document describes how to configure and build firmware for **Movecall Moji2.0 (Xiaozhi AI Derivative Edition)**.

## Prerequisites
*   **ESP-IDF Version**: v5.5
*   **Chip Model**: ESP32-C5

## Hardware Open Source Information
This project is based on the following open-source hardware design:
*   **LCEDA Open Source Hardware Platform**: [https://oshwhub.com/movecall/moji2](https://oshwhub.com/movecall/moji2)

---

## Build Steps

### 1. Set the Build Target
First, set the project target chip to ESP32-C5:
```bash
idf.py set-target esp32c5
```

### 2. Configure the Board Type
Run the following command to open the configuration menu for board selection:
```bash
idf.py menuconfig
```

**Navigate the menu following this path:**
> **Xiaozhi Assistant** -> **Board Type** -> **Movecall Moji2.0 Xiaozhi AI Derivative Edition**

*Tip: After configuration, press **S** to save and Enter to confirm, press **Q** to exit.*

### 3. Build
Run the following command to start building the project:
```bash
idf.py build
```

---

## Useful Maintenance Commands

**Clean build cache (recommended if you encounter errors):**
```bash
idf.py fullclean
```

**Flash firmware:**
```bash
idf.py flash
```

**View serial logs:**
```bash
idf.py monitor
```