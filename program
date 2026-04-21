#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <Servo.h>


// LCD
LiquidCrystal_I2C lcd(0x27, 16, 2);


// Servo
Servo myservo;


// Ultrasonic Pins
const int trigPin1 = 6;
const int echoPin1 = 7;
const int trigPin2 = 8;
const int echoPin2 = 9;


// Parking
int Slot = 4;
int flag1 = 0;
int flag2 = 0;


const int distanceThreshold = 10;


void setup() {
  Serial.begin(9600);


  // LCD
  lcd.init();
  lcd.backlight();


  // Pins
  pinMode(trigPin1, OUTPUT);
  pinMode(echoPin1, INPUT);
  pinMode(trigPin2, OUTPUT);
  pinMode(echoPin2, INPUT);


  // Servo (REVERSED LOGIC)
  myservo.attach(2);
  myservo.write(0); //


  // Welcome
  lcd.setCursor(0, 0);
  lcd.print(" PARKING SYSTEM ");
  lcd.setCursor(0, 1);
  lcd.print("     READY      ");
  delay(2000);
  lcd.clear();
}


// Distance function
long getDistance(int trigPin, int echoPin) {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);


  long duration = pulseIn(echoPin, HIGH);
  return duration * 0.034 / 2;
}


// Smooth servo movement
void smoothServoMove(int startPos, int endPos) {
  int step = (startPos < endPos) ? 1 : -1;
  for (int pos = startPos; pos != endPos; pos += step) {
    myservo.write(pos);
    delay(5);
  }
  myservo.write(endPos);
}


void loop() {


  long distance1 = getDistance(trigPin1, echoPin1);
  long distance2 = getDistance(trigPin2, echoPin2);


  Serial.print("Entry: ");
  Serial.print(distance1);
  Serial.print("  Exit: ");
  Serial.println(distance2);


  // ===== ENTRY =====
  if (distance1 < distanceThreshold && flag1 == 0) {
    Serial.println("Car at ENTRY");


    if (Slot > 0) {
      flag1 = 1;


      smoothServoMove(0, 100);
      Slot--;




      Serial.print("Slots left: ");
      Serial.println(Slot);


    } else {
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print(" PARKING FULL ");
      lcd.setCursor(0, 1);
      lcd.print(" WAIT PLEASE  ");
      delay(2000);
    }
  }


  // ===== EXIT =====
  if (distance2 < distanceThreshold && flag2 == 0) {
    Serial.println("Car at EXIT");


    if (Slot < 4) {
      flag2 = 1;


      smoothServoMove(0, 100); 
      Slot++;


      Serial.print("Slots left: ");
      Serial.println(Slot);
    }
  }


  // ===== CLOSE GATE =====
  if (flag1 == 1 || flag2 == 1) {
    delay(3000); // wait for car
    smoothServoMove(100, 0); // 


    flag1 = 0;
    flag2 = 0;


    Serial.println("Gate closed");
  }


  // Safety
  Slot = constrain(Slot, 0, 4);


  // ===== LCD DISPLAY =====
  lcd.setCursor(0, 0);
  lcd.print("Slots Left: ");
  lcd.print(Slot);
  lcd.print("   ");


  lcd.setCursor(0, 1);
  if (Slot == 0) {
    lcd.print("FULL        ");
  } else {
    lcd.print("AVAILABLE   ");
  }


  delay(500);
}
