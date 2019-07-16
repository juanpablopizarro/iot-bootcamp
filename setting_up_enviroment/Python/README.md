# Setting up enviroment for python develop

1. [Install Visual Studio Code](https://code.visualstudio.com/download "VSC Download")

- Download the .deb file and save it to a known folder.

![VSC_1](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_VSC_1.png)

- Double click on the downloaded .deb file and select install. 
- It will take a moment until the program is installed.

![VSC_2](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_VSC_2.png)

2. [Install CP2102 Driver](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers "CP2102")

- Download the corresponding linux file and save it.

![Install_Driver_1](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_Driver_1.png)

![Install_Driver_2](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_Driver_2.png)

![Install_Driver_3](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_Driver_3.png)

- Go to the downloaded folder and unzip it.

- Open a bash and navigate to the unziped folder.

![Install_Driver_4](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_Driver_4.png)

- Once in the folder, write "make" and wait for the process to finish. Now you should see more files generated.

![Install_Driver_5](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_Driver_5.png)

- Before the next step, write "uname -r" to display the version of your linux kernel. In my case it is "4.15.0-54-generic".

- Now write: "sudo cp cp210x.ko /lib/modules/kernel-version/kernel/drivers/usb/serial". Enter your sudo password.
  
![Install_Driver_6](https://github.com/juanpablopizarro/iot-bootcamp/blob/develop/images/Install_Driver_6.png)

- Then write "insmod /lib/modules/kernel-version/kernel/drivers/usb/serial/usbserial.ko"

- Finally, "insmod cp210x.ko"

3. [Install Micropython IDE for VSC](https://marketplace.visualstudio.com/items?itemName=dphans.micropython-ide-vscode "Micropython IDE")

- Open Visual Studio Code, press Ctrl+P and write 'ext install dphans.micropython-ide-vscode'.

- We will need to install some dependencies, open a bash and write the following commands line by line:

- 'sudo add-apt-repository ppa:deadsnakes/ppa'
- 'sudo apt-get update'
- 'sudo apt-get install python3.7'
- 'curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py'
- 'python get-pip.py --user'
         
4. [Install Pymakr](https://marketplace.visualstudio.com/items?itemName=pycom.Pymakr "Pymakr")

- Open Visual Studio Code, press Ctrl+P and write 'ext install pycom.Pymakr' 

- It needs nodejs to be installed. Let's install it: 'sudo apt-get install nodejs'

5. [Install Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python "Python Install")

- Open Visual Studio Code, press Ctrl+P and write 'ext install ms-python.python' 

- From within VS Code, select a Python 3 interpreter by opening the Command Palette (Ctrl+Shift+P), start typing the 'Python: Select Interpreter' command to search, then select the command.

6. Add user to dialout group: 'sudo usermod -a -G dialout $USER'

7. Check for the serial port that is being used: 'dmesg | grep tty'. In my case is /dev/ttyUSB0.
