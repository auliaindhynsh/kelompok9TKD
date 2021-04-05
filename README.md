//kelompok 9
//Nama Anggota : 
//Reka Anggraini
//Aulia Indah Yuanisah
//Ayu Azharia
#include <LiquidCrystal.h>
const int rs = 12, e = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, e, d4, d5, d6, d7);
int temp;
int led = 13;
int sensorpin = A0;
int min_temp = 35;
int max_temp = 55;

void setup() {
  lcd.begin(16, 2);
  pinMode(led, OUTPUT);
}

void loop() {
  temp = analogRead(sensorpin);
  temp = temp * 0.48883;
  if(temp > max_temp) {
    digitalWrite(led, HIGH);
    lcd.print("Pendingin Aktif ");
  }
  
  if(temp < min_temp) {
    digitalWrite(led, LOW);
    lcd.print("Pendingin Mati ");
  }
  
  else {
    lcd.print("Otomatis");
  }
  
  lcd.setCursor(0, 1);
  lcd.print("Suhu: ");
  lcd.print(temp);
  lcd.print("C");
  delay(200);
  lcd.clear();
}
