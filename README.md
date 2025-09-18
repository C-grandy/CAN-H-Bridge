# CAN-H-Bridge
A CAN Bus controlled H-Bridge motor driver designed for 12V, 10-20A brushed motors with encoders. Features a Atmel Atmega328 MCU along with a MCP2515 CAN controller for compatability with Arduino or standalone AVR C. 
NOTE: This design should not be used as is, it has a few design flaws as it was a proof of concept that was never developed further. 
## Circuit Overview
The design has two major parts, the controls and the H-Bridge motor driver. 
### Controls
The heart of the control system is the Atmega328 MCU. This MCU communicates over CAN for connectivity to other devices along with sending the appropriate PWM and enable signals to the H-bridge driver. It has connectors for a 2 pin quadrature encoder, specifically designed with GoBilda Yellow Jacket gear motors in mind. 

### Driver
The driver features 2 IRS2104's half-bridge gate drivers to drive the IRF3205 MOSFETS. This is a standard H-bridge setup, with adequete protection for expected loads. 
NOTE: This circuit uses a external 12V refrence for the IRS2104 input voltage, do not exceed 12V on board VCC or the driver might not work correctly. This is a major design flaw in the circuit as it should include a isolated supply that is refrenced off of VCC. 

## Included Code:
The code included is a Arduino test file, it takes data in from CAN and then outputs a -127 - 127 value  to the driver circuit. It is a basic test of the boards features, but in reality is not well implemented. Plans for a bare metal C driver were made, but the design intentions for this PCB were changed and rendered not needed. 
