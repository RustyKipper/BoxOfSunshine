# Solar storage
Solar battery to inverter interface

A need arose to make use of some redundant roof mounted PV panels so it was decided to install a battery system to store the power generated duing daylight hours and use cheap rate night time electric to make up for any shortfall to fill the battery on overcast or winter days. Several comercial batteries are availiable but they tend to be in a rack mounting format and are very heavy to drag up into the loft space.
A design has been drawn up to use 16 off 305Ah LifePO4 cells mounted in a linear fasion to make use of my limited loft space and allow the aprox 120Kg weight of the battery to be mounted up agaist the gable end and over a load bearing wall. Another requirement was to build the battery into an metal box to porvide some rudimentery fire proofing.

The system will consist of this 14.6Ah / 48V battery and a Solis hybrid inverter. and a custom designed circuit board to interface the BMS to the inverter.

As the chosen inverter can charge and discharge at up to 100A a JBD-AP21S002 200A unit was chosen, this gives a good current headroom, can be configured for 7 - 21 cells, has inbuilt Bluetooth and an accessable RS485 port.

The custom PCB will act as a 'companion' board to the BMS and will need to satisfy 4 requirements

1. Act as an interface between the BMS and the inverter.
    To do this it will send a request to the BMS's RS485 port, receive the requsted data packet, parse out the required data, then convert this to both a human readable format for debugging and a format that the inverter can understand,       this data is then transmitted to the inverter once per second via Can bus using the Pilontech protocol. Some people have had issues with diy Can bus circuits failing so it has been decided to use an isolated tranceiever to negate this     issue.

2. To allow a convienient way to interface the voltage sence wires to the BMS without having to extend the wires supplied with the BMS kit.

3. To make the required links to the front end of the BMS to hard wire it to a 16S system, this wiring, this can be quiute tricky, confusing and messy if done via the wiring, especialy if the system requires fault finding at a later date.
 
4. To control a heating system to keep the battery pack above a set minimum temperature. This is done by monitoring the pack temperature via the data receivec from the BMS and in turn operates a solid state relay. A solid state relay was       chosen to eliminate any switching noise as 'SSR's generaly use a zero volt switching technique and prevents contacts from erroding in use. A fail safe over temperature switch is to be incorperated onto the internal battery heater          plate in case of the relay failing short circuit.



The PCB will use an ATMEG328P-AU micro controller as these are cheap, convienient to mount and program by the Arduino IDE. An ICSP port is to be fitted to the board to allow the code to be uploaded and a serial port for debugging purposes.
RS485 comms is to be handled by the ubiqitus MAX485 and Can bus by a TJA1052I which acording to the data sheet should provide 5000V isolation. 2 x SIL isolated DC-DC converter modules are used to both provide 5V for the logic cicuitry and the power for the output side of the Can bus tranceiver.

 
![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/80bfe23f-6e01-4851-a208-60c7ab2e3b75)





![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/8fdd459a-3a08-4481-8e2a-692963963aa8)



![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/d4e5e7fd-4e51-45e1-9860-404ca554d5ba)

![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/00a1ab72-6e7b-455f-8693-a086ceed744e)


![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/e1899716-46f9-40d1-ae5e-22499ca01d6f)



