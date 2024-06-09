[![](https://img.shields.io/github/release/davesmeghead/visonic_esp32_bridge/all.svg?style=for-the-badge)](https://github.com/davesmeghead/visonic_esp32_bridge/releases) 
[![](https://img.shields.io/badge/MAINTAINER-%40Davesmeghead-green?style=for-the-badge)](https://github.com/Davesmeghead)
[![Buy me a coffee][buymeacoffee-shield]][buymeacoffee]

[buymeacoffee]: https://www.buymeacoffee.com/davesmeghead
[buymeacoffee-shield]: https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png

# ESPHOME Visonic Bridge Configuration

## Introduction
ESPHOME configuration (yaml) to bridge the UART communication between a Powerlink hardware module and a Visonic Panel. The configuration includes a wifi connection for home automation.

I have an ESP32 microcontroller board acting as a bridge between the Visonic Powerlink hardware module and the Visonic Panel.  It "splits" the RS232 communication between powerlink and panel, meaning that both communicate with the ESP32.
I have a prototype ESPHOME config file for it that I'm testing. I have taken the decision to make it available now whilst I'm alpha testing so there's no guarantees that it works at the moment, I'm still testing when I get the time.

You need to have a working ESPHOME system set up, see [here](https://esphome.io/)

### PowerMax Panels
I have only tried it once on my main panel and it seemed to work. 
PowerMax panels (at least my PowerMax Pro Part) seem fixed at 9600 baud and so don't suffer the problem below for PowerMaster panels.

### PowerMaster Panels
PowerMaster Panels change baud rate between 9600 and 38400. The problem I'm currently working on is centred around that fact that the powerlink and panel automatically negotiate the baud rate between 9600 and 38400. My ESPHOME yaml file has to support this negotiation and change the baud of the 2 UART connections (from ESP32 to the powerlink and the panel).
It does this by counting communication errors and when a threshold is hit then it changes baud.  It also looks for the message that the powerlink module sends to the panel to change baud, and then changes the baud of both UARTs on the ESP32.

## Hardware needed
An ESP32 hardware device, cost is around £10 each including delivery.

A voltage regulator, I would recommend a step up / step down regulator like [this](https://thepihut.com/products/pololu-3-3v-step-up-step-down-voltage-regulator-s7v8f3?variant=41660290236611) to get the 3.3v for the ESP32

## Connectivity/Wiring Diagram
To be completed

## Configuration
Download the yaml file and use it to configure an ESP32 hardware microcontroller using ESPHOME.

In your secrets file you need to include the following:

```
wifi_ssid: "yourwifissid"
wifi_password: "yourwifipassword"
visonic_bridge_network_ip: A.B.C.D
network_port: APORT
network_mask: 255.255.255.0
network_gateway: A.B.C.1
# go here to create a random key https://esphome.io/components/api.html
visonic_bridge_esphome_encrypt: 
```

