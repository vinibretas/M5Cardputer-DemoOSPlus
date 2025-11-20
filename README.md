# M5Cardputer-UserDemo-Plus
Enhanced version of the official Cardputer demo firmware with Arduino integration and a growing set of apps.

## Highlights
- Arduino-ESP32 packaged as an ESP-IDF component to simplify app development.
- WebRadio app (based on @cyberwisk) with HTTPS/chunked stream support, background playback on HOME, ESC to fully exit, and an editable station list.
- Extra and improved apps: Clock (ex-Timer), WiFi Scan/SetWiFi, SCALES, ENV IV, Text Editor, Keyboard, IR, Chat, REPL, Record, Hello sample.
- System polish: background WiFi (toggle via SetWiFi), automatic SNTP time, system bar showing battery voltage/current/free heap, functional WiFi icon.

## Build & Flash (ESP-IDF v4.4.6, target esp32s3)
1. Install and export ESP-IDF 4.4.6 (`. $IDF_PATH/export.sh`).
2. From the repo root run:
   ```bash
   idf.py build
   idf.py -p <PORT> flash -b 1500000 monitor
   ```
   The `flash.sh` script shows a simple wrapper if you want one command.

## App tweaks and configuration
- Radio list: edit `main/apps/app_radio/M5Cardputer_WebRadio.cpp`.
- Clock/Scan/SetWiFi include extra quality-of-life improvements.
- WiFi stays connected by default; reopen SetWiFi to disconnect.

## Adding your own app
- Copy `main/apps/app_hello` as a minimal template.
- Add your new header to `main/apps/apps.h` and install the packer in `main/cardputer.cpp`.
- CMake already glob-includes `main/apps/**`, so new sources are built automatically.

## Lineage and credits
- This repo is a fork of [`WuSiYu/M5Cardputer-UserDemo-Plus`](https://github.com/WuSiYu/M5Cardputer-UserDemo-Plus) and keeps their Arduino component packaging and app set as a starting point.
- `M5Cardputer-UserDemo-Plus` comes from the official [`M5Stack/M5Cardputer-UserDemo`](https://github.com/m5stack/M5Cardputer-UserDemo) hardware-evaluation firmware.
- Bundled components remain attributed to their authors: [`espressif/arduino-esp32`](https://github.com/espressif/arduino-esp32) (Arduino as an ESP-IDF component), [`lovyan03/LovyanGFX`](https://github.com/lovyan03/LovyanGFX) (graphics), [`earlephilhower/ESP8266Audio`](https://github.com/earlephilhower/ESP8266Audio) (audio playback), [`Forairaaaaa/mooncake`](https://github.com/Forairaaaaa/mooncake) (framework utilities), and [`pikastech/pikapython`](https://github.com/pikastech/pikapython) (REPL runtime). The WebRadio app stays credited to @cyberwisk's Cardputer example.
- Roadmap inspiration and feature ideas also reference [`lahirunirmalx/M5Cardputer-UserDemo`](https://github.com/lahirunirmalx/M5Cardputer-UserDemo?tab=readme-ov-file).

## Assets and tools
- Icon generation workflow uses [`riuson/lcd-image-converter`](https://github.com/riuson/lcd-image-converter), which exports bitmap assets suitable for the apps included here.
