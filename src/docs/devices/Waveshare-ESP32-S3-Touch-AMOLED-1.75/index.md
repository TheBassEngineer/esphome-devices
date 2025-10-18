---
title: Waveshare ESP32-S3-Touch-AMOLED-1.75
date-published: 2025-10-18
type: misc
standard: uk, us, global
board: esp32-s3
difficulty: 2
---

## Product specs

| Feature      | Spec                    |
| ------------ | ----------------------- |
| Screen       | CO5300 driver 466\*466 |
| Touch screen | CST9217                  |
| CPU          | ESP32-S3               |
| Flash        | 16MB                    |
| PSRAM        | 8MB                     |

## Product description

A circular 1.75in / 45mm AMOLED display with touchscreen, esp32s3 microcontroller, and dual microphones with AEC.
Avalible on [Waveshare](https://www.waveshare.com/esp32-s3-touch-amoled-1.75.htm?sku=31261) for ~$30. Case and GPS versions are available.

## Basic Config

```yaml
substitutions:
  name: "waveshare-s3-amoled-175"
  friendly_name: "Waveshare-S3-AMOLED-1.75in"

esphome:
  name: "${name}"
  friendly_name: "${friendly_name}"
  project:
    name: "${project_name}"
    version: "${project_version}"
  platformio_options:
    board_build.flash_mode: dio
    board_build.f_flash: 80000000L
    board_build.f_cpu: 240000000L

esp32:
  board: esp32-s3-devkitc-1
  flash_size: 16MB
  framework:
    type: esp-idf

# Enable logging
logger:

# Enable Home Assistant API
api:
  encryption:
    key: !secret encryption_key

ota:
  - platform: esphome
    password: !secret ota_key

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password

  # Enable fallback hotspot (captive portal) in case wifi connection fails
  ap:
    ssid: "${friendly_name} Fallback Hotspot"
    password: "6T3RFWEF71"

```
