# Setup a Serial Console

This guide will explain where and how to install the USB drivers and how to install and configure a terminal emulator which allows talking to the board.

##Downloading and installing USB to UART drivers

When using a Xilinx Development Board with a USB UART port use your mini-B USB cable to connect the USB UART port on the board to a PC. If the driver for this CP210x USB to UART bridge is recognized by your PC you may go to the next section, suggested HyperTerminal. If your USB to UART is not automatically recognized, the driver can be found and downloaded from the Silicon Labs website linked below.

Silicon Labs Website and installation process:
1. Go to: [Silicon Laboratories](http://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx)
2. Select the appropriate driver for your machine (VCP driver Kit)

![VCP drivers.jpg](http://www.wiki.xilinx.com/file/view/SI%20VCP%20drivers.jpg/442704062/SI%20VCP%20drivers.jpg)
Silicon Labs website driver download

3. Unzip CP210x_VCP_Windows to a directory
4. Double click on CP210xVCPInstaller_x64 (or X86 depending on the machine)
5. Agree to the license agreement and select finish when complete.

## Terminal Emulators
Common terminal emulators are:
* [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) : Select under Windows on Intel X86 "putty.exe" (the very first link)
* [TeraTerm](http://www.ayera.com/teraterm/)
* [minicom](http://alioth.debian.org/projects/minicom)
But there are plenty more. Just choose the one that fits you.

Connection Settings
The settings for the serial connection may differ from board to board, but a good guess (and they work for Zynq) are these settings:
baud rate = 115200
data bits = 8
stop bits = 1
flow control = none
parity = none
The serial device depends on your operating system and cable connection. On Windows the serial devices are usually called comN (N = 1, 2, 3, ...).
On Linux you'll find the serial devices in the /dev directory. Real serial devices are usually ttySN, UART via USB may be called ttyUSBN (again N = 1, 2, 3, ...).

Configuring Putty (Windows)
1. Open you putty
2. Once open, select the option of Serial connection
.
start.png
Open Hyper Terminal (Putty)

3. Then select Select Serial in the Category section.
inlkbuthgrxfthcygukgyftrgetrxychtgyjhbkblknm;l.png

4. To set the "Serial line to connect to" you must open the device manager to see which COM your board is connected.
To open you device manager go to Start -> (type in search) Device Manager
Go to the "Ports (COM & LPT)" section and look what COM your Silicon Labs USB to UART bridge is connected to
5. Write in the correct COM that your board is connected to.
6. Baud, section specific to the board, thus check the Getting started guide for the board that you have to get the correct baud rate.

Configuring minicom (Linux)
Minicom should be started with the -D <serial device> command line switch e.g.
minicom -D /dev/ttyUSB0

In minicom hit ctrl+a z, to get the help up. Navigate to options->serial port setup and configure the line according to your target platform.
zynq_tty_minicom.png