# cam-flash — ESP32-CAM_MJPEG2SD v9.7 MQTT+FTP Custom-Build

Flash-Seite: https://gier76.github.io/cam-flash/CAM-Flash.html (von jedem Rechner, Chrome/Edge).

## Firmware
- Basis: s60sc/ESP32-CAM_MJPEG2SD **v9.7** (Tag)
- Compiliert mit arduino-cli + esp32 Core **2.0.17**, Board `esp32cam`, Partition **min_spiffs** (2 App-Slots → OTA danach über Cam-UI möglich)
- Aktiv: `INCLUDE_MQTT`, `INCLUDE_FTP_HFS`, HA-Integration via MQTT
- Deaktiviert: SMTP, Telegram, HTTPS/Certs, WebDAV, Telemetry, Mic, UART (PSRAM-RAM für 2MB-Clone gespart)
- Board: AI-Thinker-Clone (OV2640, real 2MB PSRAM)

## Flashen
1. USB-FTDI an Cam, **GPIO0 → GND**
2. https://gier76.github.io/cam-flash/CAM-Flash.html in Chrome öffnen
3. Button klicken, Serial-Port erlauben
4. Danach: Cam-UI → WiFi + MQTT (Broker 192.168.1.21:1883, User espcam) setzen

## Nach dem Flash
- Partition ändert sich (huge_app → min_spiffs): NVS-Wifi-Creds können verloren gehen → neu setzen.
- OTA danach jederzeit: Cam-UI Firmware-Upload.

Quelle/Build-Log: siehe build/ Ordner-Layout; Source-Patches in appGlobals.h (INCLUDE_* Flags).
