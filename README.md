# arduino-serial9bit
1. Open directory "C:\Program Files\Arduino\hardware\arduino\avr\cores\arduino"
2. Backup original files :
  - HardwareSerial.cpp
  - HardwareSerial.h
  - HardwareSerial_private.h
3. Replace with files in HardwareSerial9bit folder

How To Use?
```
/*
  Using arduino mega, because there's more than one serial hardware
  - Serial 0 for debug printing (serial from usb)
  - Serial 2 for serial 9 bit reading (serial from 16, 17 arduino)
*/
void setup (){
  Serial.begin (115200);  // debugging prints
  //Serial1.begin (115200, SERIAL_8N1, true);  // 9 bit mode
  Serial2.begin (9600, SERIAL_8N1, true);  // 9 bit mode
  Serial.println ("--- starting ---");
}

void loop (){
  if (Serial2.available ()){
    Serial.println((int) Serial2.read (), HEX);
  }
}
```
