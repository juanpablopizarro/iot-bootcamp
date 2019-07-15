# Button Example

This project consists of building a simple button-led circuit. When the button is pressed, the LED should light up and turn off when the button is relesed.

![ESP32 Button Example](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/esp32_button_example.png)

In order to build the circuit you will need:

- 5mm LED
- 330 Ohm resistor
- A pushbutton
- 10 KOhm resistor

The code in python is as follows:
```python
from machine import Pin
from time import sleep
led = Pin(5,Pin.OUT)
button = Pin(4,Pin.IN)
while True:
 led.value(button.value())
 sleep(0.1)
```
Save it as "main.py" and upload it to the ESP32 board.

The code in c++ is as follows:

```cpp
#define LED 5
#define BUTTON 4

void setup() {
  pinMode(LED,OUTPUT);
  pinMode(BUTTON,INPUT);
}

void loop() {
  digitalWrite(LED,digitalRead(BUTTON));
  delay(1);
}
```
