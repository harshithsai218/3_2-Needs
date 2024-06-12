# Ultrasonic Sensor to find out the Distance

```C
#define ECHOPin 5
#define TRIGPin 6
long duration;
int distance;

void setup() {
  pinMode(TRIGPin, OUTPUT);
  pinMode(ECHOPin, INPUT);
  Serial.begin(9600);
  Serial.print("Testing of the Ultrasonic sensor HC-SR04");
  Serial.print("With Arduino UNO R3 board");
}

void loop() {
  digitalWrite(TRIGPin, LOW);
  delayMicroseconds(4);
  digitalWrite(TRIGPin, HIGH);
  delayMicroseconds(15);
  digitalWrite(TRIGPin, LOW);
  duration = pulseIn(ECHOPin, HIGH);
  distance = duration * (0.034/2);
  Serial.print("Distance : ");
  Serial.print(distance);
  Serial.print(" cm");
}
```

# IR Sensor with LED ( Object detection )

```C
int sensorPin = 2;
int outputPin = 13;

void setup(){
  pinMode(sensorPin, INPUT);
  pinMode(outputPin, OUTPUT);
  Serial.begin(9600);
}

void loop(){
  int sensorValue = digitalRead(sensorPin);
  Serial.print("Sensor Value : ");
  Serial.print(sensorValue);
  delay(1000);
  if(sensorValue == LOW){
    digitalWrite(outputPin, HIGH);
  }
  else{
    digitalWrite(outputPin, LOW);
  }
}
```

# Transfer sensor data to smartphone using Bluetooth on Arduino

```C
const int irPin = 13;

void setup(){
  pinMode(irPin, INPUT);
  Serial.begin(9600);
} 

void loop(){
  int value = digitalRead(irPin);
  Serial.print(value);
  if (value == 0){
    Serial.print("Obstacle Detected!");
  }
  else{
    Serial.print("No Obstacle Detected !");
  }
  delay(1000);
}
```

# Week 4(A)

```C
#include <SPI.h>
#include <MFRC522.h>
#define SS_PIN 10
#define RST_PIN A5
MFRC522 rfid(SS_PIN, RST_PIN);
MFRC522 :: MIFARE_Key key;
byte nuidPICC[4];

void setup(){
  Serial.begin(9600);
  SPI.begin();
  rfid.PCD_Init();
  for(byte i=0; i<6; i++){
    key.keyByte[i] = 0xFF;
  }
}

void loop(){
  if(!rfid.PICC_IsNewCardPresent()){
    return;
  }
  if(!rfid.PICC_ReadCardSerial()){
    return;
  }
  for(byte i=0; i<4; i++){
    nuidPICC[i] = rfid.uid.uidByte[i];
  }
  printHex(rfid.uid.uidByte, rfid.uid.size);
  rfid.PICC_HaltA();
  rfid.PCD_StopCrypto1();
}

void printHex(byte *buffer, byte bufferSize){  
  for(byte i=0; i<bufferSize; i++){
    Serial.print(buffer[i] < 0x10 ? "0" : " ");
    Serial.print(buffer[i], HEX);
  }
}
```


# Week 5(A)

```C
#include "DHT.h"
#define DHTTYPE DHT22
#define DHTPIN 2

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  Serial.println(F("DHTxx Test!"));  
  dht.begin();
}

void loop() {
  float h = dht.readHumidity();
  float t = dht.readTemperature();
  float f = dht.readTemperature(true);

  if (isnan(h) || isnan(t) || isnan(f)) {
    Serial.println("Failed to read the data from DHT sensor");
    return;  
  }

  float hif = dht.computeHeatIndex(f, h);
  float hic = dht.computeHeatIndex(t, h, false);

  Serial.print("Humidity : ");
  Serial.print(h);
  Serial.print("% Temperature : ");
  Serial.print(t);
  Serial.print("°C ");
  Serial.print(f);
  Serial.print("°F Heat Index (F): ");
  Serial.print(hif);
  Serial.print("°C");
  Serial.print(hic);
  Serial.println("°F");
  delay(2000);  
}
```
