
#include <LiquidCrystal.h>

LiquidCrystal lcd(12,11,5,4,3,2);
const int soundPin = 0;
const int sec = 450;

int sound;
int scale;


void setup()
{
  lcd.begin(16, 2);
  lcd.clear();
  lcd.print("Sound Sensor");
  pinMode(7,OUTPUT);
  pinMode(8,OUTPUT);
  pinMode(9,OUTPUT);
}

void loop()
{
   sound = analogRead(soundPin);
   scale = map(sound, 0, 255, 0, 100);
   
   lcd.setCursor(0,1);
   lcd.print("sound:");
   lcd.setCursor(6,1);
   lcd.print(scale);
   lcd.print(" ");
   delay(sec);
  
  if(scale<20) {
   digitalWrite(7, HIGH);
   digitalWrite(8, LOW);
   digitalWrite(9, LOW);
    delay(sec);
   digitalWrite(7, LOW);
   digitalWrite(8, HIGH);
   digitalWrite(9, LOW);
    delay(sec);
   digitalWrite(7, LOW);
   digitalWrite(8, LOW);
   digitalWrite(9, HIGH);
   lcd.setCursor(0,6);
   lcd.print("Level 1 ");
   delay(sec);
    }
    else if (scale<30){ 
   digitalWrite(7, HIGH);
   digitalWrite(8, HIGH);
   digitalWrite(9, LOW);
    delay(sec);
   digitalWrite(7, LOW);
   digitalWrite(8, LOW);
   digitalWrite(9, HIGH);
    delay(sec);
   digitalWrite(7, HIGH);
   digitalWrite(8, HIGH);
   digitalWrite(9, LOW);   
   lcd.setCursor(0,6);
   lcd.print("Level 2 ");
   delay(sec);
   
   }else {
   digitalWrite(7, HIGH);
   digitalWrite(8, LOW);
   digitalWrite(9, HIGH);
    delay(sec);
   digitalWrite(7, LOW);
   digitalWrite(8, HIGH);
   digitalWrite(9, LOW);
    delay(sec);
   digitalWrite(7, HIGH);
   digitalWrite(8, LOW);
   digitalWrite(9, HIGH); 
   lcd.setCursor(0,6);
   lcd.print("Level 3 ");
   delay(sec);
   
   }
  
}
   
