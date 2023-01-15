# Automated-Solar-Pannel
Academic project
//Single axis solar tracker program

#include <Servo.h> // loads the servo library

Servo myservo; // create servo object to control a servo

int pos = 90; // variable to store the servo position 0-180

int sensorPin = A0; // select the input pin for the potentiometer

int sensorPin2 = A1;

int sensorValue = 0; // variable to store the value coming from the sensor

int sensorValue2 = 0;

int diffval = 0;

int errorval = 15;

void setup()

{

myservo.attach(9); // attaches the servo on pin 9 to the servo object

//Serial.begin(9600); // uncomment if you need to measure outputs with the serial monitor.

}

void loop() {

sensorValue = analogRead(sensorPin);

sensorValue2 = analogRead(sensorPin2);

diffval = sensorValue – sensorValue2;

if (abs(diffval) > errorval) {

if (diffval > 0) {

pos = pos + 5;

}

else {

pos = pos – 5;

}

myservo.write(pos);

delay(100);

}
