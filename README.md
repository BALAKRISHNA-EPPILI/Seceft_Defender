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

[1] Security of Bank lockers after bank closes.

[2] Security of different company's labs /company's equipments and important documents .

[3] Security of jewelleries shop after shop closes .


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

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/046b2313-33cb-45a9-af8e-c777a5c17e72"></br>
   
</p>

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/b14cc230-7755-43f8-9a0c-701228b05882"></br>
   
</p>

## Software Used

- Arduino IDE Open Source Software
- C code

### Connections Diagram of the Product with VSDQuadron Board (Riscduino Board)

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/94f7f43c-b06f-4c3f-88a9-12533b216c5b"></br>
    
</p>


</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/30e13df8-1173-4846-9292-27b063ea116c"></br>
    
</p>


# Flowchart of the Product

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/a68e0f4d-26b8-4a70-89ad-2533c4a554ca"></br>
    
</p>


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


# Complied Code snapshot with Arduino UNO in Arduino IDE

The Compiled Code snapshot by selecting Arduino UNO Board in Arduino IDE is attached below:-

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/21fd9528-0a96-4ae7-972d-40b5e5bd5814"></br>
  
</p>

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/6eb72253-0bbc-4e08-8971-8eafab59f3ad"></br>
  
</p>


## Error-free Compilation Log File with Arduino UNO

```

C:\Program Files (x86)\Arduino\arduino-builder -dump-prefs -logger=machine -hardware C:\Program Files (x86)\Arduino\hardware -hardware C:\Users\vansh\AppData\Local\Arduino15\packages -tools C:\Program Files (x86)\Arduino\tools-builder -tools C:\Program Files (x86)\Arduino\hardware\tools\avr -tools C:\Users\vansh\AppData\Local\Arduino15\packages -built-in-libraries C:\Program Files (x86)\Arduino\libraries -libraries C:\Users\vansh\OneDrive\Documents\Arduino\libraries -fqbn=arduino:avr:uno -ide-version=10819 -build-path C:\Users\vansh\AppData\Local\Temp\arduino_build_90630 -warnings=all -build-cache C:\Users\vansh\AppData\Local\Temp\arduino_cache_111036 -prefs=build.warn_data_percentage=75 -prefs=runtime.tools.arduinoOTA.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -prefs=runtime.tools.arduinoOTA-1.3.0.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -prefs=runtime.tools.avr-gcc.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -prefs=runtime.tools.avr-gcc-7.3.0-atmel3.6.1-arduino7.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -prefs=runtime.tools.avrdude.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -prefs=runtime.tools.avrdude-6.3.0-arduino17.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -verbose C:\Users\vansh\OneDrive\Documents\Arduino\Seceft_Defender_idea_code\Seceft_Defender_idea_code.ino
C:\Program Files (x86)\Arduino\arduino-builder -compile -logger=machine -hardware C:\Program Files (x86)\Arduino\hardware -hardware C:\Users\vansh\AppData\Local\Arduino15\packages -tools C:\Program Files (x86)\Arduino\tools-builder -tools C:\Program Files (x86)\Arduino\hardware\tools\avr -tools C:\Users\vansh\AppData\Local\Arduino15\packages -built-in-libraries C:\Program Files (x86)\Arduino\libraries -libraries C:\Users\vansh\OneDrive\Documents\Arduino\libraries -fqbn=arduino:avr:uno -ide-version=10819 -build-path C:\Users\vansh\AppData\Local\Temp\arduino_build_90630 -warnings=all -build-cache C:\Users\vansh\AppData\Local\Temp\arduino_cache_111036 -prefs=build.warn_data_percentage=75 -prefs=runtime.tools.arduinoOTA.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -prefs=runtime.tools.arduinoOTA-1.3.0.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -prefs=runtime.tools.avr-gcc.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -prefs=runtime.tools.avr-gcc-7.3.0-atmel3.6.1-arduino7.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -prefs=runtime.tools.avrdude.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -prefs=runtime.tools.avrdude-6.3.0-arduino17.path=C:\Program Files (x86)\Arduino\hardware\tools\avr -verbose C:\Users\vansh\OneDrive\Documents\Arduino\Seceft_Defender_idea_code\Seceft_Defender_idea_code.ino
Using board 'uno' from platform in folder: C:\Program Files (x86)\Arduino\hardware\arduino\avr
Using core 'arduino' from platform in folder: C:\Program Files (x86)\Arduino\hardware\arduino\avr
Detecting libraries used...
"C:\\Program Files (x86)\\Arduino\\hardware\\tools\\avr/bin/avr-g++" -c -g -Os -w -std=gnu++11 -fpermissive -fno-exceptions -ffunction-sections -fdata-sections -fno-threadsafe-statics -Wno-error=narrowing -flto -w -x c++ -E -CC -mmcu=atmega328p -DF_CPU=16000000L -DARDUINO=10819 -DARDUINO_AVR_UNO -DARDUINO_ARCH_AVR "-IC:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\cores\\arduino" "-IC:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\variants\\standard" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630\\sketch\\Seceft_Defender_idea_code.ino.cpp" -o nul
Alternatives for LiquidCrystal.h: [LiquidCrystal@1.0.7]
ResolveLibrary(LiquidCrystal.h)
  -> candidates: [LiquidCrystal@1.0.7]
"C:\\Program Files (x86)\\Arduino\\hardware\\tools\\avr/bin/avr-g++" -c -g -Os -w -std=gnu++11 -fpermissive -fno-exceptions -ffunction-sections -fdata-sections -fno-threadsafe-statics -Wno-error=narrowing -flto -w -x c++ -E -CC -mmcu=atmega328p -DF_CPU=16000000L -DARDUINO=10819 -DARDUINO_AVR_UNO -DARDUINO_ARCH_AVR "-IC:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\cores\\arduino" "-IC:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\variants\\standard" "-IC:\\Program Files (x86)\\Arduino\\libraries\\LiquidCrystal\\src" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630\\sketch\\Seceft_Defender_idea_code.ino.cpp" -o nul
Using cached library dependencies for file: C:\Program Files (x86)\Arduino\libraries\LiquidCrystal\src\LiquidCrystal.cpp
Generating function prototypes...
"C:\\Program Files (x86)\\Arduino\\hardware\\tools\\avr/bin/avr-g++" -c -g -Os -w -std=gnu++11 -fpermissive -fno-exceptions -ffunction-sections -fdata-sections -fno-threadsafe-statics -Wno-error=narrowing -flto -w -x c++ -E -CC -mmcu=atmega328p -DF_CPU=16000000L -DARDUINO=10819 -DARDUINO_AVR_UNO -DARDUINO_ARCH_AVR "-IC:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\cores\\arduino" "-IC:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\variants\\standard" "-IC:\\Program Files (x86)\\Arduino\\libraries\\LiquidCrystal\\src" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630\\sketch\\Seceft_Defender_idea_code.ino.cpp" -o "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630\\preproc\\ctags_target_for_gcc_minus_e.cpp"
"C:\\Program Files (x86)\\Arduino\\tools-builder\\ctags\\5.8-arduino11/ctags" -u --language-force=c++ -f - --c++-kinds=svpf --fields=KSTtzns --line-directives "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630\\preproc\\ctags_target_for_gcc_minus_e.cpp"
Compiling sketch...
"C:\\Program Files (x86)\\Arduino\\hardware\\tools\\avr/bin/avr-g++" -c -g -Os -Wall -Wextra -std=gnu++11 -fpermissive -fno-exceptions -ffunction-sections -fdata-sections -fno-threadsafe-statics -Wno-error=narrowing -MMD -flto -mmcu=atmega328p -DF_CPU=16000000L -DARDUINO=10819 -DARDUINO_AVR_UNO -DARDUINO_ARCH_AVR "-IC:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\cores\\arduino" "-IC:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\variants\\standard" "-IC:\\Program Files (x86)\\Arduino\\libraries\\LiquidCrystal\\src" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630\\sketch\\Seceft_Defender_idea_code.ino.cpp" -o "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630\\sketch\\Seceft_Defender_idea_code.ino.cpp.o"
Compiling libraries...
Compiling library "LiquidCrystal"
Using previously compiled file: C:\Users\vansh\AppData\Local\Temp\arduino_build_90630\libraries\LiquidCrystal\LiquidCrystal.cpp.o
Compiling core...
Using precompiled core: C:\Users\vansh\AppData\Local\Temp\arduino_cache_111036\core\core_arduino_avr_uno_0c812875ac70eb4a9b385d8fb077f54c.a
Linking everything together...
"C:\\Program Files (x86)\\Arduino\\hardware\\tools\\avr/bin/avr-gcc" -Wall -Wextra -Os -g -flto -fuse-linker-plugin -Wl,--gc-sections -mmcu=atmega328p -o "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630/Seceft_Defender_idea_code.ino.elf" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630\\sketch\\Seceft_Defender_idea_code.ino.cpp.o" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630\\libraries\\LiquidCrystal\\LiquidCrystal.cpp.o" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630/..\\arduino_cache_111036\\core\\core_arduino_avr_uno_0c812875ac70eb4a9b385d8fb077f54c.a" "-LC:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630" -lm
"C:\\Program Files (x86)\\Arduino\\hardware\\tools\\avr/bin/avr-objcopy" -O ihex -j .eeprom --set-section-flags=.eeprom=alloc,load --no-change-warnings --change-section-lma .eeprom=0 "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630/Seceft_Defender_idea_code.ino.elf" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630/Seceft_Defender_idea_code.ino.eep"
"C:\\Program Files (x86)\\Arduino\\hardware\\tools\\avr/bin/avr-objcopy" -O ihex -R .eeprom "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630/Seceft_Defender_idea_code.ino.elf" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630/Seceft_Defender_idea_code.ino.hex"
Using library LiquidCrystal at version 1.0.7 in folder: C:\Program Files (x86)\Arduino\libraries\LiquidCrystal
"C:\\Program Files (x86)\\Arduino\\hardware\\tools\\avr/bin/avr-size" -A "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_90630/Seceft_Defender_idea_code.ino.elf"
Sketch uses 3224 bytes (9%) of program storage space. Maximum is 32256 bytes.
Global variables use 155 bytes (7%) of dynamic memory, leaving 1893 bytes for local variables. Maximum is 2048 bytes.

```


# Complied Code snapshot with VSDQUADRON Board (RISCDUINO Board) in Arduino IDE

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/7caeec9c-160e-4456-9af2-dd0fa26ac338"></br>
  
</p>


</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/2c65be60-3632-44bf-9239-ba7b85ef09fd"></br>
  
</p>



## Error-free Compilation Log File with VSDQUADRON Board (RISCDUINO Board)

```

C:\Program Files (x86)\Arduino\arduino-builder -dump-prefs -logger=machine -hardware C:\Program Files (x86)\Arduino\hardware -hardware C:\Users\vansh\AppData\Local\Arduino15\packages -tools C:\Program Files (x86)\Arduino\tools-builder -tools C:\Program Files (x86)\Arduino\hardware\tools\avr -tools C:\Users\vansh\AppData\Local\Arduino15\packages -built-in-libraries C:\Program Files (x86)\Arduino\libraries -libraries C:\Users\vansh\OneDrive\Documents\Arduino\libraries -fqbn=riscduino:riscv:uno:toolsloc=default -ide-version=10819 -build-path C:\Users\vansh\AppData\Local\Temp\arduino_build_606716 -warnings=all -build-cache C:\Users\vansh\AppData\Local\Temp\arduino_cache_111036 -prefs=build.warn_data_percentage=75 -prefs=runtime.tools.riscv64-unknown-elf-gcc.path=C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\tools\riscv64-unknown-elf-gcc\1.0.1 -prefs=runtime.tools.riscv64-unknown-elf-gcc-1.0.1.path=C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\tools\riscv64-unknown-elf-gcc\1.0.1 -prefs=runtime.tools.rdnodude.path=C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\tools\rdnodude\0.0.6 -prefs=runtime.tools.rdnodude-0.0.6.path=C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\tools\rdnodude\0.0.6 -verbose C:\Users\vansh\AppData\Local\Temp\arduino_modified_sketch_760446\sketch_sep29d.ino
C:\Program Files (x86)\Arduino\arduino-builder -compile -logger=machine -hardware C:\Program Files (x86)\Arduino\hardware -hardware C:\Users\vansh\AppData\Local\Arduino15\packages -tools C:\Program Files (x86)\Arduino\tools-builder -tools C:\Program Files (x86)\Arduino\hardware\tools\avr -tools C:\Users\vansh\AppData\Local\Arduino15\packages -built-in-libraries C:\Program Files (x86)\Arduino\libraries -libraries C:\Users\vansh\OneDrive\Documents\Arduino\libraries -fqbn=riscduino:riscv:uno:toolsloc=default -ide-version=10819 -build-path C:\Users\vansh\AppData\Local\Temp\arduino_build_606716 -warnings=all -build-cache C:\Users\vansh\AppData\Local\Temp\arduino_cache_111036 -prefs=build.warn_data_percentage=75 -prefs=runtime.tools.riscv64-unknown-elf-gcc.path=C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\tools\riscv64-unknown-elf-gcc\1.0.1 -prefs=runtime.tools.riscv64-unknown-elf-gcc-1.0.1.path=C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\tools\riscv64-unknown-elf-gcc\1.0.1 -prefs=runtime.tools.rdnodude.path=C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\tools\rdnodude\0.0.6 -prefs=runtime.tools.rdnodude-0.0.6.path=C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\tools\rdnodude\0.0.6 -verbose C:\Users\vansh\AppData\Local\Temp\arduino_modified_sketch_760446\sketch_sep29d.ino
Using board 'uno' from platform in folder: C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\hardware\riscv\1.2.8
Using core 'riscduino' from platform in folder: C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\hardware\riscv\1.2.8
Detecting libraries used...
"C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/bin/riscv64-unknown-elf-g++" -c -O2 -march=rv32imc -mabi=ilp32 -fpeel-loops -ffreestanding -ffunction-sections -fdata-sections -fpermissive -Wall -fno-rtti -fno-exceptions "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\system/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/drivers" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/uncache" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/riscv64-unknown-elf/include/c++/10.2.0/riscv64-unknown-elf/rv32imc/ilp32" -include sys/cdefs.h -g -w -x c++ -E -CC -DRISCDUINO_SOC=62023 -DARDUINO=10819 -DF_CPU=10000000LL -DRISCDUINO_UNO "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\cores\\riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\variants\\standard" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716\\sketch\\sketch_sep29d.ino.cpp" -o nul
Alternatives for LiquidCrystal.h: [LiquidCrystal@1.0.7 LiquidCrystal@1.0.7]
ResolveLibrary(LiquidCrystal.h)
  -> candidates: [LiquidCrystal@1.0.7 LiquidCrystal@1.0.7]
"C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/bin/riscv64-unknown-elf-g++" -c -O2 -march=rv32imc -mabi=ilp32 -fpeel-loops -ffreestanding -ffunction-sections -fdata-sections -fpermissive -Wall -fno-rtti -fno-exceptions "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\system/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/drivers" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/uncache" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/riscv64-unknown-elf/include/c++/10.2.0/riscv64-unknown-elf/rv32imc/ilp32" -include sys/cdefs.h -g -w -x c++ -E -CC -DRISCDUINO_SOC=62023 -DARDUINO=10819 -DF_CPU=10000000LL -DRISCDUINO_UNO "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\cores\\riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\variants\\standard" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\libraries\\LiquidCrystal\\src" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716\\sketch\\sketch_sep29d.ino.cpp" -o nul
"C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/bin/riscv64-unknown-elf-g++" -c -O2 -march=rv32imc -mabi=ilp32 -fpeel-loops -ffreestanding -ffunction-sections -fdata-sections -fpermissive -Wall -fno-rtti -fno-exceptions "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\system/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/drivers" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/uncache" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/riscv64-unknown-elf/include/c++/10.2.0/riscv64-unknown-elf/rv32imc/ilp32" -include sys/cdefs.h -g -w -x c++ -E -CC -DRISCDUINO_SOC=62023 -DARDUINO=10819 -DF_CPU=10000000LL -DRISCDUINO_UNO "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\cores\\riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\variants\\standard" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\libraries\\LiquidCrystal\\src" "C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\libraries\\LiquidCrystal\\src\\LiquidCrystal.cpp" -o nul
Generating function prototypes...
"C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/bin/riscv64-unknown-elf-g++" -c -O2 -march=rv32imc -mabi=ilp32 -fpeel-loops -ffreestanding -ffunction-sections -fdata-sections -fpermissive -Wall -fno-rtti -fno-exceptions "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\system/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/drivers" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/uncache" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/riscv64-unknown-elf/include/c++/10.2.0/riscv64-unknown-elf/rv32imc/ilp32" -include sys/cdefs.h -g -w -x c++ -E -CC -DRISCDUINO_SOC=62023 -DARDUINO=10819 -DF_CPU=10000000LL -DRISCDUINO_UNO "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\cores\\riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\variants\\standard" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\libraries\\LiquidCrystal\\src" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716\\sketch\\sketch_sep29d.ino.cpp" -o "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716\\preproc\\ctags_target_for_gcc_minus_e.cpp"
"C:\\Program Files (x86)\\Arduino\\tools-builder\\ctags\\5.8-arduino11/ctags" -u --language-force=c++ -f - --c++-kinds=svpf --fields=KSTtzns --line-directives "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716\\preproc\\ctags_target_for_gcc_minus_e.cpp"
Compiling sketch...
"C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/bin/riscv64-unknown-elf-g++" -c -O2 -march=rv32imc -mabi=ilp32 -fpeel-loops -ffreestanding -ffunction-sections -fdata-sections -fpermissive -Wall -fno-rtti -fno-exceptions "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\system/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/drivers" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/uncache" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/riscv64-unknown-elf/include/c++/10.2.0/riscv64-unknown-elf/rv32imc/ilp32" -include sys/cdefs.h -g -DRISCDUINO_SOC=62023 -DARDUINO=10819 -DF_CPU=10000000LL -DRISCDUINO_UNO "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\cores\\riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\variants\\standard" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\libraries\\LiquidCrystal\\src" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716\\sketch\\sketch_sep29d.ino.cpp" -o "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716\\sketch\\sketch_sep29d.ino.cpp.o"
Compiling libraries...
Compiling library "LiquidCrystal"
"C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/bin/riscv64-unknown-elf-g++" -c -O2 -march=rv32imc -mabi=ilp32 -fpeel-loops -ffreestanding -ffunction-sections -fdata-sections -fpermissive -Wall -fno-rtti -fno-exceptions "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\system/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/include" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/drivers" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/uncache" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/riscv64-unknown-elf/include/c++/10.2.0/riscv64-unknown-elf/rv32imc/ilp32" -include sys/cdefs.h -g -DRISCDUINO_SOC=62023 -DARDUINO=10819 -DF_CPU=10000000LL -DRISCDUINO_UNO "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\cores\\riscduino" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\variants\\standard" "-IC:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\libraries\\LiquidCrystal\\src" "C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8\\libraries\\LiquidCrystal\\src\\LiquidCrystal.cpp" -o "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716\\libraries\\LiquidCrystal\\LiquidCrystal.cpp.o"
Compiling core...
Using precompiled core: C:\Users\vansh\AppData\Local\Temp\arduino_cache_111036\core\core_riscduino_riscv_uno_toolsloc_default_ef39785d817fd5facac5184af4faeadd.a
Linking everything together...
"C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/bin/riscv64-unknown-elf-g++" -march=rv32imc -mabi=ilp32 -T "C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\hardware\\riscv\\1.2.8/sdk/bsp/env/uncache/link.lds" -nostartfiles -Wl,-N -Wl,--gc-sections -Wl,--wrap=malloc -Wl,--wrap=free -Wl,--wrap=sbrk "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716\\sketch\\sketch_sep29d.ino.cpp.o" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716\\libraries\\LiquidCrystal\\LiquidCrystal.cpp.o" -nostdlib -Wl,--start-group "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_cache_111036\\core\\core_riscduino_riscv_uno_toolsloc_default_ef39785d817fd5facac5184af4faeadd.a" -lm -lstdc++ -lc -lgloss -Wl,--end-group -lgcc -o "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716/sketch_sep29d.ino.elf"
"C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/bin/riscv64-unknown-elf-objcopy" -R .rel.dyn -O binary "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716/sketch_sep29d.ino.elf" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716/sketch_sep29d.ino.bin"
"C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/bin/riscv64-unknown-elf-objcopy" -R .rel.dyn -O verilog "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716/sketch_sep29d.ino.elf" "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716/sketch_sep29d.ino.hex"
Multiple libraries were found for "LiquidCrystal.h"
 Used: C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\hardware\riscv\1.2.8\libraries\LiquidCrystal
 Not used: C:\Program Files (x86)\Arduino\libraries\LiquidCrystal
Using library LiquidCrystal at version 1.0.7 in folder: C:\Users\vansh\AppData\Local\Arduino15\packages\riscduino\hardware\riscv\1.2.8\libraries\LiquidCrystal
"C:\\Users\\vansh\\AppData\\Local\\Arduino15\\packages\\riscduino\\tools\\riscv64-unknown-elf-gcc\\1.0.1/bin/riscv64-unknown-elf-size" -B "C:\\Users\\vansh\\AppData\\Local\\Temp\\arduino_build_606716/sketch_sep29d.ino.elf"
Sketch uses 11788 bytes (0%) of program storage space. Maximum is 8388608 bytes.

```

# Working

The working of this product is in such a way that whenever any person enters or Any thief enters into this protected area then, if in case he/she will crosses the set distance of ultrasonic sensor then, it ultrasonic sensor detects that and alarm triggers and if in any case/situation someone crosses the or escapes the ultrasonic sensor distance without any alarm triggers then, there is PIR sensor also there, which detects the motion with the help of heat and hence it detects that person motion and alarm triggers ,in this case also ,on LCD display it shows that someone enters and which sensor causes the alarm to trigger so, one came to know about it .
After that if in any case/situation ,someone's escapes from ultrasonic sensor or PIR sensor then, there is highly protected laser technology established there, that escaping from this technology is not so much easy so, as soon as that person goes further , as LDR sensor detects  the light on which laser module depend so, when one interrupts in between the laser light then, it causes the alarm to trigger and messages goes over the LCD display .
And it alerts outside the about the thieve or something unusual is happening inside that area so, other people or that area guard come and cross check that .

There , is also a switch connected there , using which one can stop the alarm in case ,If the guard or some dedicated or assigned person enters just to check kr roam once in a place and alarm triggers so,at that time he/she can press the switch button and the alarm stops .
But ,this switch is not be known by every person ,it only knows to guard or employee who are taking care of that area .


# Advantages 

1. More secure 
2. Having multiple flexibility of security .
3. There is a backup option available as ,if in any cases one sensor become fails or disabled ,then other is present there to work , it detects and work accordingly .
So, in such a way we can have the multiple backup system in a single product


# Rough sketch of Final Product 

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/5ada858b-01f4-413e-a900-357822129025"></br>
   
</p>




# Future Scope

This product  have several future scope ,these are :-

1) We can also connect this app with GSM module , which can directly send normal message over the phone for these unnecessary types of situations ,one can be notified on urgent basis and on time .

2) In future, we can connect this product with the Bluetooth or wifi  or with gsm module so, that we can make its app and this message directly goes to the app .
The message which it's displaying on LCD now.


So, if in case suppose it's a building and guard is only sitting at the bottom of the building then, in such mishappening of situation one can be notified and he/she can rush in hurry and check in that area ,which ensures you more safety .

3) With the help of AI technology we can add camera there also, and get access of that camera which wil be connected to our app directly and we can monitor everything on our phone .


But for implementing these future scopes ,the cost of the product may increase as per the requirements and some additional components will be added in the product .

As, these are the future scope so, we can check or update it in future as per the requirement of market or availability of this much advanced product in the market .


# Team Details
- Team Name: Secure Vision

</p>
<p align="center">
  <img src="https://github.com/BALAKRISHNA-EPPILI/Seceft_Defender/assets/88899069/02a2ba47-c11c-4cff-88be-a0d781bad792"></br>
   
</p>

- Vanshika Tanwar, 
  
Course- B.tech (Electronics and Communication Engineering)

  Institute- Dronacharya Group Of Institution, Greater Noida (affiliated to AKTU)

  Role in this product - Handling Hardware Connections and pin out with VSDQuadron Board.



- E Balakrishna, 

  Course- B.tech (Electronics and Communication Engineering)

  Institute- Dronacharya Group Of Institution, Greater Noida (affiliated to AKTU)

  Role in this product - Handling Software part Arduino IDE coding of the product 



# References 

## For Laser

[1]. https://techatronic.com/how-to-make-a-laser-security-alarm/ ( code) 

[2]. https://rees52.com/make-a-security-system-using-laser-and-ldr-module-kt616-2794-projects-kits/ (code)

[3]. https://www.youtube.com/watch?v=jxxY9uTAD6I


[4]. https://www.hackster.io/Techatronic/how-to-make-a-laser-security-alarm-using-arduino-4b851a#:~:text=Connect%20the%20220%20Ohm%20resistor,2%20on%20the%20Arduino%20board.

## Code

[1]. https://www.youtube.com/watch?v=alQ9v8dyaTs

[2]. https://www.youtube.com/watch?v=Q8B4f0y1UCI 

[3]. https://www.youtube.com/watch?v=Q8B4f0y1UCI 

[4]. https://drive.google.com/drive/folders/1MCopaGDJfGTQ13RYMycoDNMVMuGshYor 

[5].https://lpulaguna.edu.ph/wp-content/uploads/2019/10/2.-Design-and-Implementation-of-an-Arduino-Based-Security-System-Using-Laser-Light.pdf 


## PIR SENSOR 

[1]. https://studytronics.weebly.com/uploads/4/4/3/7/44372217/home_security_alarm_system_using_arduino_project_report.pdf 

[2]. https://www.hackster.io/roshan-baig/security-system-using-pir-sensor-d713a5 


[3]. https://airccse.com/eeij/papers/4317eeij01.pdf (ALL)

# Acknowledgements:

- [Kunal Ghosh](https://github.com/kunalg123), Founder, VSD Corp. Pvt. Ltd
- [VLSI System Design (VSD) Corp. Pvt. Ltd India](https://www.vlsisystemdesign.com/)




# Author
• Vanshika Tanwar, B.Tech(ECE), Dronacharya Group of Institutions, Greater Nodia, Uttar Pradesh.

• E Balakrishna, B.Tech(ECE), Dronacharya Group of Institutions, Greater Nodia, Uttar Pradesh.
