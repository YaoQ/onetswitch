##Introduction
An ONetSwitch enables users in different development roles to build a complete networking system in a single node. Users can build the embedded system either from scratch, or based on some pre-built images.  
In either way, getting-started projects would help you
* to get acquainted with the board and its components  
* to make quick hardware tests on the main silicon and its peripherals  
* to understand the usage and be ready for next-stage development  

##Project List  
* [Zynq PS Test](https://github.com/MeshSr/wiki/wiki/GSG-ZynqPSTest)  
_Project to verify the clocks, resets, memories, etc at the ARM CPU side._  
* [IBERT](https://github.com/MeshSr/wiki/wiki/GSG-IBERT)  
_Project to verify the rate and SI of the transceivers using PRBS generator._  
* [MAC Loopback](https://github.com/MeshSr/wiki/wiki/GSG-MACLoopBack)  
_Project to verify the PHYs and the MACs on each of the Ethernet ports._  
* [PCIe Enumeration](https://github.com/MeshSr/wiki/wiki/GSG-PCIeRootEnum)  
_Project to verify the Mini PCIe and the configuration of PCIe Root Complex._  
* [QDRII+ Memory Test](https://github.com/MeshSr/wiki/wiki/GSG-QDRIIMemTest)  
_Project to verify the calibration of PL QDRII+ SRAM, with traffic generator._  
* [DDR3 Memory Test](https://github.com/MeshSr/wiki/wiki/GSG-DDR3MemTest)  
_Project to verify the calibration and read/write operations on PL DDR3 SDRAM._  

The table below shows the applicability.  

| Project       | ONS20 | ONS30 | ONS45 |
|:-------       |:-----:|:-----:|:-----:|
| ZynqPSTest    | o     | o     | o     |
| IBERT         | x     | o     | o     |
| MACLoopback   | o     | o     | o     |
| PCIeRootEnum  | x     | o     | o     |
| QDRIIMemTest  | x     | x     | o     |
| DDR3MemTest   | x     | o     | x     |
