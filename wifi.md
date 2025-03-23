---
layout: page
title: Notes on Wi-Fi Connection for ESP32
permalink: /project/wifi
---
Both `csi_recv` and `mqtt` requires the ESP32 to connect to a Wi-Fi, where your laptop and CSI sender can find in the local network.

Since HKU Wi-Fi is protected by HKU certificate, it is not easy for your ESP32 to connect to it. 

Here we provide some suggestions on how you can connect to the Wi-Fi and finish your project.

## Connect to your router

This is the easiest way to connect to the Wi-Fi. This is irrelevant to the network you are using, i.e. whether you are using HKU network or other public/home network.

Here is the setting in `esp32c5/csi_recv/main/app_main.c`

```c++
wifi_config_t wifi_config = {
      .sta =
          {
              .ssid = "<your_ssid>",
              .password = "<your_password>",
              .threshold.authmode = WIFI_AUTH_WPA2_PSK,
              .pmf_cfg = {.capable = true, .required = false},
          },
  };
```

## Connect to your mobile phone's hotspot

Here is the setting in `esp32c5/csi_recv/main/app_main.c`

```c++
wifi_config_t wifi_config = {
      .sta =
          {
              .ssid = "<your_mobile_hotpot_ssid>",
              .password = "<your_mobile_hotpot_password>",
              .threshold.authmode = WIFI_AUTH_WPA2_PSK,
              .scan_method = DEFAULT_SCAN_METHOD, 
              .pmf_cfg = {.capable = true, .required = false},
          },
  };
```

You have to add the `.scan_method = DEFAULT_SCAN_METHOD` to use your mobile phone's hotspot.

## Connect to Wi-Fi.HK via HKU

If you do not have a router and you do not want to connect to your mobile phone's hotspot, you can connect to Wi-Fi.HK via HKU. 

Here is the setting in `esp32c5/csi_recv/main/app_main.c`

```c++
wifi_config_t wifi_config = {
      .sta =
          {
              .ssid = "Wi-Fi.HK via HKU",
              .password = "",
              .threshold.authmode = WIFI_AUTH_OPEN,
              .pmf_cfg = {.capable = true, .required = false},
          },
  };
```

You need to set the `.threshold.authmode = WIFI_AUTH_OPEN` to use Wi-Fi.HK via HKU.

## (Optional) Connect to HKU

If you really want to try connecting the ESP32 to HKU Wi-Fi, we recommend you to access the following materials:

1. [Official Examples for Wi-Fi Enterprise Mode](https://github.com/espressif/esp-idf/tree/master/examples/wifi/wifi_enterprise)
2. [Settings for HKU Wi-Fi](https://its.hku.hk/kb/procedure-other-access-hku-wifi/)

