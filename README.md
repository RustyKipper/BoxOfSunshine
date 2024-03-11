# Solar storage
Solar battery to inverter interface

A need arose to make use of some redundant roof mounted PV panels so it was decided to install a battery system to store the power generated duing daylight hours and use cheap rate night time electric to completely fill the battery on overcast or winter days. Several comercial batteryies are availiable but they tend to be in a rack mounting format and are very hravy to drag up into the loft space.
A design has been drawn up to use 16 off 305Ah LifePO4 cells mounted in a linera fasuin to make use of my limited loft space and allow the aprox 120Kg weight of the battery to be mounted up agaist the gable end and over a load bearing wall.
Another requirement was to build the battery into an metal box to porvide some rudimentery fire proofing.

The system will consist of this 14.6Ah / 48V battery and a Solis hybrid inverter. The battery is to include the BMS, main isolator and a custom made circuit board to act as a 'companion' to the BMS. It will porovide a convienient interface to the battery sense wires thus no requirement to extend the wires that come with the BMS and also to accomadate the front end wiring to the BMS wich allows it to know that the system is a 16S (16 cells in series system.

This code is for the Rusty Kipper Designs JBD to Solis hybrid inverter interface PCB.

The PCB does 2 things;
1. The microcontroller (ATMega328) sends a request to the JBD BMS RS485 port requsting the current battery status and values such as state of charge, Voltage, charge / discharge current ect. The code then pulls out the relevent pieces of data from the replied data packet, these pieces of data are then converted to both a user readable format for debugging and a format that the invreter can understand. The inverter data is then transmitted via isolated canbus to the invreter. An isoladed Can bus tranciever has been selected as people have had issues with non isolated Can bus transievers failing if the battery is not connected to the inverter which likely creates a Voltage potential or transient above the rating of the tranciever.
2. The pcb connects the BMS battery sense inputs to a set of screw connectors that allow easy connection of the sense wires from the battery terminals to the BMS without soldering or otherwise extending the wires. The pcb also makes the specific links and connections to set the BMS to a 16S configuration that can be tricky to hard wire.


![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/8fdd459a-3a08-4481-8e2a-692963963aa8)



![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/d4e5e7fd-4e51-45e1-9860-404ca554d5ba)

![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/00a1ab72-6e7b-455f-8693-a086ceed744e)


![image](https://github.com/RustyKipper/BoxOfSunshine/assets/160714870/e1899716-46f9-40d1-ae5e-22499ca01d6f)



