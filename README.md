## CS207-Fall2020

#### By Tori Sambrook

## The Modern Clock

For this project, an old analog clock was converted into a digital clock and weather forecasting device. A printed circuit board from an old computer was used as a background for the clock, and a Nokia 5110 LCD was used for a display. To determine the time and current weather, a DS1307 RTC module and BME280 module were implemented in the circuit. An additional touch sensor was added to the circuit which functions by turning on/off LEDs when a piece of metal is touched. Below is an image of the final device:

![Image of Modern Clock](https://github.com/torisambrook/CS207-Fall2020/blob/main/img/IMG_1319.png)

## Repository contents
 - **/src** - contains the source code used to implement the Modern Clock. 
 - **/hardware** - contains the design files for the Modern Clock (separated into the weather forecasting clock and touch sensor diagrams).
- **/libraries** - contains the libraries used to implement the modern clock.
 - **/img** - various images ilustrating the Modern Clock design and build process.

## Requirements and Materials
**Libraries**

All of the libraries required for this project are found in the /libraries folder. They can also be found at the following sources: 
- DS1307 Library (for setting the time, requires Time Library): https://github.com/PaulStoffregen/DS1307RTC
- Time Library: https://github.com/PaulStoffregen/Time
- Adafruit BME280 Library: https://github.com/adafruit/Adafruit_BME280_Library
- RTC 1307 Library: http://www.rinkydinkelectronics.com/library.php?id=34
- LCD5110 Graph Library: http://www.rinkydinkelectronics.com/library.php?id=47

**Materials**
- Old analog clock (or any frame of choice)
- Old printed circuit board (PCB) for a background
- Arduino Nano (R3)
- Breadboard for connections
- BME 280 sensor module (temperature, humidity, pressure)
- Nokia 5110 LCD display
- DS1307 RTC module
- Photoresistor/Light dependent resistor (LDR)
- Buzzer/speaker (if implementing alarm sounds)
- 3 push buttons
- Resistors: 1MΩ, 2x10KΩ, 270Ω, 150Ω<
- Micro USB cable for power
- 1+ LED(s) (for the touch circuit)

## Build Instructions
To build the Modern Clock, the build is divided between the weather forecast clock and touch sensor circuts. The circut designs and schematics are outlined below. 

#### Weather Forecast Clock
- The LCD has 8 pins: VCC goes to 5V, GND to ground, and the other six connections starting at RST go to digital pins 12-7. 
- The BME 280 Module has four connections: VCC to 3.3V, GND to ground, SDA to pin A4 and SCL to pin A5. 
- The RTC module has 4 pins, all the same connections as the BME 280 module. 
- Two of the push buttons have one end to ground and the other to D3 and D4. The third button, the menu button, has a connection from ground to a 10KΩ resistor, to pin D2, to the button, then to 5V. It works as a pull-up button. 
- The photoresistor is connected on one end to A3 and on the other to A1 and a 10KΩ resistor to ground. 
- The Arduino Nano 5V is connected to one positive rail on the board and 3.3V is connected to the other. The ground is connected to both negative rails. 
- In the original code, a speaker is implemented at digital pin 6. However, the memory space did not permit the code for this and the pin was instead used for the touch sensor circuit. 

![Image of Weather Forecast Clock Schematic](https://github.com/torisambrook/CS207-Fall2020/blob/main/img/Clock%20Sketch_schem_before_lights.jpg)

![Image of Weather Forecast Clock Circuit](https://github.com/torisambrook/CS207-Fall2020/blob/main/img/Clock%20Sketch__before_lights.jpg)

#### Touch Sensor
- Any LEDs are attached to pin A2 as output, then the negative end is attached to the ground with a low value resistor (150Ω or less). 
- For the touch sensor, pin 5 is attached to one end of a 1MΩ resistor, the other goes to pin 6 and to the metal sensor. 
Since so many of the pins are already being used, I could only manage these pins for the circuit.

![Image of Touch Sensor Circuit](https://github.com/torisambrook/CS207-Fall2020/blob/main/img/LED_schm.png)

## Firmware Installation
When the circuits are built, there are a few steps that first need to be completed before uploading the code. 
1. Install Arduino IDE.
2. Install libraries used in this project found in the /libraries folder.
3. Run the setTime example code from the DS1307RTC library. This is necessary in order to initally set the time on the RTC clock. 
4. Download the source code found in the /src folder. The code is ready to be uploaded to the project.

If the memory space on the driver permits it, certain parts of the code can be added again by removing the comment bars from them. For example, the playSound() function could be added back to the sketch. 

## Usage
When the software is uploaded to the Modern Clock, the current time will appear to the screen. The screen will rotate through various information including the temperature, humidity, pressure, and voltage/battery. If the menu button is pressed, then a menu will appear which could allow the user to view the data, set an alarm or the time, or exit the menu. The second button is used to move forward through the options, and the third button moves backwards through the options. The menu button can also be pressed as an "OK" button to select one of the options. 

The photoresistor is used to turn on the light on the Nokia LCD if there is motion in front of the clock. If there is no motion for a certain period of time, the light on the LCD will turn off and the information will continue to display. If the clock light is off and the button is pressed the LCD light will turn back on. If the metal piece on the side of the clock is touched, the LEDs attached to analog pin A2 will turn on/off. 

## Presentation
A video presentation demonstrating the design and build for this project can be found at: 

## Credits
The original design and code for the weather forecast clock is created by LenkaDesign and is referenced in the sources [1] through [4]. The touch sensor circuit is adapted from code created by Amel Mathew and can be found at reference [5]. 

## References
 [1] Design, L. (2018, July 21). \emph{Weather Forecast Clock Using Old Alarm and Arduino.} Retrieved December 7, 2020, from https://create.arduino.cc/projecthub/LenkaDesign/weather-forecast-clock-using-old-alarm-and-arduino-c1bb67?ref=similar\&ref\_id=122346\&offset=5

 [2] Design, L. (2018, July 3). \emph{LenkaDesign/Weather-Forecast-Arduino-Clock.} Retrieved December 7, 2020, from https://github.com/LenkaDesign/Weather-Forecast-Arduino-Clock

[3] Design, L. (2018, August 05). \emph{Weather Forecast Clock Using Old Alarm and Arduino.} Retrieved December 7, 2020, from https://www.instructables.com/Weather-Forecast-Clock-Using-Old-Alarm-and-Arduino/

[4] Design, L. (2018, August 05). \emph{How to make Weather station - Arduino, Nokia 5110 LCD and an old clock.} Retrieved December 7, 2020, from https://www.youtube.com/watch?v=-FDuY51MYSw

[5] Mathew, A. (2018, January 27). \emph{Touch Controlled Light Using Arduino.} Retrieved December 7, 2020, from https://create.arduino.cc/projecthub/amalmathewtech/touch-controlled-light-using-arduino-d2f878
