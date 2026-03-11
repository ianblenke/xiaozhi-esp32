# BluFi Network Provisioning (Integrated with esp-wifi-connect)

This document explains how to enable and use BluFi (BLE Wi-Fi provisioning) in the XiaoZhi firmware, combined with the built-in `esp-wifi-connect` component for Wi-Fi connection and storage. For the official BluFi protocol specification, please refer to the [Espressif Documentation](https://docs.espressif.com/projects/esp-idf/zh_CN/stable/esp32/api-guides/ble/blufi.html).

## Prerequisites

- A chip and firmware configuration that supports BLE is required.
- Enable `WiFi Configuration Method -> Esp Blufi` (`CONFIG_USE_ESP_BLUFI_WIFI_PROVISIONING=y`) in `idf.py menuconfig`. If you want to use BluFi, you must disable the Hotspot option under the same menu; otherwise, the Hotspot provisioning mode will be used by default.

- Keep the default NVS and event loop initialization (already handled by the project's `app_main`).
- The two macros CONFIG_BT_BLUEDROID_ENABLED and CONFIG_BT_NIMBLE_ENABLED should be mutually exclusive; they cannot be enabled simultaneously.
## Workflow

1) The mobile phone connects to the device via BluFi (using the official EspBlufi App or a custom client) and sends the Wi-Fi SSID/password. The phone can obtain the Wi-Fi list scanned by the device through the BluFi protocol.
2) On the device side, the credentials are written to `SsidManager` (stored in NVS, part of the `esp-wifi-connect` component) in the `ESP_BLUFI_EVENT_REQ_CONNECT_TO_AP` event.
3) Then `WifiStation` is started to scan and connect; the status is returned via BluFi.
4) After successful provisioning, the device will automatically connect to the new Wi-Fi; on failure, a failure status is returned.

## Usage Steps

1. Configuration: Enable `Esp Blufi` in menuconfig. Compile and flash the firmware.
2. Trigger provisioning: The device will automatically enter provisioning mode on first boot if no saved Wi-Fi is found.
3. Mobile phone operation: Open the EspBlufi App (or another BluFi client), search for and connect to the device. You can choose whether to use encryption. Enter the Wi-Fi SSID/password as prompted and send it.
4. Observe the result:
    - Success: BluFi reports a successful connection, and the device automatically connects to Wi-Fi.
    - Failure: BluFi returns a failure status; you can resend or check the router.

## Notes

- BluFi provisioning cannot be enabled simultaneously with hotspot provisioning. If hotspot provisioning is already started, it will be used by default. Please keep only one provisioning method in menuconfig.
- If testing multiple times, it is recommended to clear or overwrite the stored SSID (`wifi` namespace) to avoid interference from old configurations.
- If using a custom BluFi client, you must follow the official protocol frame format. Refer to the official documentation link above.
- The official documentation provides download links for the EspBlufi App.
- Due to changes in the BluFi interface in IDF 5.5.2, the Bluetooth name after compilation is "Xiaozhi-Blufi" in version 5.5.2, while in version 5.5.1 the Bluetooth name is "BLUFI_DEVICE".
