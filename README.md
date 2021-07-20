Room Thermometer Using DHT11 Sensor

GROUP NAME: CAD Maniac

MEMBERS:
1. ASHRAF AMININ BIN ARMAN ALIM (A17KE0034)
2. MAHMUDA BINTI ISMAIL (A17KE5295)
3. NOR FARAH AFIQAH BINTI ABDUL RAHIM (A17KE0216)
4. NUR IRDINA BINTI MOHD SHAHRIR (A17KE0229)

LECTURER’S: PM MUNIM AHMAD ZABIDI

1.0 Introduction:

The purpose of this project is to measure the room humidity and temperature based on CPLD implementation. The humidity and temperature sensor used in this project 
is DHT11 sensor as the sensor is a two-in-one sensor for temperature and humidity measurement. This sensor has three pins, namely VCC, GND and DATA.
DHT11 uses a single bus for communication which is the line that connecting the DATA pin to the microcontroller which is the CPLD. When the microcontroller is
not interacting with DHT11, the bus is in an idle state and it will be in high level state with the action of a pull-up resistor. When the microcontroller and
the sensor are communicating, the bus is in the communication state. A complete communication process can be seen in the timing diagram below.




Figure 1: Timing Diagram of the DHT11. Link: https://imgur.com/a/Hi1zDhX


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

2.0 Software:

The software used in this project is Quartus II 13.0 Web Edition.


3.0 Hardware:

The hardware used in this project are listed below:
1.     DHT11 Temperature Sensor
2.     Common Anode 7-Segment
3.     EPM240T100C5 CPLD


DHT11 Sensor Specification:

1. Operating Voltage: 3.5V to 5.5V
2. Operating Current: 0.3mA (measuring), 60A (standby)
3. Output: Serial data
4. Temperature Range: 0 to 50
5. Humidity Range: 20 to 90
6. Resolution: Both Temperature and Humidity are 16-bit
7. Accuracy: Plus minus 1 degree celcius and Plus minus 1%


4.0 Flowchart of Overall Project:

Figure 2: Flowchart of overall room thermometer project. Link: https://imgur.com/a/FyOmKHj


5.0 Methodology:


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

6.0 Result & Discussion:
1. As you can see, we give two different coding (DHT11 sensor and 4 digit 7-segment display).
2. From the simulation, we could not receive any result from the DHT11 sensor but we receive the simulation result for the 7-segment display. This is the link for the simulation output waveform: https://imgur.com/a/h9bNcB0
3. For the hardware part, as you can see we have a problem for dht11 sensor to work because it cannot receive signal from the microcontroller, so dht11 sensor
cannot function. But when we troubleshoot the dht11 sensor with arduino, it work perfectly. So, we conclude that it have a problem with the connection from the
microcontroller or CPLD.
4. For the 4-digit 7-segment display, we actually make it work but due to hardware troubleshooting, we lost the output.
5. Then, we try to combine it together into one code, but still when we uploaded the code to the CPLD, it did not work because the 7-segment display give output 0
(means that it did not receive any input from the dht11 sensor). After that, due to troubleshooting of the hardware, we lost again the output.
6. So, this youtube video will show the progress of our project: https://youtu.be/nDr88O4JYqg . This video just show the simulation of the 7-segment display and the
hardware progress for 7-segment display.

7.0 Project References
1. Verilog code dynamically displayed by 4-digit 7-segment common cathode digital tube - Programmer Sought. (2020). Programmersought.com. https://www.programmersought.com/article/97147360817/
2. [FPGA Tutorial] Seven-Segment LED Display on Basys 3 FPGA. (2017). Fpga4student.com. https://www.fpga4student.com/2017/09/seven-segment-led-display-controller-basys3-fpga.html
3. DHT11–Temperature and Humidity Sensor. (2018). Components101. https://components101.com/sensors/dht11-temperature-sensor
4. [FPGA] Verilog code to realize temperature and humidity sensor DHT11 - Programmer Sought. (2020). Programmersought.com. https://www.programmersought.com/article/90045264630/
5. Temperature and humidity measurement based on FPGA and DHT11 - Programmer Sought. (2018). Programmersought.com. https://www.programmersought.com/article/38214979535/
6. FPGA driver code for DHT11 temperature and humidity sensor - Programmer Sought. (2020). Programmersought.com. https://www.programmersought.com/article/58114878413/
