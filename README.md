# Solar storage
Solar battery to inverter interface

A need arose to make use of some redundant roof mounted PV panels so it was decided to install a battery system to store the power generated duing daylight hours and use cheap rate night time electric to make up for any shortfall to fill the battery on overcast or winter days. Several comercial batteries are availiable but they tend to be in a rack mounting format and are very heavy to drag up into the loft space.
A design has been drawn up to use 16 off 305Ah LifePO4 cells mounted in a linear fasion to make use of my limited loft space and allow the aprox 120Kg weight of the battery to be mounted up agaist the gable end and over a load bearing wall. Another requirement was to build the battery into an metal box to porvide some rudimentery fire proofing.

![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/80bfe23f-6e01-4851-a208-60c7ab2e3b75)

The system will consist of this 14.6Ah / 48V battery and a Solis hybrid inverter. and a custom designed circuit board to interface the BMS to the inverter.

As the chosen inverter can charge and discharge at up to 100A a JBD-AP21S002 200A unit was chosen, this gives a good current headroom, can be configured for 7 - 21 cells, has inbuilt Bluetooth and an accessable RS485 port.

The custom PCB will act as a 'companion' board to the BMS and will need to satisfy 4 requirements

1. Act as an interface between the BMS and the inverter.
    To do this it will send a request to the BMS's RS485 port, receive the requsted data packet, parse out the required data, then convert this to both a human readable format for debugging and a format that the inverter can understand,       this data is then transmitted to the inverter once per second via Can bus using the Pilontech protocol. Some people have had issues with diy Can bus circuits failing so it has been decided to use an isolated tranceiever to negate this     issue.

2. To allow a convienient way to interface the voltage sence wires to the BMS without having to extend the wires supplied with the BMS kit.

3. To make the required links to the front end of the BMS to hard wire it to a 16S system, this wiring can be a bit tricky, confusing and messy if done via the wiring, especialy if the system requires fault finding at a later date.
 
4. To control a heating system to keep the battery pack above a set minimum temperature. This is done by monitoring the pack temperature via the data received from the BMS and in turn operates a solid state relay. A solid state relay was       chosen to eliminate any switching noise as 'SSR's generaly use a zero volt switching technique and prevents contacts from erroding in use. A fail safe over temperature switch is to be incorperated onto the internal battery heater          plate in case of the relay failing short circuit.

![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/8fdd459a-3a08-4481-8e2a-692963963aa8)

The PCB will use an ATMEG328P-AU micro controller as these are cheap, convienient to mount and program by the Arduino IDE. An ICSP port is to be fitted to the board to allow the code to be uploaded and a serial port for debugging purposes.
RS485 comms is to be handled by the ubiqitus MAX485 and Can bus by a TJA1052I which acording to the data sheet should provide 5000V isolation. 2 x SIL isolated DC-DC converter modules are used to both provide 5V for the logic cicuitry and the power for the output side of the Can bus tranceiver. An RJ45 socket is fitted to the board to allow direct connection to the inverter with via the supplied cable.

 
The PCB, BMS, 100A circuit breaker / isolator and indicator led's are to be mounted into a 'control box' mounted on the front of the main battery assembly for good access for maintenace.



Update 8/3/2024

The circuit board laminate has been recieved and populated. The ATMega328 has been flashed with a blink skech to check the circuit is basicaly alive, 5V is being supplied and programming ports are opearational, an led is connected to the relay output, the led flashes as expected. As yet its not possible to upload skethes via the serial port however serial data can be read for debugging, uploading the code via the ISCP port works ok, I'll look into this at a later date.
All components have been fitted into the control box which is made from 2mm sheet aluminium and painted NATo green with orange highlighs which is the colour used for my projects.

A temporary battery has been assembled from 16 x 18650 cells from a defunkt ebike battery and connected to the 'voltage sense' inputs of the pcb and the relevent wires to the BMS together with the battery -Ve wire. A small issue was found with the hard coding part of the pcb which was discoverd when only 13 of the cells showed on the Overkill solar (bluetooth) app, this was soon remidied and the app then showed the full 16 cells with a stable reading of 67.5V which tallied with a reading from a DVM.
Shortly after the bluetooth started to randomly drop out, this became worse over a period of minutes until the app is constantly 'waiting for BMS'. The BMS is still showing in the serach, all data held in the BMS has been lost, the temperature inputs are shwoing -273 degress. The blue led on the BMS is flashing at 1 second intervals.

update 20/3/2024

Main control panel pretty much finished:
![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/a5bf5a7c-004c-4efd-84b1-7521f7a99042)

An RS485 / BMS simulator has been knocked up to test the circuit board which seems to be working nicely:

![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/163600e2-1889-4812-b2cc-d5b1fdfffff7)




