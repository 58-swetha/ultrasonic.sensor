# ultrasonic.sensor
#include <LiquidCrystal.h>
LiquidCrystal lcd(7,6,5,4,3,2);
const int trigPin=11;
const int echoPin=10;
const int led=13;
void setup() 
{
 pinMode(trigPin,OUTPUT);
 pinMode(echoPin,INPUT);
 pinMode(led,OUTPUT);
 lcd.begin(16,2);
 lcd.setCursor(0,1);
 lcd.print ("ULTRASONIC RANGE FINDER");
 delay (2000);
 
}   
long duration, r;
float distance;
void loop()
{
 lcd.clear();
 lcd.print("Distance in cm");
 digitalWrite(trigPin, LOW);
 delayMicroseconds(2);
 digitalWrite(trigPin, HIGH);
 delayMicroseconds(10);
 digitalWrite(trigPin,LOW);
 duration=pulseIn(echoPin,HIGH);
 long r=3.4*duration/2; 
 float distance=r/100;
 lcd.setCursor(0,1);
 lcd.print(distance);
 delay (100);
 if(distance<10)
 {
 digitalWrite(led,HIGH);
 }
else
 {
 digitalWrite(led,LOW);
 }
    }
