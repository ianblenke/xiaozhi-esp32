
minsi-k08-wifi and minsi-k08-ml307 are products from Minsi Technology based on ESP32S3N16R8, equipped with MAX98357 audio power amplifier and INMP441 omnidirectional microphone module. They are punk-style Xiaozhi AI chatbot solutions with large speakers and large batteries, created by modifying the K08 transparent mecha mini speaker.

<a href="https://item.taobao.com/item.htm?id=889892765588" target="_blank" title="SenseCAP Watcher">Minsi-k08</a>

  <a href="minsi-k08.jpg" target="_blank" title="Minsi-k08">
    <img src="minsi-k08.jpg" width="240" />
  </a>



# Build Configuration Commands

**Set the build target to ESP32S3:**

```bash
idf.py set-target esp32s3
```

**Open menuconfig:**

```bash
idf.py menuconfig
```

**Select the board:**

```
Xiaozhi Assistant -> Board Type -> Minsi Technology K08 (DUAL)
```

**Build and flash:**

```bash
idf.py build flash
```