[![](https://img.shields.io/github/release/davesmeghead/visonic_esp32_bridge/all.svg?style=for-the-badge)](https://github.com/davesmeghead/visonic_esp32_bridge/releases) 
[![](https://img.shields.io/badge/MAINTAINER-%40Davesmeghead-green?style=for-the-badge)](https://github.com/Davesmeghead)
[![Buy me a coffee][buymeacoffee-shield]][buymeacoffee]

[buymeacoffee]: https://www.buymeacoffee.com/davesmeghead
[buymeacoffee-shield]: https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png

# ESPHOME Visonic Bridge Configuration

## Introduction
ESPHOME configuration (yaml) to bridge the UART communication between a Powerlink hardware module and a Visonic Panel. The configuration includes a wifi connection for home automation.


## Connectivity/Wiring Diagram
To be completed

## Configuration
Download the yaml file and use it to configure an ESP32 hardware microcontroller using ESPHOME.

In your secrets file you need to include the following:

wifi_ssid: "yourwifissid"

wifi_password: "yourwifipassword"

visonic_bridge_network_ip: A.B.C.D

network_port: APORT

network_mask: 255.255.255.0

network_gateway: A.B.C.1

# go here to create a random key https://esphome.io/components/api.html

visonic_bridge_esphome_encrypt: 


