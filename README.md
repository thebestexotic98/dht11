Room Thermometer Using DHT11 Sensor

Introduction

The purpose of this project is to measure the room humidity and temperature based on CPLD implementation. The humidity and temperature sensor used in this project 
is DHT11 sensor as the sensor is a two-in-one sensor for temperature and humidity measurement. This sensor has three pins, namely VCC, GND and DATA.
DHT11 uses a single bus for communication which is the line that connecting the DATA pin to the microcontroller which is the CPLD. When the microcontroller is
not interacting with DHT11, the bus is in an idle state and it will be in high level state with the action of a pull-up resistor. When the microcontroller and
the sensor are communicating, the bus is in the communication state. A complete communication process can be seen in the timing diagram below.




Figure 1: Timing Diagram of the DHT11.

 



1.    First, the microcontroller configures the IO of the drive bus as an output mode and ready to send data to DHT11 sensor.

2.    The microcontroller then pulls the bus down for at least 18ms to send the start signal. After that, it pulls the bus high and delay for 20-40 to end the start signal. 

3.    The microcontroller configures the IO of the drive bus as input mode, and ready to receive the DHT11 response.

4.    When DHT11 detects the start signal given by the microcontroller, it will send out a low voltage level response signal for 80.
Then it pulls up the voltage and keeps it at 80 to prepare for data transmission. 

5.    When DHT11 sends data to MCU, every bit of data begins with the low voltage level for 50 and the next high voltage level signal length
will determine whether the data bit is “0” or “1”. If the high voltage level length is for 26-28, the bit is “0” and if the high voltage level length is for 70,
the bit will be “1”. 


The data transfer from the DHT11 will be displayed through the 7-segment display.
There is a total of four 7-segment display used in this project. Each of the 7-segment display give different reading which are the 8-bit humidity reading,
8-bit fractional humidity reading, 8-bit temperature reading and 8- bit fractional temperature reading. 

Software:

The software used in this project is Quartus II 13.0 Web Edition.


Hardware:

The hardware used in this project are listed below:
1.     DHT11 Temperature Sensor
2.     Common Anode 7-Segment
3.     EPM240T100C5 CPLD


DHT11 Sensor Specification:

Operating Voltage: 3.5V to 5.5V
Operating Current: 0.3mA (measuring), 60A (standby)
Output: Serial data
Temperature Range: 0 to 50
Humidity Range: 20 to 90
Resolution: Both Temperature and Humidity are 16-bit
Accuracy:  and  


Flowchart of Overall Project









 



Figure 2: Flowchart of overall room thermometer project.

Methodology: From the coding


Firstly, the DHT11 sensor is configure by using the Verilog Code below to enable the
data transfer and communication between the microcontroller and the sensor.
Through the coding, there is a total of 8 state for the sensor to detect and
transfer the humidity and temperature value as input to the microcontroller.
The microcontroller then processes the input data and displayed it as output
through the 7-segment display.



There are four unit of 7-segment display used and the display are arranged side to
side on the breadboard. From the left side, the first 7-segment will display
the 8-bit value of humidity reading, next unit will display the value of
fractional humidity reading. The third unit of the 7-segment will display the
8-bit temperature reading value and the last one displays the 8-bit fractional
temperature reading.
