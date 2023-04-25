# CAN/WiFi Gateway Hardware
Schematics and PCB layout for a CAN-WiFi gateway based on an ESP8266, an Arduino Nano and a CAN adapter/bridge.

Currently, there is only the DevBoard version available, which was designed to replace a prototype based on prototyping boards, some wires and a case. The dev board is meant to provide a more robust and reliable base for attaching and connecting the individual off-the-shelf components together:

 * An ESP8266 dev board ("NodeMCU Lolin V2")
 * An Arduino Nano V3
 * A CAN bus module based on MCP2515/TJA1050 with SPI (e.g. https://amzn.eu/d/gYvjiQy)
 * A power supply module (e.g. https://amzn.eu/d/45afEuz)

The shape and mounting hole pattern is designed to fit into an enclosure made for possibly moist/wet environments (https://sonoff.tech/product/accessories/ip66/), which is available from different vendors.

Can be used for running https://github.com/simonlmn/can-wifi-gateway-stiebel-eltron.

## Notes on design choices

 * A separate Arduino Nano was used to interface with the CAN module to be able off-load some protocol handling from the ESP8266. While it could have been a better choice to upgrade to an ESP32 for more performance, this approach was a) what was available at the time and b) still seems to allow a more robust operation (the ESP8266 can be overloaded easily into unreliable operation).
 * Because the Arduino uses 5V and the ESP8266 3.3V the board makes use of specialized level shifting ICs. These may be over engineered, but they did  improve reliabililty compared to the prototype (where a resistor was used for level shifting).
