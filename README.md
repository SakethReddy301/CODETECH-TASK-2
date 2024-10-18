NAME: VELIDANDI SAKETH REDDY
COMPANY: CODTECH IT SOLUTIONS  
ID: CT08DS8242
DOMAIN: EMBEDDED SYSTEMS  
DURATION:SEPTEMBER TO OCTOBER 2024  
MENTOR: 

OVERVIEW OF THE PROJECT 
---

Project: Temperature and Humidity Monitoring with DHT Sensor

---

Objective: The objective is to interface a DHT sensor with an Arduino to measure temperature and humidity, displaying the readings on a 16x2 LCD screen. This project demonstrates the process of acquiring real-time environmental data and displaying it for monitoring purposes.

---

Components Required:
1. Arduino Board (e.g., Arduino Uno)
2. DHT11 or DHT22 Sensor (for temperature and humidity readings)
3. 16x2 LCD Display
4. Breadboard and Jumper Wires
5. Resistor (optional, if needed for the DHT sensor)

---

Key Concepts:
1. DHT Sensor: Measures both temperature and humidity.
2. LCD Display: Displays data such as temperature and humidity for easy viewing.
3. Arduino Control: Controls the process of reading data from the sensor and updating the LCD screen in real-time.

---

Steps to Implement the Project:

Setting Up the Hardware:
- DHT Sensor Connections:
  - Connect the VCC pin of the DHT sensor to the 5V pin on the Arduino.
  - Connect the GND pin to the GND on the Arduino.
  - Connect the DATA pin to digital pin 12 on the Arduino.

- LCD Display Connections:
  - Connect the LCD pins to the following Arduino pins:
    - RS (Register Select) to pin 2
    - Enable to pin 3
    - D4 to pin 4
    - D5 to pin 5
    - D6 to pin 6
    - D7 to pin 7
  - Connect VCC and GND of the LCD to the 5V and GND pins on the Arduino.

Writing the Arduino Sketch:

```cpp
#include <dht.h>          // Including library for DHT
#include <LiquidCrystal.h> // Library for LCD

LiquidCrystal lcd(2, 3, 4, 5, 6, 7);
#define dht_dpin 12
dht DHT;

byte degree[8] = {
  0b00011,
  0b00011,
  0b00000,
  0b00000,
  0b00000,
  0b00000,
  0b00000,
  0b00000
};

void setup() {
  lcd.begin(16, 2);
  lcd.createChar(1, degree);
  lcd.clear();
  lcd.print("   Humidity   ");
  lcd.setCursor(0,1);
  lcd.print("  Measurement ");
  delay(2000);
  lcd.clear();
  lcd.print("Circuit Digest ");
  delay(2000);
}

void loop() {
  DHT.read11(dht_dpin);
  lcd.setCursor(0,0);
  lcd.print("Humidity: ");
  lcd.print(DHT.humidity);   // Display Humidity
  lcd.print(" %");
  lcd.setCursor(0,1);
  lcd.print("Temperature:");
  lcd.print(DHT.temperature); // Display Temperature
  lcd.write(1);
  lcd.print("C");
  delay(500);
}
```

Uploading the Sketch:
1. Connect your Arduino to your computer using a USB cable.
2. Open the Arduino IDE and select the appropriate board (e.g., Arduino Uno) and port.
3. Click on the Upload button to compile and upload the sketch to your Arduino.

---

Observing the Output:
- Once the code is uploaded, the temperature and humidity readings will be shown on the 16x2 LCD display.
- The data will refresh every 500 milliseconds, showing real-time environmental data in a user-friendly format.

---

Learning Outcomes:
- Sensor Integration:You’ll learn how to interface with the DHT sensor to measure temperature and humidity.
- LCD Display Handling: Learn to display sensor data in a structured format on a 16x2 LCD.
- Embedded Programming: Acquire the skill of reading real-time environmental data and presenting it using Arduino. CODETECH-TASK-2
