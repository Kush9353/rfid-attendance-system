# rfid-attendance-system
This project creates an RFID-based touchless attendance system with an automatic door locking mechanism using an Arduino Uno.


Project Overview
The system is designed to grant access and mark attendance when an authorized RFID card is presented. When a valid card is scanned, the system unlocks a door for a set period and records the attendance. If an invalid card is scanned, it triggers a warning light and buzzer.




Core Components
The following components are required for this project:


Arduino Uno with a USB Type-A to Type-B cable 


EM-18 RFID Reader Module 


Relay Module connected to a door motor 

Red Warning Light and a Buzzer 

Jumper wires 


Arduino IDE for programming the microcontroller 

System Architecture and Functionality
The system's functionality is controlled by an Arduino Uno, which is connected to the various modules as depicted in the block diagram.

Connections:

The EM-18 RFID Reader's transmitter (TX) pin is connected to the Arduino's receiver (RX) pin (Digital Pin 0) to send scanned tag data.



A relay module, which controls the door motor, is connected to digital pin 13 of the Arduino.


A red LED, acting as a warning light, is connected to digital pin 12.


Operation:

The system initializes and prints "SPT 5th Sem Touchless Attendance System" to the serial monitor. The door is initially kept locked by setting the relay pin to HIGH.


The Arduino continuously listens for data from the EM-18 RFID reader. An RFID card has a 12-byte unique ID.



When a card is scanned, the Arduino reads the 12-byte ID and compares it to a pre-defined authorized tag ID ("08006A7A657D") stored in the code.



Authorized Access: If the scanned tag matches the authorized tag, the system prints "Roll no-21 present" to the serial monitor. It then activates the relay by setting its pin to LOW, which unlocks the door motor for 5 seconds. After the delay, the relay is deactivated, locking the door again.




Unauthorized Access: If the scanned tag does not match, the system prints "Invalid student roll number!" to the serial monitor. The red warning light connected to pin 12 is turned on for 5 seconds to indicate an invalid attempt.


A separate procedure is noted for initially identifying a card's ID: the RFID reader's TX pin should be connected to the Arduino's TX pin to display the card's unique ID on the serial monitor. This ID can then be used as the authorized 

tag value in the main code.
