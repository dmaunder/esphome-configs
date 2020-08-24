---
title: Brilliant Smart WiFi Relay Mech 21322
date-published: 2020-08-24
type: switch
standard: au
---
1. TOC
{:toc}

## GPIO Pinout

| Pin     | Function                           |
|---------|------------------------------------|
| GPIO1   | Tuya TX                            |
| GPIO3   | Tuya RX                            |
|---------|------------------------------------|


## Basic Configuration

```yaml
# Basic Config
# https://www.brilliantsmart.com.au/smart-products/electrical/smart-relay-mech/

substitutions:
  device_name: bathroom_light
  friendly_name: "Bathroom Light"

#################################

esphome:
  platform: ESP8266
  board: esp01_1m
  name: $device_name
  esp8266_restore_from_flash: true

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_key
  fast_connect: on
  
api:

ota:

uart:
  rx_pin: GPIO3
  tx_pin: GPIO1
  baud_rate: 9600

# Register the Tuya MCU connection
tuya:

# Make the light
light:
  - platform: "tuya"
    name: $friendly_name
    dimmer_datapoint: 2
    switch_datapoint: 1
    default_transition_length: 0s
`
