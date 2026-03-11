# Acoustic Test
This GUI is used to test receiving PCM data returned from Xiaozhi devices via `udp`, converting it to time domain/frequency domain. It can save audio of the window length, useful for determining noise frequency distribution and testing the accuracy of acoustic wave ASCII transmission.

Firmware testing requires enabling `USE_AUDIO_DEBUGGER` and setting `AUDIO_DEBUG_UDP_SERVER` to the local machine address.
Acoustic wave `demod` can be tested through `sonic_wifi_config.html` or by uploading to PinMe's [Xiaozhi Acoustic Network Configuration](https://iqf7jnhi.pinit.eth.limo) to output acoustic waves.

# Acoustic Decoding Test Records

> `✓` means successful decoding when receiving the raw PCM signal at I2S DIN, `△` means noise reduction or additional operations are needed for stable decoding, `X` means the effect is still poor after noise reduction (may decode partially but very unstably).
> Some ADCs require more precise noise reduction adjustments during the I2C configuration phase. Since devices are not universal, testing is only based on the configs provided in boards.

| Device | ADC | MIC | Result | Notes |
| ---- | ---- | --- | --- | ---- |
| bread-compact | INMP441 | Integrated MEMS MIC | ✓ |
| atk-dnesp32s3-box | ES8311 | | ✓ |
| magiclick-2p5 | ES8311 | | ✓ |
| lichuang-dev  | ES7210 | | △ | Need to disable INPUT_REFERENCE during testing |
| kevin-box-2 | ES7210 | | △ | Need to disable INPUT_REFERENCE during testing |
| m5stack-core-s3 | ES7210 | | △ | Need to disable INPUT_REFERENCE during testing |
| xmini-c3 | ES8311 | | △ | Needs noise reduction |
| atoms3r-echo-base | ES8311 | | △ | Needs noise reduction |
| atk-dnesp32s3-box0 | ES8311 | | X | Can receive and decode, but packet loss rate is very high |
| movecall-moji-esp32s3 | ES8311 | | X | Can receive and decode, but packet loss rate is very high |