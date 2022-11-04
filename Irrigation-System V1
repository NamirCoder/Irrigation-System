#include <DHT.h>;

//Rain Sensor
const int capteur_D = 4;
const int capteur_A = A1;
int val_analogique;
const int LEDR = 5;

//Soil Moisture
int SMLED = 13;
int sensorPin = A0;
int sensorValue;
int limit = 300;

//DHT22
#define DHTPIN 7
#define DHTTYPE DHT22
DHT dht(DHTPIN, DHTTYPE);

//DHT22 Variables
int chk;
float hum;
float temp;

//Pir Motion
int MLED = 10;
int sensor = 2;
int state = LOW;
int val = 0;
int MBuzzer = 11;


void setup() {
  //Rain Sensor Pin Setup
  pinMode(capteur_D, INPUT);
  pinMode(capteur_A, INPUT);
  Serial.begin(9600);

  //Soil Moisture Pin Setup
  Serial.begin(9600);
  pinMode(SMLED, OUTPUT);

  //DHT22 Setup
  Serial.begin(9600);
  dht.begin();

  //Pir Motion Setup
  pinMode(MLED, OUTPUT);
  pinMode(sensor, INPUT);
  pinMode(MBuzzer, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  //Rain Sensor Function Setup
  if (digitalRead(capteur_D) == LOW) {
    Serial.println("Raining : Yes");
    delay(10);
    digitalWrite(LEDR, HIGH);

  } else {
    Serial.println("Raining : No");
    delay(10);
    digitalWrite(LEDR, LOW);
  }
  val_analogique = analogRead(capteur_A);
  Serial.print("Analog value : ");
  Serial.println(val_analogique);
  Serial.println("");
  delay(1000);

  //Soil Moisture Sensor Function Setup
  sensorValue = analogRead(sensorPin);
  Serial.println("Soil Moisture : ");
  Serial.println(sensorValue);

  if (sensorValue < limit) {
    digitalWrite(SMLED, HIGH);
  } else {
    digitalWrite(SMLED, LOW);
  }

  delay(1000);

  // DHT22 Function Setup
  delay(2000);
  //Read data and store it to variables hum and temp
  hum = dht.readHumidity();
  temp = dht.readTemperature();
  //Print temp and humidity values to serial monitor
  Serial.print("Humidity: ");
  Serial.print(hum);
  Serial.print(" %, Temp: ");
  Serial.print(temp);
  Serial.println(" Celsius");
  delay(1000);  //Delay 2 sec.

  //Pir Motion Function Setup
  val = digitalRead(sensor);
  if (val == HIGH) {
    digitalWrite(MLED, HIGH);
    delay(500);

    if (state == LOW) {
      Serial.println("Motion detected!");
      state = HIGH;
    }
  } else {
    digitalWrite(MLED, LOW);
    delay(500);

    if (state == HIGH) {
      Serial.println("Motion stopped!");
      state = LOW;
    }
  }
}
