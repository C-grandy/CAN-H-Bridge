# CAN-H-Bridge
A CAN Bus controlled H-Bridge motor driver designed for 12V, 10-20A brushed motors with encoders. Features a Atmel Atmega328 MCU along with a MCP2515 CAN controller for compatability with Arduino or standalone AVR C. 
NOTE: This design should not be used as is, it has a few design flaws as it was a proof of concept that was never developed further. 
## Circuit Overview
The design has two major parts, the controls and the H-Bridge motor driver. 
### Controls
The heart of the control system is the Atmega328 MCU. This MCU communicates over CAN for connectivity to other devices along with sending the appropriate PWM and enable signals to the H-bridge driver. It has connectors for a 2 pin quadrature encoder, specifically designed with GoBilda Yellow Jacket gear motors in mind. 
<img width="1042" height="788" alt="image" src="https://github.com/user-attachments/assets/f06c9f9a-f2ff-4265-b8fc-b20c20ee186b" />


### Driver
The driver features 2 IRS2104's half-bridge gate drivers to drive the IRF3205 MOSFETS. This is a standard H-bridge setup, with adequete protection for expected loads. 
NOTE: This circuit uses a external 12V refrence for the IRS2104 input voltage, do not exceed 12V on board VCC or the driver might not work correctly. This is a major design flaw in the circuit as it should include a isolated supply that is refrenced off of VCC. 
<img width="1045" height="789" alt="image" src="https://github.com/user-attachments/assets/d007af47-5162-4633-8137-d8d421a9915b" />


## Included Code:
The code included is a Arduino test file, it takes data in from CAN and then outputs a -127 - 127 value  to the driver circuit. It is a basic test of the boards features, but in reality is not well implemented. Plans for a bare metal C driver were made, but the design intentions for this PCB were changed and rendered not needed. 

## PCB Layout:
This board is a 2 layer stackup, with very basic PCB design rules followed. The overall design of the PCB is lacking, the traces are not properly sized for the loads at hand and a lack of copper pours makes this a elementary design. Even with these shortcomings, the PCB works as expected, but in long tests proved it needed refinement. 
Front: 
<img width="1120" height="837" alt="image" src="https://github.com/user-attachments/assets/f2f03ba2-187a-42fc-a282-feedb09f715e" />

Back: 
<img width="1122" height="837" alt="image" src="https://github.com/user-attachments/assets/f04818c4-fed0-4295-a268-e7cc8fee3d25" />


3D Render: 
Front:
<img width="908" height="673" alt="image" src="https://github.com/user-attachments/assets/75525626-e85d-40a3-a31c-ace5874e4ef0" />

Back:
<img width="905" height="675" alt="image" src="https://github.com/user-attachments/assets/233562f9-b6a5-40b4-85c7-96b5f2c7722d" />
