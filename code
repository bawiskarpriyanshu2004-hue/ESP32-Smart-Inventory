#define BLYNK_TEMPLATE_ID "TMPL3s8gREmS1"
#define BLYNK_TEMPLATE_NAME "Smart Inventory"
#define BLYNK_AUTH_TOKEN "IZ_Q7xBLbpyCC_C7vGm_yk9sijUPof59"

#include <WiFi.h>
#include <BlynkSimpleEsp32.h>
#include <LiquidCrystal_I2C.h>

// Pins
const int trigPin = 5;
const int echoPin = 18;
const int potPin = 34;
const int buzzer = 2;

LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzer, OUTPUT);
  
  lcd.init();
  lcd.backlight();
  
  // Wokwi uses a special "Virtual WiFi"
  Blynk.begin(BLYNK_AUTH_TOKEN, "Wokwi-GUEST", "");
}

void loop() {
  Blynk.run();
  
  // 1. Measure Distance (Stock Height)
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  long duration = pulseIn(echoPin, HIGH);
  int distance = duration * 0.034 / 2;
  int stockPercent = map(distance, 2, 40, 100, 0); // Adjust based on bin size

  // 2. Measure Simulated Weight
  int weight = analogRead(potPin);

  // 3. Low Stock Alert
  if (stockPercent < 20) {
    digitalWrite(buzzer, HIGH);
    lcd.setCursor(0, 1);
    lcd.print("LOW STOCK!      ");
  } else {
    digitalWrite(buzzer, LOW);
  }

  // 4. Update Blynk and LCD
  Blynk.virtualWrite(V1, stockPercent);
  Blynk.virtualWrite(V2, weight);
  
  lcd.setCursor(0, 0);
  lcd.print("Stock: ");
  lcd.print(stockPercent);
  lcd.print("%   ");
  
  delay(1000); // 1-second update interval
}
