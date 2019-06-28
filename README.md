# Internet Of Things

## Introduction
This training is aimed to who want to start with internet of things, is not an advance training or similar. I will cover some topics from my point of view and try to create a useful set of concepts. I will create a project to be sure that I don't miss any concept, from the ideation to the implementation. So.. my name is Juan Pablo Pizarro and you can find my professional profile at [linkedin](https://www.linkedin.com/in/juanpablopizarro/).

The training is all about internet of things so we need a project in mind to see the progress and for that I'm thinking in a tool for automatic irrigation system but you can go with your own ideas if you have some features in common with this training like wifi connection, BLE, OTA and Cloud Computing.

## Table of Contents

### Microprocessor vs microcontroller
The term microprocessor and microcontroller have always been confused with each other. Both of them have been designed for real time application. They share many common features and at the same time they have significant differences.

Microprocessor is an integrated circuit which has only the CPU inside them. These microprocessors don’t have RAM, ROM, and other peripheral on the chip. A system designer has to add them externally to make them functional. Application of microprocessor includes Desktop PC’s, Laptops, etc.
 
But this is not the case with Microcontrollers. Microcontroller has a CPU, in addition with a fixed amount of RAM, ROM and other peripherals all embedded on a single chip. At times it is also termed as a mini computer or a computer on a single chip. Today different manufacturers produce microcontrollers with a wide range of features available in different versions. Some manufacturers are ATMEL, Microchip, TI, Freescale, Philips, Motorola etc. 
 
Microcontrollers are designed to perform specific tasks. Specific means applications where the relationship of input and output is defined. Depending on the input, some processing needs to be done and output is delivered. For example, keyboards, mouse, washing machine, digicam, pendrive, cars, bikes, telephone, mobiles, watches, etc. Since the applications are very specific, they need small resources like RAM, ROM, I/O ports etc and hence can be embedded on a single chip. This in turn reduces the size and the cost.

### ESP32 & Tools
The ESP32 Board is the ESP8266 successor, loaded with lots of new features. It has Wi-Fi and Bluetooth wireless capabilites. There are many ESP32 development boards, we will focus on the ESP32 DOIT DEVKIT V1 Board.

![ESP32 Board](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/esp32_board.png)

This board comes with the ESP-WROOM-32 chip. It has a 3.3V voltage regulator that drops the input voltage to power the ESP32 chip. It also comes with a CP2102 chip that allows you to plug the ESP32 to your computer to program it.

![ESP32 Board Buttons](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/esp32_board_buttons.png)

The board has two on-board buttons: the ENABLE and the BOOT button.
If you press the ENABLE button, it reboots your ESP32. If you hold down the BOOT button and then press the enable, the ESP32 reboots in programming mode.

#### ESP32 Specifications
- It is dual core.
- It has Wi-Fi: 2.4GHz up to 150 Mbit/s
- It has bluetooth: BLE (Bluetooth Low Energy) and legacy Bluetooth
- It runs 32-bit programs.
- The clock frequency can go up to 240MHz.
- It has 512kB RAM
- This board comes with 30 pins, 15 in each row.
- It has a wide variety of peripherals available: capacitive touch, ADCs (Analog-to-digital converter), DACs (Digital-to-analog converter), UART (universal asynchronous receiver/transmitter), SPI (Serial peripheral interface), I2C (Inter-integrated circuit), PWM (pulse width modulation) and more.

![ESP32 DEVKIT V1](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/esp32_devkit_v1_doit.png)

### Setting up enviroment for Linux

1. [Install Visual Studio Code](https://code.visualstudio.com/download "VSC Download")
2. [Install PlatfromIO IDE for VSC](https://platformio.org/install/ide?install=vscode "PlatformIO IDE")
3. [Install Micropython IDE for VSC](https://marketplace.visualstudio.com/items?itemName=dphans.micropython-ide-vscode "Micropython IDE")
4. [Install Pymakr](https://marketplace.visualstudio.com/items?itemName=pycom.Pymakr "Pymakr")
5. [Python prerequisites](https://code.visualstudio.com/docs/python/python-tutorial#_prerequisites "Python prerequisites")
6. [Install Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python "Python Install")
7. Add user to dialout group: 'sudo usermod -a -G dialout $USER'
    
### Examples

#### Led Example
This project consists of simply blinking the ESP32 on-board LED. The on-board LED corresponds to GPIO 2. 
This project works as follows: 
- First, the LED turns on for 1 second. GPIO 2 set to HIGH.
- Second, the LED turns off for 1 second. GPIO 2 set to LOW.
- The pattern continues until you exit the program.

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

The code in c++ is as follows:
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

#### Button Example

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

#### ADC Example

This project consists of using the ADC (analog to digital converter). This will allow you to read voltages between 0V and 3.3V. The ESP32 has 12 bit resolution ADC, so the voltage measured is assigned to a value between 0 and 4095. In which 0V corresponds to 0, and 3.3V corresponds to 4095. Any voltage between 0V and 3.3V is given the corresponding value in between.

In the ESP32, the following GPIOs can act as ADC pins: 0,2,4,12,13,14,15,25,26,27,32,33,34,35,36 and 39.

ESP32 ADC pins have 12 bit resolution by default, but this can be changed by code.

![ESP32 ADC Example](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/esp32_adc_example.png)

The code in python is as follows:
```python
from machine import Pin, ADC
from time import sleep

pot = ADC(Pin(34))        #Create ADC object called pot on GPIO 34
pot.atten(ADC.ATTN_11DB)  #Full range: 3.3V

while True:
 pot_value = pot.read()   #Read  the pot value and save it in the pot_value variable
 print(pot_value)
 sleep(0.1)               #Add delay of 100ms
```
Save it as "main.py" and upload it to the ESP32 board. If you open the serial port monitor you should see the different values of the ADC, they should be values between 0 to 4095.

The attent() method can take the followin arguments:

- ADC.ATTN_0DB -- the full range voltaje: 1.2V
- ADC.ATTN_2_5_DB -- the full range voltage: 1.5V
- ADC.ATTN_6DB -- the full range voltage: 2.0V
- ADC.ATTN_11DB -- the full range voltage: 3.3V

The resolution can be changed by using the width() method:

```python
ADC.width(bit)
```
The bit argument can be one of the following parameters:

- ADC.WIDTH_9BIT: range 0 to 511.
- ADC.WIDTH_10BIT: range 0 to 1023.
- ADC.WIDTH_11BIT: range 0 to 2047.
- ADC.WIDTH_12BIT: range 0 to 4095.

The code in c++ is as follows:
```cpp
#define ADC 34
 
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


#### PWM Example
#### Wifi Example
