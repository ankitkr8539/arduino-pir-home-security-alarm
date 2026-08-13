# Arduino PIR Home Security Alarm

A simple Arduino-based home security alarm system that detects motion using a PIR sensor and provides visual and audible alerts through an LED and buzzer.

## Project Overview

This project uses an Arduino Uno and an HC-SR501 PIR motion sensor to monitor movement in a specific area. When motion is detected, the Arduino activates an LED and buzzer to provide an immediate alert.

The project demonstrates the fundamentals of sensor interfacing, digital input processing, and output control using Arduino.

## Features

- Real-time motion detection.
- Visual alert using an LED.
- Audible alert using a buzzer.
- Simple and low-cost circuit.
- Beginner-friendly Arduino implementation.
- Serial Monitor status messages.

## Hardware Requirements

- Arduino Uno
- HC-SR501 PIR motion sensor
- LED
- 220-ohm resistor
- Buzzer
- Breadboard
- Jumper wires
- USB cable

## Circuit Connections

| Component | Pin | Arduino Connection |
|---|---|---|
| PIR sensor | VCC | 5V |
| PIR sensor | GND | GND |
| PIR sensor | OUT | Digital pin 2 |
| LED anode | Through 220-ohm resistor | Digital pin 3 |
| LED cathode |  | GND |
| Buzzer positive |  | Digital pin 4 |
| Buzzer negative |  | GND |

## System Operation

1. The PIR sensor monitors the surrounding area.
2. When movement is detected, the sensor sends a HIGH signal to the Arduino.
3. The Arduino turns on the LED.
4. The buzzer produces an audible alarm.
5. When motion stops, the LED and buzzer turn off.

## Arduino Code

```cpp
const int pirPin = 2;
const int ledPin = 3;
const int buzzerPin = 4;

void setup() {
  pinMode(pirPin, INPUT);
  pinMode(ledPin, OUTPUT);
  pinMode(buzzerPin, OUTPUT);

  digitalWrite(ledPin, LOW);
  digitalWrite(buzzerPin, LOW);

  Serial.begin(9600);
}

void loop() {
  int motionDetected = digitalRead(pirPin);

  if (motionDetected == HIGH) {
    digitalWrite(ledPin, HIGH);
    tone(buzzerPin, 1000);

    Serial.println("Motion detected!");
  } else {
    digitalWrite(ledPin, LOW);
    noTone(buzzerPin);

    Serial.println("No motion detected.");
  }

  delay(100);
}
```

## Testing Procedure

1. Upload the code to the Arduino Uno.
2. Power the circuit.
3. Allow the PIR sensor to stabilize for approximately 30–60 seconds.
4. Move in front of the sensor.
5. Confirm that the LED turns on and the buzzer sounds.
6. Open the Serial Monitor at 9600 baud to view the sensor status.

## Future Improvements

- Add an arm/disarm switch.
- Add an LCD display.
- Add a keypad for password protection.
- Add GSM SMS notification.
- Add Wi-Fi or IoT monitoring.
- Add a rechargeable battery backup.

## Applications

- Basic room monitoring.
- Door-entry alert systems.
- Educational embedded-systems projects.
- Electronics and Arduino demonstrations.
- Prototype home-security systems.

## Disclaimer

This is an educational prototype and should not be considered a replacement for a certified commercial security system.#mainscraft technology

## License

This project is available under the MIT License.
