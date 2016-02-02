# Install Xilinx Tools

The Xilinx tools provide all required tool chains to compile and link applications for Xilinx supported platforms, create and configure hardware designs and creating bitstreams.


## Xilinx Vivado Tools
* [Download](http://www.xilinx.com/support/download/index.htm) the Xilinx Vivado tools suite.

Output Files Produced
* Installation of Xilinx tools on user's local computer

### Task Description
The complete hardware/software work flow for Xilinx devices relies on a number of Xilinx-provided tools. These tools are available as download for Linux and Windows based systems. Please, follow the installer to install the tools on your system. Note that the Xilinx SDK tools must also be installed for embedded linux applications.

### Platform specific hints & tips
Ubuntu 12.04 LTS x86_64 users may run into issues related to missing dependencies when installing the Xilinx tools. This release of Ubuntu lacks some needed 32-bit libraries which need to be installed. This can be done by executing:
```
bash$ sudo apt-get install ia32-libs
```

### Setting Up the Tools
Many software items, such as Linux, use the environment variable CROSS_COMPILE, to invoke the cross compiler that is used to build it (SDK must be installed). Also the $PATH environment variable has to be extended to find the newly installed tools.
```bash
bash$ export CROSS_COMPILE=<x-tool prefix>
bash$ source <Xilinx Tools installation directory>/ISE_DS/settings64.sh # use settings32.sh on 32-bit operating systems
```
The Xilinx tools provide the following cross toolchains:

|Target Architecture |x-tool prefix|
|:---:|:---:|
|Zynq |arm-xilinx-linux-gnueabi-|
|ZynqMP|aarch64-linux-gnu-|
|Microblaze little endian|microblazeel-xilinx-linux-gnu-|
|Microblaze big endian|microblaze-xilinx-linux-gnu-|
|PowerPC|powerpc-eabi-|
