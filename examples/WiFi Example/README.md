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

#### Setting up enviroment for c++ develop

1. [Install Visual Studio Code](https://code.visualstudio.com/download "VSC Download")

- Download the .deb file and save it to a known folder.

![VSC_1](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_VSC_1.png)

- Double click on the downloaded .deb file and select install. 
- It will take a moment until the program is installed.

![VSC_2](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_VSC_2.png)

2. [Install PlatfromIO IDE for VSC](https://platformio.org/install/ide?install=vscode "PlatformIO IDE")

- Open Visual Studio Code.

![PIO_1](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_PIO_1.png)

- Go to the 'Extentions' section and search for 'Platformio'.

![PIO_2](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_PIO_2.png)

- Press install and wait for the process to finish.

![PIO_3](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_PIO_3.png)

![PIO_4](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_PIO_4.png)

- After that you should see the PlatformIO IDE extention.

![PIO_5](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_PIO_5.png)

- Go to 'Platforms', press on 'Intall Embedded Platform', search for 'Espressif 32' and install it.

![PIO_6](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_PIO_6.png)

![PIO_7](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_PIO_7.png)

![PIO_8](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_PIO_8.png)

#### Setting up enviroment for python develop

1. [Install Micropython IDE for VSC](https://marketplace.visualstudio.com/items?itemName=dphans.micropython-ide-vscode "Micropython IDE")
2. [Install Pymakr](https://marketplace.visualstudio.com/items?itemName=pycom.Pymakr "Pymakr")
3. [Python prerequisites](https://code.visualstudio.com/docs/python/python-tutorial#_prerequisites "Python prerequisites")
4. [Install Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python "Python Install")
5. Add user to dialout group: 'sudo usermod -a -G dialout $USER'
    
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
#include <driver/adc.h>

void setup() {
  adc1_config_width(ADC_WIDTH_BIT_12);
  adc1_config_channel_atten(ADC1_CHANNEL_6,ADC_ATTEN_DB_11);
}

void loop() {
  int val = adc1_get_raw(ADC1_CHANNEL_6);
  printf( "%i\n", val);
  delay(10);
}
```


#### PWM Example

If you alternate an LED's voltage between HIGH and LOW very fast, your eyes can't keep up with the speed at which the LED switches on and off; you will simply see some gradations in brightness.

That's basically how PWM works, by producing an output that changes between HIGH and LOW at a very high frequency. The duty cycle is the fraction of the time period at which the LED is set to HIGH.

![PWM](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/esp32_pwm.png)

That means, a duty cycle of 50 percent results in 50 percent LED brightness, a duty cycle of 0 means the LED is fully off, and a duty cycle of 100 means the LED is fully on. Changing the duty cycle is how you produce different levels of brightness.

This project consists to control the PWM duty cycle with a potentiometer through the ADC.

You will need:
- 5mm LED
- 330 Ohm resistor
- Potentiometer

![PWM ADC Example](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/esp32_pwm_adc_example.png)

The code in python is as follows:
```python
from machine import Pin, ADC, PWM
from time import sleep

frequency = 5000
led = PWM(Pin(5),frequency)   #Define frequency of the PWM signal and create a PWM object called led on GPIO 5
pot = ADC(Pin(34))            #Create ADC object called pot on GPIO 34
pot.width(ADC.WIDTH_10BIT)    #Set analog reading to 10bit resolution to match the PWM duty cycle
pot.atten(ADC.ATTN_11DB)      #Full range: 3.3V

while True:
 pot_value = pot.read()       #Read  the pot value and save it in the pot_value variable
 print(pot_value)             #Print the value on the shell
 if pot_value < 15:
  led.duty(0)
 else:
  led.duty(pot_value)
  
 sleep(0.1)                    #Add delay of 100ms
```

The code in c++ is as follows:

```cpp
#include <driver/adc.h>

// the number of the LED pin
const int ledPin = 15;  

const int freq = 5000;
const int ledChannel = 0;
const int resolution = 10;

void setup() {
  adc1_config_width(ADC_WIDTH_BIT_10);
  adc1_config_channel_atten(ADC1_CHANNEL_6,ADC_ATTEN_DB_11);
  ledcSetup(ledChannel, freq, resolution);                      // configure LED PWM functionalitites
  ledcAttachPin(ledPin, ledChannel);                            // attach the channel to the GPIO to be controlled  
}

void loop() {
  int val = adc1_get_raw(ADC1_CHANNEL_6);
  printf( "%i\n", val);
  if (val < 15)
  {
    ledcWrite(ledChannel, 0);
  }
  else
  {
    ledcWrite(ledChannel, val);
  }
  delay(10);
}
```

Upload the code to the ESP32, you should be able to control the LED brightness by rotating the potentiometer and read the reading from the potentiometer on the shell.

#### Wifi Example

The WiFi libraries provide support for configuring and monitoring the ESP32 WiFi networking functionality. This includes configuration for:

- Station mode (aka STA mode or WiFi client mode). ESP32 connects to an access point.
- AP mode (aka Soft-AP mode or Access Point mode). Stations connect to the ESP32.
- Combined AP-STA mode (ESP32 is concurrently an access point and a station connected to another access point).
- Various security modes for the above (WPA, WPA2, WEP, etc.)
- Scanning for access points (active & passive scanning).
- Promiscuous mode for monitoring of IEEE802.11 WiFi packets.

In this project we will connect to Wifi throught the ESP32, so we will be using the ESP32 in WiFi client mode.

The code in python is as follows:
```python
import network
 
    ssid = "yourNetworkName"
    password =  "yourNetworkPassword"
 
    station = network.WLAN(network.STA_IF)
 
    if station.isconnected() == True:
        print("Already connected")
        return
 
    station.active(True)
    station.connect(ssid, password)
 
    while station.isconnected() == False:
        pass
 
    print("Connection successful")
    print(station.ifconfig())
```
Save it as "main.py" and upload it to the ESP32 board.

The code in c++ is as follows:
```cpp
#include "WiFi.h"
 
const char* ssid = "yourNetworkName";
const char* password =  "yourNetworkPass";
 
void setup() {
 
  Serial.begin(115200);
 
  WiFi.begin(ssid, password);
 
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.println("Connecting to WiFi..");
  }
 
  Serial.println("Connected to the WiFi network");
 
}
 
void loop() {}
```
#### OTA Example

The OTA Web Updater allows you to update/upload new code to your ESP32 using a browser, without the need to make a serial connection between the ESP32 and your computer.

OTA programming is useful when you need to update code to ESP32 boards that are not easily accessible. The example here works when the ESP32 and your browser are on your local network.

The only disadvantage of the OTA Web Updater is that you have to add the code for OTA in every sketch you upload, so that you’re able to use OTA in the future.

How does OTA Web Updater Works?

- The first sketch should be uploaded via serial port. This sketch should contain the code to create the OTA Web Updater, so that you are able to upload code later using your browser.
- The OTA Web Updater sketch creates a web server you can access to upload a new sketch via web browser.
- Then, you need to implement OTA routines in every sketch you upload, so that you’re able to do the next updates/uploads over-the-air.
- If you upload a code without a OTA routine you’ll no longer be able to access the web server and upload a new sketch over-the-air.

The ESP32 is prepared for OTA support by creating two data partitions.  This example creates an asynchronous web server where you can upload new code to your board without the need for a serial connection.

The code in c++ is as follows:
```cpp
#include <WiFi.h>
#include <WiFiClient.h>
#include <WebServer.h>
#include <ESPmDNS.h>
#include <Update.h>

const char* host = "esp32";
const char* ssid = "Your_ssid";
const char* password = "Your_pass";

WebServer server(80);

/*
 * Login page
 */

const char* loginIndex = 
 "<form name='loginForm'>"
    "<table width='20%' bgcolor='A09F9F' align='center'>"
        "<tr>"
            "<td colspan=2>"
                "<center><font size=4><b>ESP32 Login Page</b></font></center>"
                "<br>"
            "</td>"
            "<br>"
            "<br>"
        "</tr>"
        "<td>Username:</td>"
        "<td><input type='text' size=25 name='userid'><br></td>"
        "</tr>"
        "<br>"
        "<br>"
        "<tr>"
            "<td>Password:</td>"
            "<td><input type='Password' size=25 name='pwd'><br></td>"
            "<br>"
            "<br>"
        "</tr>"
        "<tr>"
            "<td><input type='submit' onclick='check(this.form)' value='Login'></td>"
        "</tr>"
    "</table>"
"</form>"
"<script>"
    "function check(form)"
    "{"
    "if(form.userid.value=='admin' && form.pwd.value=='admin')"
    "{"
    "window.open('/serverIndex')"
    "}"
    "else"
    "{"
    " alert('Error Password or Username')/*displays error message*/"
    "}"
    "}"
"</script>";
 
/*
 * Server Index Page
 */
 
const char* serverIndex = 
"<script src='https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js'></script>"
"<form method='POST' action='#' enctype='multipart/form-data' id='upload_form'>"
   "<input type='file' name='update'>"
        "<input type='submit' value='Update'>"
    "</form>"
 "<div id='prg'>progress: 0%</div>"
 "<script>"
  "$('form').submit(function(e){"
  "e.preventDefault();"
  "var form = $('#upload_form')[0];"
  "var data = new FormData(form);"
  " $.ajax({"
  "url: '/update',"
  "type: 'POST',"
  "data: data,"
  "contentType: false,"
  "processData:false,"
  "xhr: function() {"
  "var xhr = new window.XMLHttpRequest();"
  "xhr.upload.addEventListener('progress', function(evt) {"
  "if (evt.lengthComputable) {"
  "var per = evt.loaded / evt.total;"
  "$('#prg').html('progress: ' + Math.round(per*100) + '%');"
  "}"
  "}, false);"
  "return xhr;"
  "},"
  "success:function(d, s) {"
  "console.log('success!')" 
 "},"
 "error: function (a, b, c) {"
 "}"
 "});"
 "});"
 "</script>";

/*
 * setup function
 */
void setup(void) {
  Serial.begin(115200);

  // Connect to WiFi network
  WiFi.begin(ssid, password);
  Serial.println("");

  // Wait for connection
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.print("Connected to ");
  Serial.println(ssid);
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());

  /*use mdns for host name resolution*/
  if (!MDNS.begin(host)) { //http://esp32.local
    Serial.println("Error setting up MDNS responder!");
    while (1) {
      delay(1000);
    }
  }
  Serial.println("mDNS responder started");
  /*return index page which is stored in serverIndex */
  server.on("/", HTTP_GET, []() {
    server.sendHeader("Connection", "close");
    server.send(200, "text/html", loginIndex);
  });
  server.on("/serverIndex", HTTP_GET, []() {
    server.sendHeader("Connection", "close");
    server.send(200, "text/html", serverIndex);
  });
  /*handling uploading firmware file */
  server.on("/update", HTTP_POST, []() {
    server.sendHeader("Connection", "close");
    server.send(200, "text/plain", (Update.hasError()) ? "FAIL" : "OK");
    ESP.restart();
  }, []() {
    HTTPUpload& upload = server.upload();
    if (upload.status == UPLOAD_FILE_START) {
      Serial.printf("Update: %s\n", upload.filename.c_str());
      if (!Update.begin(UPDATE_SIZE_UNKNOWN)) { //start with max available size
        Update.printError(Serial);
      }
    } else if (upload.status == UPLOAD_FILE_WRITE) {
      /* flashing firmware to ESP*/
      if (Update.write(upload.buf, upload.currentSize) != upload.currentSize) {
        Update.printError(Serial);
      }
    } else if (upload.status == UPLOAD_FILE_END) {
      if (Update.end(true)) { //true to set the size to the current progress
        Serial.printf("Update Success: %u\nRebooting...\n", upload.totalSize);
      } else {
        Update.printError(Serial);
      }
    }
  });
  server.begin();
}

void loop(void) {
  server.handleClient();
  delay(1);
}
```
Upload the previous code to your ESP32 board. Don’t forget to enter your network credentials and select the right board and serial port.

After uploading the code, open the Serial Monitor at a baud rate of 115200, press the ESP32 enable button, and you should get the ESP32 IP address.

Now, you can upload code to your ESP32 over-the-air using a browser on your local network.

To test the OTA Web Updater you can disconnect the ESP32 from your computer and power it using a power bank, for example.

Open a browser in your network and enter the ESP32 IP address. You should get the following:

![ESP32_login](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/esp32-login.jpg)

Enter the username and the password:

Username: admin
Password: admin
You can change the username and password on the code.

Note: After you enter the username and password, you are redirected to the /serverIndex URL. You don’t need to enter the username and password to access the /serverIndex URL. So, if someone knows the URL to upload new code, the username and password don’t protect the web page from being accessible from others.

![ESP32_server](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/esp32-server-index.jpg)

A new tab should open on the /serverIndex URL. This page allows you to upload a new code to your ESP32. You should upload .bin files (we’ll see how to do that in a moment).

When uploading a new sketch over-the-air, you need to keep in mind that you need to add code for OTA in your new sketch, so that you can always overwrite any sketch with a new one in the future. So, we recommend that you modify the previous sketch to include your own code.

For learning purposes let’s upload a new code that blinks an LED. 

```cpp
#include <WiFi.h>
#include <WiFiClient.h>
#include <WebServer.h>
#include <ESPmDNS.h>
#include <Update.h>

#define LED 2

const char* host = "esp32";
const char* ssid = "Your_ssid";
const char* password = "Your_pass";

WebServer server(80);

/*
 * Login page
 */

const char* loginIndex = 
 "<form name='loginForm'>"
    "<table width='20%' bgcolor='A09F9F' align='center'>"
        "<tr>"
            "<td colspan=2>"
                "<center><font size=4><b>ESP32 Login Page</b></font></center>"
                "<br>"
            "</td>"
            "<br>"
            "<br>"
        "</tr>"
        "<td>Username:</td>"
        "<td><input type='text' size=25 name='userid'><br></td>"
        "</tr>"
        "<br>"
        "<br>"
        "<tr>"
            "<td>Password:</td>"
            "<td><input type='Password' size=25 name='pwd'><br></td>"
            "<br>"
            "<br>"
        "</tr>"
        "<tr>"
            "<td><input type='submit' onclick='check(this.form)' value='Login'></td>"
        "</tr>"
    "</table>"
"</form>"
"<script>"
    "function check(form)"
    "{"
    "if(form.userid.value=='admin' && form.pwd.value=='admin')"
    "{"
    "window.open('/serverIndex')"
    "}"
    "else"
    "{"
    " alert('Error Password or Username')/*displays error message*/"
    "}"
    "}"
"</script>";
 
/*
 * Server Index Page
 */
 
const char* serverIndex = 
"<script src='https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js'></script>"
"<form method='POST' action='#' enctype='multipart/form-data' id='upload_form'>"
   "<input type='file' name='update'>"
        "<input type='submit' value='Update'>"
    "</form>"
 "<div id='prg'>progress: 0%</div>"
 "<script>"
  "$('form').submit(function(e){"
  "e.preventDefault();"
  "var form = $('#upload_form')[0];"
  "var data = new FormData(form);"
  " $.ajax({"
  "url: '/update',"
  "type: 'POST',"
  "data: data,"
  "contentType: false,"
  "processData:false,"
  "xhr: function() {"
  "var xhr = new window.XMLHttpRequest();"
  "xhr.upload.addEventListener('progress', function(evt) {"
  "if (evt.lengthComputable) {"
  "var per = evt.loaded / evt.total;"
  "$('#prg').html('progress: ' + Math.round(per*100) + '%');"
  "}"
  "}, false);"
  "return xhr;"
  "},"
  "success:function(d, s) {"
  "console.log('success!')" 
 "},"
 "error: function (a, b, c) {"
 "}"
 "});"
 "});"
 "</script>";

/*
 * setup function
 */
void setup(void) {
  pinMode(LED, OUTPUT);
  
  Serial.begin(115200);

  // Connect to WiFi network
  WiFi.begin(ssid, password);
  Serial.println("");

  // Wait for connection
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.print("Connected to ");
  Serial.println(ssid);
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());

  /*use mdns for host name resolution*/
  if (!MDNS.begin(host)) { //http://esp32.local
    Serial.println("Error setting up MDNS responder!");
    while (1) {
      delay(1000);
    }
  }
  Serial.println("mDNS responder started");
  /*return index page which is stored in serverIndex */
  server.on("/", HTTP_GET, []() {
    server.sendHeader("Connection", "close");
    server.send(200, "text/html", loginIndex);
  });
  server.on("/serverIndex", HTTP_GET, []() {
    server.sendHeader("Connection", "close");
    server.send(200, "text/html", serverIndex);
  });
  /*handling uploading firmware file */
  server.on("/update", HTTP_POST, []() {
    server.sendHeader("Connection", "close");
    server.send(200, "text/plain", (Update.hasError()) ? "FAIL" : "OK");
    ESP.restart();
  }, []() {
    HTTPUpload& upload = server.upload();
    if (upload.status == UPLOAD_FILE_START) {
      Serial.printf("Update: %s\n", upload.filename.c_str());
      if (!Update.begin(UPDATE_SIZE_UNKNOWN)) { //start with max available size
        Update.printError(Serial);
      }
    } else if (upload.status == UPLOAD_FILE_WRITE) {
      /* flashing firmware to ESP*/
      if (Update.write(upload.buf, upload.currentSize) != upload.currentSize) {
        Update.printError(Serial);
      }
    } else if (upload.status == UPLOAD_FILE_END) {
      if (Update.end(true)) { //true to set the size to the current progress
        Serial.printf("Update Success: %u\nRebooting...\n", upload.totalSize);
      } else {
        Update.printError(Serial);
      }
    }
  });
  server.begin();
  pinMode(LED,OUTPUT);
}

void loop(void) {
  server.handleClient();
  delay(1);

  delay(1000);
  digitalWrite(LED,HIGH);
  delay(1000);
  digitalWrite(LED,LOW);
  }
```
As you can see, we’ve added the “blinking led” code to the OTAWebUpdater code, so that we’re able to make updates later on.

Now, you should see the on board led blinking.