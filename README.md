2.9inch E-Paper Display from seengreat:www.seengreat.com
 =======================================
# Instructions
## Product Overview
This product is a 2.9-inch e-ink display expansion module suitable for Raspberry Pi series boards, Arduino, STM32, and more. We provide example programs for both the C and Python versions on Raspberry Pi, as well as example programs for Arduino and STM32. These example programs enable drawing of dots, lines, rectangles, and circles, and they also allow displaying English letters, numbers, and images.<br>
## Product parameters
|Dimensions	|82mm (Length) * 38mm (Width)|
|----------------------|-----------------------------------|
|Pixels	|296*128|
|Display Color	|Monochrome|
|Voltage Translator	|TXS0108EPWR|
|Signal Interface	|SPI|
|Power Supply Voltage	|5V/3.3V|
|LCD Display Area	|66.9mm (H) * 29mm (W)|
|Grayscale |4|
|Full Refresh Time	|3S|
|Fast Refresh Time	|1.5S|
|Partial Refresh Time	|0.3S|
|Power Consumption	|9mW|
|Standby Power Consumption	|0.003mW |
## Product dimensions
|Size|82mm(Length)*38mm(width)|
|----|--------------------------------|
|Weight|20.6g(with screen)|
|Screw Size|M2.5|<br>
## Pin Definitions
|VCC	|3.3V&5V|
|-----------|----------|
|GND	|Power Ground|
|RST	|External Reset Pin (Low level for reset)|
|BUSY	|Busy Status Output Pin (High level indicates busy)|
|D/C	|Data/Command Control Pin (High level for data, low level for command)|
|MOSI	|SPI Communication MOSI Pin|
|CS	|SPI Chip Select Pin (Low level active)|
|CLK	|SPI Communication SCK Pin|
## Pin Definitions
Resource introduction as shown in the following figure:<br>
![image](https://github.com/seengreat/2.9inch-E-Paper-Display/blob/main/1.png)<br>
![image](https://github.com/seengreat/2.9inch-E-Paper-Display/blob/main/2.png)<br>
Resource Introduction Diagram<br>
①、2.9-inch e-ink display<br>
②、E-ink display connector<br>
③、SPI control interface connector<br>
④、Level conversion chip TXS0108<br>
⑤、SPI line selection switch<br>
# Usage
## Raspberry Pi demo codes usage
### Hardware interface configuration description
The example program for the Raspberry Pi uses the pin definitions numbered in wiringPi. The pin connections on the Raspberry Pi board are defined as follows in the table below：<br>
|E-Ink Display Interface	|WiringPi number	|BCM number|
|----------------------------------|----------------------|---------------|
|VCC	|3.3V	|3.3V|
|GND	|GND	|GND|
|RST	|P0	|17|
|BUSY	|P5	|24|
|D/C 	|P6	|25|
|MOSI	|MOSI/P12	|10|
|CLK	|SCLK/P14	|11|
|CS	|CE0/P10	|8|<br>
### Example Program Usage
All example programs provided with this product are based on the 4-wire SPI mode. Therefore, the default position for the switch on the back of the board (BS selection switch) should be set to "0".<br>	
#### Wiringpi library installation
sudo apt-get install wiringpi<br>
   wget https://project-downloads.drogon.net/wiringpi-latest.deb  # Version 4B upgrade of Raspberry Pi<br>
   sudo dpkg -i wiringpi-latest.deb<br>
   gpio -v # If version 2.52 appears, the installation is successful<br>
#For the Bullseye branch system, use the following command:<br>
git clone https://github.com/WiringPi/WiringPi<br>
cd WiringPi<br>
./build<br>
gpio -v<br>
#Running gpio - v will result in version 2.70. If it does not appear, it indicates an installation error<br>
If the error prompt "ImportError: No module named 'wiringpi'" appears when running the python version of the sample program, run the following command<br>
#For Python 2. x version<br>
pip install wiringpi<br>
 
#For Python version 3. X<br>
pip3 install wiringpi<br>
Note: If the installation fails, you can try the following compilation and installation:<br>
git clone --recursive https://github.com/WiringPi/WiringPi-Python.git<br>
Note: The -- recursive option can automatically pull the submodule, otherwise you need to download it manually.<br>
Enter the WiringPi Python folder you just downloaded, enter the following command, compile and install:<br>
#For Python 2. x version<br>
sudo python setup.py install <br>
#For Python version 3. X<br>
sudo python3 setup.py install<br>
If the following error occurs:<br>
"Error:Building this module requires either that swig is installed<br>
        (e.g.,'sudo apt install swig') or that wiringpi_wrap.c from the<br>
        source distribution (on pypi) is available."<br>
At this time, enter the command sudo apt install swig to install swig. After that, compile and install sudo python3 setup.py install. If a message similar to the following appears, the installation is successful.<br>
"ges<br>
Adding wiringpi 2.60.0 to easy-install.pth file<br>
Installed /usr/local/lib/python3.7/dist-packages/wiringpi-2.60.0-py3.7-linux-armv7<br>
Processing dependencies for wiringpi==2.60.0<br>
Finished processing dependencies for wiringpi==2.60.0"<br>
#### Open SPI interface
sudo raspi-config<br>
Enable SPI interface:<br>
Interfacing Options > SPI > Yes<br>
To view enabled SPI devices:<br>
ls /dev/spi * # The following will be printed: "/dev/spidev0.0" and "/dev/spidev0.1"<br>
#### Installation of python library
The demo codes uses the python 3 environment. To run the python demo codes, you need to install the pil, numpy, and spiderv libraries. Enter the following commands in order to install:<br>
sudo apt-get install python3-pil<br>
sudo apt-get install python3-numpy<br>
sudo apt-get install python3-pip<br>
sudo pip3 install spidev<br>
#### C version demo codes
Navigate to the C directory in the example program project folder:<br>
sudo make clean<br>
sudo make<br>
sudo ./main<br>
After entering the above command, you can observe the E-Ink display.<br>
#### python Version demo codes
Navigate to the Python directory in the example program project folder:<br>
python3 gui_demo.py<br>
After entering the above command, you can observe the E-Ink display.<br>
## Arduino MEGA Example Program Usage
### Hardware interface configuration description
|E-Ink display	|Arduino|
|----------------------|--------|
|VCC	|5V|
|GND	|GND|
|RST	|D9|
|BUSY	|D10|
|D/C 	|D8|
|MOSI	|D51|
|CLK	|D52|
|CS	|D53|
### Demo Codes Usage
Open the example program file using the Arduino IDE software. Click on "Verify" to confirm that there are no errors. Once verified, upload the program to the module and observe the E-Ink display.<br>
## Arduino UNO Example Program Usage
### Hardware Interface Configuration Instructions
|E-Ink Display Interface	|Arduino Interface|
|----------------------------------|-------------------|
|VCC	|5V|
|GND	|GND|
|RST	|D9|
|BUSY	|D8|
|D/C 	|D10|
|MOSI	|D13|
|CLK	|D12|
|CS	|D11|
## STM32 Demo Codes Usage
### Hardware interface configuration description
|E-Ink display|	STM32|
|----------------------|-------|
|VCC|	3.3V|
|GND|	GND|
|CS|	PB12|
|CLK|	PB13|
|MOSI|	PB15|
|DC|	PA8|
|RST|	PA11|
|BUSY|	PA12|
### Demo Codes Usage
Open the routine in directory 2.9inch E-Paper Display\demo codes\STM32 with Keil uVision5 software, compile it correctly, download it to the module, and observe the E-Ink display.<br>
## ESP32 Example Program Usage
### Hardware Interface Configuration Instructions
|E-Ink Display Interface|	ESP32 Interface|
|------------------------|--------------------------|
|VCC	|3.3V|
|GND	|GND|
|RST	|IO33|
|BUSY	|IO13|
|D/C 	|IO14|
|MOSI	|IO23|
|CLK	|IO18|
|CS	|IO27|
### Example Program Usage:
Open the example program project file with the Arduino IDE software. After compiling without errors, download it to the module, and observe the display situation of the e-ink screen.<br>
Image Creation and Modeling Instructions
### Image Creation
Create images that need to be displayed in 296*128 resolution as pure black and white images (grayscale is not supported), save them as BMP or JPG files (BMP format is recommended).<br>
### Modeling
Modeling can be done using the "image2lcd" software provided in the compressed package. <br>
1、Open the image that needs to be modeled.<br>
2、Output data type: Select "C Language Array (*.c)".<br>
3、Scan mode: Select "Vertical Scan".<br>
4、Output grayscale: Select "Monochrome".<br>
5、Maximum width and height: Select "296" "128", and click the arrow next to them to confirm.<br>
6、Do not check any of the 5 items as shown in the figure below.<br>
<img src="https://github.com/seengreat/2.9inch-E-Paper-Display/blob/main/3.png"><br>
7、Color inversion: Check to display the original image, uncheck for color inversion.<br>
8、Click "Save" to save the converted array to a file with the extension ".c".<br>
9、Finally, replace the corresponding array in the program code with the array from the ".c" file.<br>
<img src="https://github.com/seengreat/2.9inch-E-Paper-Display/blob/main/3.jpg"><br>
                                 Figure 2-2<br>
<img src="https://github.com/seengreat/2.9inch-E-Paper-Display/blob/main/4.jpg"><br>
Figure 2-3<br>
