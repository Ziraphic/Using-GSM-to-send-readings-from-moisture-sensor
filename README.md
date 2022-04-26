# Using-GSM-to-send-readings-from-moisture-sensor
# ABSTRACT
It is a big issue to know the soil moisture without direct contact to the zone where the moisture sensor is located or other weather station. This issue leads to different effects especially where such information is too important. This prototype uses Arduino Uno board which is easy to be programmed and economical. The way it is programmed, the moisture sensor will sense the moisture in the soil, and send and give values of moisture according to the wetness or dryness of soil to the Arduino board. Arduino will record values of moisture sensor and make a GSM module send those values to a specific location (number) by using SMS (Short Message Service). This will help to know the moisture in the soil remotely, so other decisions can be made. Easy access to the information about moisture in soil by using GSM technology is what the prototype offers.

# PROBLEM STATEMENT
Soil parameters are needed in different sectors of modern life, such as in agriculture, metheo boards and in weather stations. Sometimes it requires a human to recognize the values of soil moisture but by reaching the exact place. Different decisions are taken but after visiting the place where the sensor is placed. It became difficult to visit the station daily.
Many issues have been related to the global warming. One of the effects of global warming is the dryness of soil in plantation. Increased in temperature will caused the soil to become very dry and not suitable for agricultural activities.[1]

Most of agriculture uses different methods of irrigation so that many farmers use scheduled irrigation systems. Some farmers use time based switches or planned hours to irrigate. In this method, there will be constant time to irrigate without knowing whether the soil is wet or dry. Through this, crops may get too wet above the desired level so that they may be damaged. The same as dry time,

Also people in urban area tend to grow plants in pots on their balconies but due to their busy schedule they do not have time to take care of their garden[1] 


# MAIN COMPONENTS TO BE USED
1.	Arduino Uno board
The Arduino UNO is an open-source microcontroller board dependent on the Microchip ATmega328P microcontroller and created by Arduino.cc The board is furnished with sets of computerized and simple info/yield (I/O) sticks that might be interfaced to different extension sheets (shields) and different circuits. The board has 14 Digital pins, 6 Analog pins, and programmable with the Arduino IDE (Integrated Development Environment) by means of a sort B USB link.[2]
 ![image](https://user-images.githubusercontent.com/103578178/165391655-d518458e-40c0-4755-ba51-475a6718ba8d.png)

# Figure 1: Arduino Uno board

# 2.	Moisture sensor
 Hygrometer various sorts of sensors can be utilized for the estimation of soil mugginess. In that venture, these sensors are utilized for soil dampness. Hygrometer is one sort of humidity sensor which has capacity of estimating the water vapor in the air. It’s utilized for both computerized and simple. Yield of the sensor gives as a contribution of an Arduino Uno. Soil Humidity Sensor Hygrometer Maintaining the Integrity of the Specifications[2].
Moisture sensor is used to monitor the moisture content in the soil. It is to avoid the soil to become too dry or too wet. It is because, too little or excessive of water may be harmful to the plant.[1]

  ![image](https://user-images.githubusercontent.com/103578178/165391756-1c6ed5ac-dc20-492d-8708-5759c9d587e1.png)

# Figure 2: Soil moisture sensor

# 3.	GSM module

Meanwhile, through this project, GSM module has been used as transceiver system that uses a network provider to connect and transfer data. GSM modem is a simple device which uses a SIM card to send and receive the messages to/from the user. The modem can be controlled by Arduino using serial communication. AT commands are used to configure the GSM modem. GSM is proposed to be used in this prototype because it is will enable the user to know the value/level of moisture remotely, unlike using wireless system which enable only at certain specific range.[1]
GSM module is utilized to set up correspondence between a PC and a GSM framework. Worldwide System for Mobile correspondence (GSM) is a design utilized for portable correspondence in a large portion of the nations. Worldwide Packet Radio Service (GPRS) is an expansion of GSM that empowers higher information transmission rate.[2]

  ![image](https://user-images.githubusercontent.com/103578178/165391856-c54b888a-b572-4e0f-a2e9-d4715360a6ee.png)

# Figure 3: GSM module



# BLOCK DIAGRAM
![image](https://user-images.githubusercontent.com/103578178/165392191-7f205fd2-79d2-4708-a4d8-9bb52a094765.png)

# DESCRIPTION
5DCV power supply is generated from USB cable which is connected Arduino board. The soil moisture sensor is connected to analog pins of Arduino board and the data sensed by soil moisture sensor is transmitted to microcontroller. GSM module is initialized and waits until it connects to the network. 12v power supply is scheduled to the GSM module through adaptor. Values which are received from sensor are sent to a specific number declared in Arduino through GSM communication. Arduino is connected to GSM module in which transmitter of Arduino is connected to the receiver of GSM module and receiver of Arduino is connected to the transmitter of GSM module.
The mobile number declared in Arduino will receive an SMS include the values read by moisture sensor but in certain time.

# SOURCE CODE FOR THE CIRCUIT

#include<SoftwareSerial.h>\

int readings=0;

SoftwareSerial mySerial(2,3);


void setup()

{

  mySerial.begin(9600);
  
  Serial.begin(9600);
  
  pinMode(A0,INPUT);
  
  boolean notconnected=true;
  
  Serial.println(readings);
  
  while(millis()<5000);
  
}

void loop()

{

Serial.print("Readings: ");

  Serial.println(readings);
  
  
  mySerial.println("AT+CMGF=1");//sets the GSM module in text mode
  
  delay(1000);//dalay of 1000 milli seconds or 1 second
  
  mySerial.println("AT+CMGS=\"+250783986252\"\r");//numberwhere readings of sensor are sent
  
  delay(1000);
  
  mySerial.println("Readings of soil moisture sensor are: ");
  
  mySerial.println(readings);
  
  delay(100);
  
  mySerial.println((char)26); 
  
  delay(1000);
  
}

# CIRCUIT IN PROTEUS
 ![image](https://user-images.githubusercontent.com/103578178/165393221-fd7e9bca-96c6-47ba-a10d-13b0793192f2.png)

# References
[1]	“GSMactivatedwateringsystemprototype.pdf.” 

[2]	“A9991058119 moisture sensor.pdf.” 



# done by:
NIYIGIRIMBABAZI JOSEPH 

MUGENI REBECCA
