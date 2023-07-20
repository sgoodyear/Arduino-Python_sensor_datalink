The latest version of the software to interface with Mine_Evacuation.py is labeled as "V3" for the Arduino and Python portions of the program.
In this verison, the Arduino uses an i2c bus multiplexer to read 14 AHT20 temperature sensors on the i2c bus, along with analog gas detection sensors
and sends the data over a serial connection to the Python program for live graphing.


During startup, the Arduino sends status messages over the serial connection, which the Python program will pass to it's terminal until the Arduino sends
"Data to follow:", after which point the Python program reads the next 2 lines of serial to determine first which sensors are being used (all sensors are
assigned a unique 3-digit identifier by the user inside the startup sequence of the Arduino program) and second at which nodes the sensors are located (also
set by the user inside the Arduino program).


After the first 2 lines of preliminary data, the Arduino sends and the Python program reads sensor data formatted as:


[sensor's 3-digit ID][sensor's data],[next sensor's ID][sensor's data],...   ...,


Note that the Arduino does not use brakets to separate the sendor ID or sensor data, they are sent one right after the other and the different sensor/data groups
are separated by commas. An important thing to note is that the datastream ends with a comma, which the Python program is hard-coded to filter out.


Example data stream:


S010,S020,S030,S04218,S052427,S062536,S072100,S081909,S091827,S102236,S111963,S121663,S131581,S141418,S152427,S161963,A010.19,T0122.64,T0222.34,T0322.99,T0422.75,T0522.53,T0622.81,T0723.02,



When the digital pin 53 on the Arduino Mega is pulled low by the switch, the Arduino sends "!" over serial to signal the Python program to stop graphing data
and to write it to the duplicate.xlsx file. The file overwrites itself each time the program is run, and is formatted so that the Mine_Evacuation.py program
can load and interpret it's data.

[The Mine_Evacuation.py program is set as read-only and is not modified]
