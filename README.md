# Arduino--sensor-monitoring
Arduino based analog sensor data monitoring using serial monitor and LED indication
int sensorValue;
int energyValue;
int ledPin = 13;

void setup() {
  Serial.begin(9600);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  sensorValue = analogRead(A0);
  energyValue = 1023 - sensorValue;  // reverse mapping

  Serial.print("Energy Value: ");
  Serial.println(energyValue);

  if (energyValue > 500) {  
    // Normal light
    Serial.println("HIGH Energy");
    digitalWrite(ledPin, HIGH);
  }
  else if (energyValue > 200) {
    Serial.println("MEDIUM Energy");
    digitalWrite(ledPin, HIGH);
    delay(200);
    digitalWrite(ledPin, LOW);
  }
  else {
    // Kai cover / dark
    Serial.println("LOW Energy");
    digitalWrite(ledPin, LOW);
  }

  delay(500);
}
