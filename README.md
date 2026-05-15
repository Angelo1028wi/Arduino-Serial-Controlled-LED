# Arduino Serial Controlled LED 🚦

Simple beginner project to turn ON/OFF the built-in LED using commands sent via Serial Monitor.
Perfect introduction to Serial Communication, Data Types, and basic logic control.

---

## 🛒 Components Needed
- Arduino Uno R3
- USB Cable
- Computer with Arduino IDE

---

## ⚡ Wiring Diagram
**No external wiring needed!** Uses the built-in LED on Pin 13 (`LED_BUILTIN`).

---

## 💻 Code
```cpp
void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  if (Serial.available() > 0) {
    String data = Serial.readString();
    data.trim(); // Remove extra spaces/newlines

    if (data == "ON") {
      digitalWrite(LED_BUILTIN, HIGH);
      Serial.println("✅ LED TURNED ON");
    } 
    else if (data == "OFF") {
      digitalWrite(LED_BUILTIN, LOW);
      Serial.println("❌ LED TURNED OFF");
    }
  }
  delay(100);
}
