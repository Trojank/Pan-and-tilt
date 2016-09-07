# Pan-and-tilt
/*
 Controlling a servo position using a potentiometer (variable resistor)
 by Michal Rinott <http://people.interaction-ivrea.it/m.rinott>

 modified on 8 Nov 2013
 by Scott Fitzgerald
 http://www.arduino.cc/en/Tutorial/Knob
*/

#include <Servo.h>

Servo xServo;  // create servo object to control a the X servo
Servo yServo;  // Y servo control

int xpotpin = 0;  // analog pin used to connect the potentiometer
int ypotpin = 1;  

int xVal;    // variable to read the value from the analog pin
int yVal;

void setup() {
  xServo.attach(9);  // attaches the servo on pin 9 to the servo object
  yServo.attach(6);
}

void loop() {
  xVal = analogRead(xpotpin);            // reads the value of the potentiometer (value between 0 and 1023)
  yVal = analogRead(ypotpin);
  xVal = map(xVal, 0, 1023, 0, 180);     // scale it to use it with the servo (value between 0 and 180)
  yVal = map(yVal, 0, 800, 180, 40);
  xServo.write(xVal);                  // sets the servo position according to the scaled value
  delay(1);
  yServo.write(yVal);
  delay(1);                           // waits for the servo to get there
}
