/*
     GLOBAL SOLUTION - IOT
     MORGANTINI

     @author - Ronaldo Prates - 93601

     
     CÓDIGO:  Q0624
     AUTOR:   BrincandoComIdeias
     LINK:    https://www.youtube.com/brincandocomideias ; https://cursodearduino.net/ ; https://cursoderobotica.net
     COMPRE:  https://www.arducore.com.br/
     SKETCH:  Exemplo LiquidCrystal_I2C
     DATA:    11/02/2020
*/


#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <HCSR04.h>

#define endereco  0x27
#define colunas   16
#define linhas    2

int triggerPinLeft = 5;
int echoPinLeft = 6;

int triggerPinRight = 2;
int echoPinRight = 3;

int initDelay = 5000;
int loopDelay = 10000;

String alertMessage = "Via Interditada...";
String warningMessage = "Via em Atencao...";
String okMessage = "Via liberada.....";

HCSR04 hc1(triggerPinLeft, echoPinLeft); //HCSR04 (trig pin , echo pin);
HCSR04 hc2(triggerPinRight, echoPinRight); //HCSR04 (trig pin , echo pin);

LiquidCrystal_I2C lcd(endereco, colunas, linhas);


void setup() {

  Serial.begin(9600);
  
  lcd.init(); 
  lcd.backlight();
  lcd.clear(); 

  lcd.print("Ronaldo F Prates");
  lcd.setCursor(0, 1);
  lcd.print("RM 93601");

  delay(initDelay);

}

void loop() {
  
  logger();

  int minimumValue = 26;
  int maximumValue = 27;

  bool isRedAlert = hc1.dist() <= minimumValue && hc2.dist() <= minimumValue;
  bool isOrangeAlert = (hc1.dist() > minimumValue && hc2.dist() <= maximumValue);

  
  lcd.clear();

  if(isRedAlert) {

    lcd.print(alertMessage);
    
  }
  else if(isOrangeAlert){

    lcd.print(warningMessage);
    
  }
  
  lcd.print(okMessage);

  delay(loopDelay);

}
  
 void logger(void) {
  Serial.println("DIREITA:: ");
  Serial.println(hc1.dist());

  Serial.println("---------------");

  Serial.println("ESQUERDA:: ");
  Serial.println(hc2.dist());

  Serial.println("---------------");
  Serial.println("---------------");
  Serial.println("---------------");
 
}
