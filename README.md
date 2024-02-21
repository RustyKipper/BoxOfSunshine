# BoxOfSunshine
Solar battery to inverter interface

This code is for the Rusty Kipper Designs JBD to Solis hybrid inverter interface PCB.

The PCB does 2 things;
1. The microcontroller (ATMega328) sends a request to the JBD BMS RS485 port requsting the current battery status and values such as state of charge, Voltage, charge / discharge current ect. The code then pulls out the relevent pieces of data from the replied data packet, these pieces of data are then converted to both a user readable format for debugging and a format that the invreter can understand. The inverter data is then transmitted via isolated canbus to the invreter. An isoladed Can bus tranciever has been selected as people have had issues with non isolated Can bus transievers failing if the battery is not connected to the inverter which likely creates a Voltage potential or transient above the rating of the tranciever.
2. The pcb connects the BMS battery sense inputs to a set of screw connectors that allow easy connection of the sense wires from the battery terminals to the BMS without soldering or otherwise extending the wires. The pcb also makes the specific links and connections to set the BMS to a 16S configuration that can be tricky to hard wire.
