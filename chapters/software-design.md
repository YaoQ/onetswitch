## Build FSBL  
An FSBL can be generated within the template in SDK, based on the exported hardware description from Vivado system design.  
We have done some patches to the template (for ONS30), and added functions to program the clock generator during the boot stage (for ONS30 and ONS45). So it is recommended to make use of the pre-built FSBLs directly instead of regenerating, unless the following PS clock settings doesn't meet your design. Below is a typical settings for PS Clocks configured during FSBL stage.  
Find the pre-built FSBL images for different boards [here](https://github.com/MeshSr/common-bin/tree/master/fsbl/).   
Find the details of FSBL changes comparing to the official version [here](https://github.com/MeshSr/wiki/wiki/Topic-Bootloader).  

| PS Clock | Frequency |
| -------- | --------- |
| FCLK0    | 125MHz    |
| FCLK1    | 75MHz     |
| FCLK2    | 200MHz    |
| FCLK3    | unused    |


##Build SSBL (u-boot)  
**This step must be done in a Linux environment.**  
[Download](https://github.com/MeshSr/u-boot-meshsr) our official u-boot repo, and refer to the Xilinx Wiki [Build U-Boot](http://www.wiki.xilinx.com/Build+U-Boot) for u-boot image generation.  
To build u-boot for ONetSwitch execute

```bash
git clone https://github.com/MeshSr/u-boot-meshsr
cd u-boot-meshsr

make zynq_ons20_config # OR
make zynq_ons30_config # OR
make zynq_ons45_config

make ARCH=arm CROSS_COMPILE=arm-xilinx-linux-gnueabi-
```

Notice that the generated file 'u-boot' should be renamed with .elf extension. And pay attention to the usage of _mkimage_.  

```bash
cp -rp ./tools/﻿mkimage <somewhere-in-$PATH>
mv u-boot u-boot-<any suffix>.elf
```

The official u-boot for ONetSwitch is derived from [Xilinx u-boot](https://github.com/Xilinx/u-boot-xlnx).   
Find the details of u-boot changes comparing to the official version [here](https://github.com/MeshSr/wiki/wiki/Topic-Bootloader).  

Find the pre-built u-boot images for different boards and types of rootfs [here](https://github.com/MeshSr/common-bin/tree/master/u-boot/).  
Notice that we prefer _u-boot-ons*-ext.elf_ in our reference designs.  

##Build and Modify Rootfs  
Please refer to Xilinx Wiki [Build and Modify a Rootfs](http://www.wiki.xilinx.com/Build+and+Modify+a+Rootfs).  
You can [download](https://github.com/MeshSr/common-bin/tree/master/rootfs) a pre-built one directly from our repo.  

For _uramdisk.image.gz_, you have to put it directly in the FAT partition and use it together with _u-boot-ons*-ram.elf_.  
For *rootfs_ext4.tar.gz*, you need to extract and copy to the EXT partition with sudoer privilege, use with _u-boot-ons*-ext.elf_.  

##Build Device Tree Blob  
The Xilinx Wiki [Build Device Tree Blob](http://www.wiki.xilinx.com/Build+Device+Tree+Blob) provides two ways to create an original .dts.  
Changes has been done on the original tcl-generated .dts when the ONetSwitch and certain applications require more device/driver supporting. The recommended way is to take ours as the baseline, use or make changes on our modified .dts, and finally generate the .dtb using the Linux device tree complier.

```bash
<path-to-kernel-src>/script/dtc/dtc -I dts -O dtb -o devicetree.dtb devicetree.dts
```

The modification on the devicetree is closely related to the board hardware and the driver support. Please refer to the .dts in each ready-to-download folder for more details.  

## Build Linux Kernel  
**This step must be done in a Linux environment.**  
[Download](https://github.com/MeshSr/linux-meshsr) our official Linux repo, and refer to the Xilinx Wiki [Build Kernel](http://www.wiki.xilinx.com/Build+Kernel) for kernel image generation.  
To build kernel for ONetSwitch execute

```bash
git clone https://github.com/MeshSr/linux-meshsr
cd linux-meshsr

cp -p arch/arm/configs/meshsr_ons_defconfig .config
make uImage UIMAGE_LOADADDR=0x8000 ARCH=arm CROSS_COMPILE=arm-xilinx-linux-gnueabi-
```

The official Linux kernel for ONetSwitch is derived from [Xilinx Linux](https://github.com/Xilinx/linux-xlnx).  
Find the details of kernel changes comparing to the official version [here](https://github.com/MeshSr/wiki/wiki/Topic-Linux).  

Find the pre-built kernel image [here](https://github.com/MeshSr/common-bin/blob/master/kernel/uImage).  
