# Seceft_Defender (Kavach)


# Introduction:
The project SECEFT DEFENDER (security theft ) defender describes that
As, nowadays we know that protecting our personal belongings ,data , or perosnal things to keep it safe and secure from others either it's in form of money ,data, jewelleries , etc. ….
What everyone is doing that , they are keeping their money safe at their home by using automatic or secure locked locker at their home or ,some people's put these things in their bank lockers , and for a big companies like MnC their data is so much crucial and they wants to safe their data from their competitors ….so, if I take example of bank then, bank has the responsibilty of protecting locker facility so, that any thief will not come and theft all people perosnal belongings. And If I say , that after bank timings become over and it is closed then, who is responsible for that ? For securing and keep an eye on bank lockers ,etc. So, in this type of situation What they actually do is that they  hired a guard …and  cctv's cameras are established but …guard is human being to whom the theives can easily do unconscious and also using advanced technologies they can dismiss the CTVS cameras as well and stile all things from bank lockers …or same is the case of co pany ….so, what if I say that ….I have an advanced solution of all of your this problems using which you can protect your personal belongs ,data etc ..
Yes, actually the solution of this problem is where this Idea arises …
SECEFT DEFENDER (security theft ) defender ..this is a prototype model wn which we are using some sensors for keep an eye on the theives  these sensors are Ultrasonic sensor , …PIR sensor and laser sensor ..and if in any case, one sensor failed or disabled then others are their for working …and the excited feature of this prototype is that …..you can establish or purchase this at a very minimal or affordable cost … 

As ,you all have seen in some of the movies that they are using laser technology for protecting their crucial data …so, laser technology is a very advanced technology and protected technology and if all sensors fails but there is always a backup and more protected solution is laser one cannot get rid from laser light and it caught the thief and it become easy for the others to protect their data ….

So, this is just a small and brief overview on our idea ….


This is what our project describes. .. 

Now ,let's come to the purpose of our project …

# Purpose
The main purpose of our project is to protect the secure data, crucial personal belongings from stolen by the thieves/anyone ….. The personal belongings or data can be either in the form of bank lockwers, money at home, company’s personal secure properties , Jewelleries , etc.  


# Applications of SECEFT

The applications of SECEFT  are ➖


# Some Actions and Features of Product  

Primary Action and Features of the Product are given below:- 

• Security 
• Monitoring
 • Alarm 
• Detect motion 
• Track
• Respond 
• Display Message


# Block Diagram of the Product 

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/0124acb8-28ca-42bc-9eee-c8606955354d"></br>
   
</p>

     
# Components Required 

## → Hardware Components Used

| Component name  | Quantity Required | Unit price  | Total Price (Unit price*Quantity) |
| ------------- | ------------- || ------------- | ------------- || ------------- | ------------- |
| Ultrasonic Sensor  | Quantity Required | Unit price  | Total Price (Unit price*Quantity) |


## Software Used

- Arduino IDE Open Source Software
- C code

### Connections Diagram of the Product with VSDQuadron Board (Riscduino Board)

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/94f7f43c-b06f-4c3f-88a9-12533b216c5b"></br>
    
</p>

# Flowchart of the Product

# Algorithm of the Product

- When any person enters into the room .
- He/she crosses the measured distance .
- Ultrasonic sensor detects it and activates the alarm, alarm buzzes and it is displayed on LCD that alarm buzzes due to ultrasonic sensor.
- If ultrasonic sensor ,not able to detect or person , escapes from ultrasonic sensor, then, PIR sensor detects motion, and alarm triggers ,and it is displayed on LCD that alarm buzzes due to PIR sensor.
- If PIR sensor ,not able to detect or person also, escapes from PIR  sensor, then,the Laser Module is also their for monitoring .
- If someone crosses the laser beam, alarm triggers and it is displayed on LCD that alarm buzzes due to Laser module.
- LDR also monitors ambient light, and due to this only, laser module detects the person.
 - If in any case or situation whenever someone tries to block the sensor, Alarm Triggers.
- When any sensors are triggered, buzzer starts buzzing to alert nearby persons.
- LCD display shows, information about intruder and throws message.
- LCD display also shows, information that due to which sensor the alarm buzzes .


# C code in Arduino UNO

```

#include <LiquidCrystal.h>
// Pin assignments
const int PIR_PIN = 2;                                                 //
const int LDR_PIN = A0;
const int LASER_PIN = 3;
const int ULTRASONIC_TRIG_PIN = 5;
const int ULTRASONIC_ECHO_PIN = 6;
const int BUZZER_PIN = 4;
const int LCD_RS_PIN = 12;
const int LCD_EN_PIN = 11;
const int LCD_D4_PIN = 5;
const int LCD_D5_PIN = 4;
const int LCD_D6_PIN = 3;
const int LCD_D7_PIN = 2;
const int SWITCH_PIN = 7;

// System state
boolean alarmTriggered = false;
boolean alarmStopped = false;

// Sensor readings
int PIR_reading = 0;
int LDR_reading = 0;
long ultrasonic_distance = 0;

// LCD display
LiquidCrystal lcd(LCD_RS_PIN, LCD_EN_PIN, LCD_D4_PIN, LCD_D5_PIN, LCD_D6_PIN, LCD_D7_PIN);

void setup() {
  // Set up the PIR sensor
  pinMode(PIR_PIN, INPUT);

  // Set up the LDR sensor
  pinMode(LDR_PIN, INPUT);

  // Set up the laser module
  pinMode(LASER_PIN, OUTPUT);

  // Set up the ultrasonic sensor
  pinMode(ULTRASONIC_TRIG_PIN, OUTPUT);
  pinMode(ULTRASONIC_ECHO_PIN, INPUT);

  // Set up the buzzer
  pinMode(BUZZER_PIN, OUTPUT);

  // Set up the LCD display
  lcd.begin(16, 2);
  lcd.print("Theft Security System");

  // Turn on all sensors
  digitalWrite(LASER_PIN, HIGH);
  digitalWrite(ULTRASONIC_TRIG_PIN, HIGH);
  pinMode(SWITCH_PIN, INPUT);
  digitalWrite(SWITCH_PIN,HIGH);

}

void loop() {
  // Read the PIR sensor
  PIR_reading = digitalRead(PIR_PIN);

  // Read the LDR sensor
  LDR_reading = analogRead(LDR_PIN);


  

  // Read the ultrasonic sensor
  ultrasonic_distance = measureDistance();
  

  // Read the switch
  boolean switchState = digitalRead(SWITCH_PIN);

  // Check if any sensor detects an object or motion
  if (ultrasonic_distance < 200 || PIR_reading == HIGH) {
    // Trigger the alarm
    alarmTriggered = true;
  }


if (LDR_reading < 500) {
    // Turn on the laser module
    digitalWrite(LASER_PIN, HIGH);

    // Turn on the buzzer
    digitalWrite(BUZZER_PIN, HIGH);

    // Display alarm message on LCD
    lcd.clear();
    lcd.print("Alarm Triggered!");
  }



   // Check if the LDR sensor detects a change in light conditions
  

  // If the alarm is triggered
  


  // If the alarm is triggered and not stopped
  if (alarmTriggered && !alarmStopped) {
    // Turn on the buzzer
    digitalWrite(BUZZER_PIN, HIGH);

    // Display alarm message on LCD
    lcd.clear();
    lcd.print("Alarm Triggered!");

    // Show the sensor name that triggered the alarm on LCD
    if (ultrasonic_distance < 200) {
      lcd.print("\nUltrasonic Sensor");
    } else if (PIR_reading == HIGH) {
      lcd.print("\nPIR Sensor");
    } else if (LDR_reading < 500) {
      lcd.print("\nLDR Sensor");
    }

    // Show warning message that someone enters on LCD
    lcd.print("\nSomeone Enters!");
  }

  // Otherwise, turn off the buzzer
  else {
    digitalWrite(BUZZER_PIN, LOW);
  }
  

  // Check if the switch is pressed
  if (switchState == LOW) {
    // Stop the alarm
    alarmStopped = true;
  }

  // If the alarm is stopped
  if (alarmStopped) {
    // Clear the LCD display
    lcd.clear();

    // Display message that the alarm is stopped

  }
}
// Measures the distance to an object using the ultrasonic sensor
long measureDistance() {
  // Set the TRIG pin HIGH for 10 microseconds
  digitalWrite(ULTRASONIC_TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(ULTRASONIC_TRIG_PIN, LOW);

  // Measure the time it takes for the echo pulse to return
  long pulseDuration = pulseIn(ULTRASONIC_ECHO_PIN, HIGH);

  // Calculate the distance to the object
  long distance = pulseDuration / 58.2;

  return distance;
}


```
