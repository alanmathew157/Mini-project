A power generating floor system utilizes piezoelectric sensors embedded within its structure to harness energy from mechanical stress caused by foot traffic. When people walk or move on the floor, the pressure exerted on the piezoelectric sensors generates electricity. This harvested energy can be stored in a battery or used directly to power low-power electronic devices.
![power generating floor structure](https://github.com/user-attachments/assets/e78d3edc-688e-4d05-b167-952d8742e225)


https://github.com/user-attachments/assets/ac97cd3e-5343-4904-8369-bec2b914fe3b



https://github.com/user-attachments/assets/30112662-7d7e-4ddb-95c4-a28f0eb8a658


Code:
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 4);

#define Sensor A0
float vOUT = 0.0;
float vIN = 0.0;
float R1 = 30000.0;
float R2 = 7500.0;

void setup() {
  Serial.begin(9600);
  lcd.init();
  lcd.backlight();
}

void loop() {
  int value = analogRead(Sensor);
  vOUT = (value * 5.0) / 1024.0;
  vIN = vOUT / (R2 / (R1 + R2));

  lcd.setCursor(0, 0);
  lcd.print("Voltage :");
  lcd.print(vIN);
  lcd.print("v ");
  Serial.print("Voltage : ");
  Serial.println(vIN);
}
