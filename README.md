# halfkay-webusb

Inspired by https://github.com/keyboardio/teensy-loader.js and https://github.com/PaulStoffregen/teensy_loader_cli/

Sibling: [avr109-webserial](https://github.com/benjaminaigner/avr109-webserial)

## Background

For our assistive device [FABI](https://github.com/asterics/fabi) & [FLipMouse](https://github.com/asterics/flipmouse) we currently develop a WebSerial based [GUI](https://github.com/asterics/Addon-Bluetooth-WebGUI) to adjust the settings.

One main missing feature was the update process for the included Arduino Micro and TeensyLC.

This project aims to be a proof-of-concept for WebSerial/WebHID based TeensyLC updates (using the HalfKay bootloader.

## Caveats

Because this is a simple proof of concept, some features are still missing or implemented just for TeensyLC:

* Currently only TeensyLC (tested), other blocksizes would allow all other Teensy boards
* Auto-reset to bootloader works only if there is a serial interface in your sketch.
* I just implemented one PID/VID pair for the auto-reset, I don't know if it changes, if there is a different USB feature set selected (in our case: mouse + keyboard + joystick + serial)
* The WebSerial feature of Chromium does NOT allow to open 2 ports with 1 user interaction. But the Arduino Micro running and its bootloader use 2 different PID/VIDs, so 2 user interactions are required (extra "Reset" button)

## How to use

1. Select the corresponding .hex file
2. Press "Reset" and select TeensyLC device (WebSerial)
3. Press "Upload" and select the TeensyLC Bootloader device (WebUSB)

Note: if there is no device shown when "reset" is pressed, your board might be already in the upload mode, so proceed with "upload"

# Acknowledgements

@noopcat for [avrgirl-arduino](https://github.com/noopkat/avrgirl-arduino) which provided the HTML code.

@bminer for [intel-hex.js](https://github.com/bminer/intel-hex.js) which provided the Intel HEX file parser

@PaulStoffregen for the wonderful Teensy boards and the very easy bootloader mechanism,
as well as internal information in [teensy_loader_cli](https://github.com/PaulStoffregen/teensy_loader_cli/)

and of course: stackoverflow :-)


