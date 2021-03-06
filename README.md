## Introduction

**TahakomAVRLib** is a C++ library to program Atmel AVR microcontrollers. 
The library make use of the AVR standard C library and is written for easy usage.

Currently, the classes compile on the **ATmega48P/88P/168P/328P AVR microcontrollers** family. 


## Library structure 

The library is composed of several classes that abstract the internal elements of a microcontroller and some external components that when hooked up to the chip can perform some actions. 

These classes implement all functionalities and are organized into the namespaces: 

* core
* io (input/output)
* or components

Several [Applications](#applications) and [Projects](#projects) are implemented in order to demonstrate the library usage. 

A more detailed description of the code listings can be found in the [library documentation](TahakomAVRLibDoc.pdf) (generated by Doxygen)



## Software setup  

 Before using the library and start programming and interfacing external peripherals, some software packages need to be installed in your system: 

* binutils-avr: for getting tools like assembler, linker, ...
* gcc-avr : AVR GNU C cross-compiler
* avr-libc: AVR C library
* avrdude : driver program for downloading/uploading code and data from/to Atmel AVR microcontrollers



### Linux

In Linux (Ubuntu in my case), the software packages can be installed as follows:

```
sudo apt-get update
sudo apt-get install gcc build-essential
sudo apt-get install gcc-avr binutils-avr avr-libc gdb-avr
sudo apt-get install avrdude
```

### Windows

In Windows, the software packages can be downloaded and installed as follows:

* AVR toolchain for windows: can be downloaded from the Atmel's website [download](https://www.microchip.com/en-us/development-tools-tools-and-software/gcc-compilers-avr-and-arm)
* avrdude: can be downloaded from [download](http://download.savannah.gnu.org/releases/avrdude/)
* make: can be downloaded from [download](http://fab.cba.mit.edu/classes/863.16/doc/projects/ftsmin/make-3.81.exe)
* cmake: binary distribution can be downloaded from [download](https://cmake.org/download/)

An alternative, would be to download the precompiled AVR-GCC toolchain from [download](https://blog.zakkemble.net/avr-gcc-builds/) that also include avrdude and make utilities but not cmake.

Before using these software tools, you need to update the **PATH** environement variable with the file paths to their executables and restart the system.

## Compile and Flash programs

To compile and flash a program code to the AVR chip via USB port, you need to:

* Install the USB driver for the programmer used
* Adapt the CMakeLists.txt parameters to your system configuration: 
    * **MCU**: AVR chip used 
    * **F_CPU**: AVR CPU frequency
    * **BAUD**: Baude rate for serial communication
    * **PROG_TYPE**: Programmer type
    * **AVRFLASH_PORT**: Flash port name
* Change compiler flags if necessary
 
 and execute the following steps (shown for the [Blink a Led](applications/BlinkLed) application): 

### Linux
 
```
../BlinkLed$ mkdir build
../BlinkLed$ cd build
../BlinkLed/build$ cmake ..
../BlinkLed/build$ make flash
```
### Windows

```
../BlinkLed$ mkdir build
../BlinkLed$ cd build
../BlinkLed/build$ cmake .. -G "Unix Makefiles"
../BlinkLed/build$ make flash
```
## Hardware setup  

* AVR chip either barebone or on a development board like an Arduino UNO
* A bunch of Leds, resistors, drivers, sensors and actuators
* A breadboard
* Jumper wires
* An AVR ISPProgrammer (optional)


## Applications

These applications demonstrate the usage of **TahakomAVRLib** in simple examples:

* [Blink a Led](applications/BlinkLed)
* [AVR Square-Wave Organ](applications/Organ)
* [AVR Music Box](applications/MusicBox)
* [AVR Light Meter](applications/LightMeter)


## Projects

These are more complex projects implemented using **TahakomAVRLib**


## Author

* Farid Oubbati
* Date: 12-May-2018
* Copyright (c) 2018

## License

This project is licensed under the MIT License - see the [LICENSE.txt](LICENSE.txt) file for more details
