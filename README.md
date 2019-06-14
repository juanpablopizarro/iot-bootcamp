# Internet Of Things

## Introduction
This training is aimed to who want to start with internet of things, is not an advance training or similar. I will cover some topics from my point of view and try to create a useful set of concepts. I will create a project to be sure that I don't miss any concept, from the ideation to the implementation. So.. my name is Juan Pablo Pizarro and you can find my professional profile at [linkedin](https://www.linkedin.com/in/juanpablopizarro/).

The training is all about internet of things so we need a project in mind to see the progress and for that I'm thinking in a tool for automatic irrigation system but you can go with your own ideas if you have some features in common with this training like wifi connection, BLE, OTA and Cloud Computing.

## Table of Contents
### Processors, controllers.. hardware.
    
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
5. [Install Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python "Python Install")
[Python prerequisites](https://code.visualstudio.com/docs/python/python-tutorial#_prerequisites "Python prerequisites")
6. Add user to dialout group: 'sudo usermod -a -G dialout $USER'
If your don't have the sudo user, contact Service Desk and ask them to add your user to that group.
    
### Micropython Examples
1. [led]()
2. [button]()
3. [ADC]()
4. [PWM]()

### C/C++ Examples
1. [led]()
2. [button]()
3. [ADC]()
4. [PWM]()
