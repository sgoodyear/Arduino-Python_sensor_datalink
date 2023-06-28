Takes specially formatted data from an Arduino's serial output:

***baud rate set to 600 by default, otherwise the python program will get overwhelmed***

.

[sensorname1] [sensorname2] [sensorname3]                                                                                >first line: spacebar separated sensor id's (3 digits)

[3_digit_sensor_id][sensor_data],[3_digit_sensor_id][sensor_data],[3_digit_sensor_id][sensor_data],...,                  >main datastream

...                                                                                                                      >continues for as long as you want

...                                                                                

...

!                                                                                                                        > "!" to signal end of data


Takes the data and uses a pandas dataframe to store it, then when it recieves the "!", it converts the
dataframe into a .csv ("comma separated value") file that can be optionally imported into Google Sheets
or Microsoft Excel to further analyze the data.


The .csv files included here contain example data from an airspeed sensor and two MQ-2 gas smoke/flammable
gas sensors that you would see as the output of the first python program given the arduino program as input.
