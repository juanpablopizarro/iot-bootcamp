# PWM Example

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
#include "Arduino.h"
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

The same signal of the led pin can be used with a dc motor. Except that a motor driver is neeeded and an additional power source. Just connect a 5v power to the driver, on the exit of the driver motor connect the dc motor and the output signal of the ESP32 connect it to the input of the motor driver.

Then you should be able to regulate the motor speed by the ADC pot.
