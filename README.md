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
    Serial.println("LOW Energy");
    digitalWrite(ledPin, LOW);
  }
# Arduino Sensor Monitoring

## Problem Statement
To monitor environmental changes using an analog sensor and display variation using Arduino.

## Objective
- Read analog sensor values
- Show variation using LED and Serial Monitor
- Classify values as Low / Medium / High

## Components Used
- Arduino Uno
- Analog Sensor (LDR / similar)
- LED
- Jumper wires

## Working Principle
- Sensor gives analog values to A0
- Arduino processes the value
- LED indicates intensity
- Output is shown in Serial Monitor

## Output
- High value → LED ON
- Low value → LED OFF
- Real-time values displayed
  delay(500);
}
WhatsApp Video 2026-01-23 at 12.42.37 AM
