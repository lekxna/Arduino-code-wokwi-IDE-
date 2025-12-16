# Arduino-code-wokwi-IDE- my wokwi username is vontlus0_.
i will link the wokwi simulation
so this to me is a series since im gonna use my code and improve my ski.lls in order to make a project 
(my project wil remain a mestery towards until i reveal it idk how i can but yh)
#include <Servo.h>

Servo myServo;
int servopin = 10;
int trigpin = 12;
int echopin = 11;

void setup() {

  myServo.attach(servopin);

  
  pinMode(trigpin, OUTPUT);
  pinMode(echopin, INPUT);

  Serial.begin(9600); 
}

void loop() {


  // --- Ultrasonic measurement ---
  digitalWrite(trigpin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigpin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigpin, LOW);

  long duration = pulseIn(echopin, HIGH);
  int distance = duration / 58;
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
  
  if(distance>30)
  {
 
  myServo.write(0);
  delay(1000);
  myServo.write(90);
  delay(1000);

  for(int i=0; i<90; i++) {
    myServo.write(90 + i);
    delay(15);
  }
  }

  delay(500);
}
