Please verify your development board hardware version. If the hardware version differs, select the ev_board type in the configuration.
Versions 1.4 and 1.5 only have IO changes.
You can check the official documentation for specific details: https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32s3/esp32-s3-lcd-ev-board/user_guide.html
The specific changes are:
I2C_SCL     IO18    ->     IO48
I2C_SDA     IO8     ->     IO47
LCD_DATA6   IO47    ->     IO8
LCD_DATA7   IO48    ->     IO18

This version only supports 800x480 screens