# ADC Example

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
