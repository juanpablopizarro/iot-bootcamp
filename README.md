# Internet Of Things

## Introduction
This training is aimed to who want to start with internet of things, is not an advance training or similar. I will cover some topics from my point of view and try to create a useful set of concepts. I will create a project to be sure that I don't miss any concept, from the ideation to the implementation.

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

IT IS NEEDED TO HAVE ADMIN RIGHTS FOR INSTALLING THE FOLLOWING PACKAGES.

- [Setting up enviroment for c++ develop](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/setting_up_enviroment/Cpp/README.md)

- [Setting up enviroment for python develop](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/setting_up_enviroment/Python/README.md)
    
### Examples

[LED Example](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/examples/Led%20Example/README.md)

[Button Example](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/examples/Button%20Example/README.md)

[ADC Example](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/examples/ADC%20Example/README.md)

[PWM Example](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/examples/PWM%20Example/README.md)

[Wifi Example](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/examples/WiFi%20Example/README.md)

[OTA Example](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/examples/OTA%20Example/README.md)
