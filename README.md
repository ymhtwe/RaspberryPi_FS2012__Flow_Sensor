# RaspberryPi_FS2012__Flow_Sensor
Interfacing IDT FS2012 flow sensor module with raspberry pi over I2C communication.

To read the data from the IDT FS2012 flow sensor module, the raspberry pi need to set up the I2C communication.
In this tutorial, the WiringPi library which is the Cpp library for raspberry pi is used to read data from sensor module over I2C.
So, to instll and use the WiringPi library, make sure you read the following web page, introduction to WiringPi before if you don't know the library well.
https://roboticsbackend.com/introduction-to-wiringpi-for-raspberry-pi/

The raspberry pi also need to activate the I2C communication and if you haven’t used I2C on your Raspberry Pi yet, it probably means that the I2C communication is not activated. To activate it, search for the “/boot/config.txt” file. Open this file (with sudo), find the line #dtparam=i2c_arm=on, and remove the leading ‘#’ to uncomment it. After that, reboot your Pi, and I2C will be activated as long as you don’t comment the I2C line again in the config file.

The program is written in C++ which use GNU compiler and normally Raspberry Pi OS includes all the packages needed to code in C/C++ directly after the installation.
But for any issues while compiling and running the program, consider the following the web page for fixing the issue.
https://raspberrytips.com/use-c-on-raspberry-pi/

To start reading sensor data,
1. Check Wiriging Diagram.jpg and Wiring Diagram 2.jpg for hardware connection
2. install WiringPi library on raspberry pi and activate I2C communication if you haven't activated yet
4. Download and save RaspberryPi_FS2012.cpp file from this repo to raspberry pi
5. Compile and Run the program in terminal

You can type this command to check all the connected I2C slave devices after compiling the program.
$ i2cdetect -y 1

-------------------------------------------------------------------------------------------------------------------------------------
Before compile and run the program, Don’t forget to link to the wiringPi library by using -lwiringPi.

$ g++ -o rpi_fs2012_wiringpi_i2c RaspberryPi_FS2012.cpp -lwiringPi 

$ ./rpi_fs2012_wiringpi_i2c 

FS2012 communication successfully setup

Data received: 


The sensor's reading data is now stored in received_data variable and edit the code to align with your requirements. 
Also read the sensor module's data sheet: section 7 for calculating the Flow Senor Output.
https://www.renesas.com/us/en/document/dst/fs2012-datasheet




