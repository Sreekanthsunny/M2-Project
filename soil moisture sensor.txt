#include <LiquidCrystal.h>

LiquidCrystal lcd(8,9,4,5,6,7); // lcd hardware interface

int levelUp = 600; // see calibration notes
int levelDown = 300; // see calibration notes

int probeIn = 1; // sensor head input to A1

void setup(){

  lcd.begin(16,2);

  lcd.clear();
}

void loop(){

  String DisplayNote;
 
  int probeValue;
  probeValue = analogRead(probeIn);
  lcd.setCursor(0,1);
  lcd.print("Digi-Soil Meter"); // custom message

  if (probeValue < levelDown){
    String DisplayNote = "Dry, Water Me!";
    lcd.setCursor(1,0);
    lcd.print(DisplayNote);

  } 
  else if (probeValue > levelUp){
    String DisplayNote = "Wet, Leave Me!";
    lcd.setCursor(1,0);
    lcd.print(DisplayNote); 

  } 
  else {
    lcd.setCursor(1,0);
    lcd.print(DisplayNote);
  }
}