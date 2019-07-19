
# Led Example
This project consists of simply blinking the ESP32 on-board LED. The on-board LED corresponds to GPIO 2. 
This project works as follows: 
- First, the LED turns on for 1 second. GPIO 2 set to HIGH.
- Second, the LED turns off for 1 second. GPIO 2 set to LOW.
- The pattern continues until you exit the program.

## Python Instructions

1. Connect your device to an USB port. It will turn on a red light when plugged in.

2. Open Visual Studio Code. If you have done the [Setting up enviroment for python develop](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/setting_up_enviroment/Python/README.md) the board will be autodetected and connected. It will show a python prompt.

3. Go to Micropython button and start a project called "Blinking Led".

4. Check for the serial port that is being used: 'dmesg | grep tty'. In my case is /dev/ttyUSB0.

![Ports](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Ports.png)

When asked for the port enter that name.

The code in python is as follows:
```python
from machine import Pin
from time import sleep
led = Pin(2,Pin.OUT)
while True:
 led.value(not led.value())
 sleep(1)
```
Save it as "main.py" and upload it to the ESP32 board.

## CPP Instructions

1. Open Visual Studio Code. It will open in the PIO Home.

![LED_EXAMPLE_1](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/LED_Example_1.png)

2. Press on new project. It will open a project wizard.

- Name: Blinking Led
- Board: DOIT ESP32 DEVKIT V1
- Framework: Arduino

![LED_EXAMPLE_2](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/LED_Example_2.png)

3. After the project is generated, navigate to the 'main.cpp' file and copy the code.

```cpp
#define LED 2
 
void setup() {
  // Set pin mode
  pinMode(LED,OUTPUT);
}
 
void loop() {
  delay(1000);
  digitalWrite(LED,HIGH);
  delay(1000);
  digitalWrite(LED,LOW);
}
```

![LED_EXAMPLE_3](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/LED_Example_3.png)

4. Press the upload button, it will build and upload the code to the ESP32.

![LED_EXAMPLE_4](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/LED_Example_4.png)

5. Now you should see blinking the onboard led.

![LED_EXAMPLE_5](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/LED_Example_5.png)
