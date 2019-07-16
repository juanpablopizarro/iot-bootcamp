# Setting up enviroment for c++ develop

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

3. [Install CP2102 Driver](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers "CP2102")

- Download the corresponding linux file and save it.

- Go to the downloaded folder and unzip it.

- Open a bash and navigate to the unziped folder.

- Once in the folder, write "make" and wait for the process to finish. Now you should see more files generated.

- Before the next step, write "uname -r" to display the version of your linux kernel. In my case it is "4.15.0-54-generic".

- Now write: "sudo cp cp210x.ko /lib/modules/<kernel-version>/kernel/drivers/usb/serial". Enter your sudo password.

- Connect the board to the usb and check if visual studio code can see the board. If not, continue with the next steps.

- Then write "insmod /lib/modules/<kernel-version>/kernel/drivers/usb/serial/usbserial.ko"

- Finally, "insmod cp210x.ko"

4. Linux users have to install udev rules for PlatformIO supported boards/devices.

- Open a terminal and type 'curl -fsSL https://raw.githubusercontent.com/platformio/platformio-core/master/scripts/99-platformio-udev.rules | sudo tee /etc/udev/rules.d/99-platformio-udev.rules'

- Restart “udev” management tool: 'sudo service udev restart'

- Ubuntu/Debian users may need to add own “username” to the “dialout” group if they are not “root”. 
- Add user to dialout group: 'sudo usermod -a -G dialout $USER'
- Add user to plugdev group: 'sudo usermod -a -G plugdev $USER'
- Add user to tty group: 'sudo usermod -a -G tty $USER'
                              
- You will need to log out and log back in again (or reboot) for the user group changes to take effect.


