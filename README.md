# DDS Controller
PC controlled [AD9850 DDS module](http://artofcircuits.com/product/ad9850-dds-module) using a [PSoC 4](http://www.cypress.com/products/32-bit-arm-cortex-m0-psoc-4).  
The idea is to have a small kit that can generate create a required frequency at the DDS module.
All controls are accessible via the COM interface using a terminal application.

Author: Angad Gill

## Hardware  
The $4 PSoC 4 [Prototyping Kit](http://www.cypress.com/documentation/development-kitsboards/psoc-4-cy8ckit-049-4xxx-prototyping-kitshttp://www.cypress.com/documentation/development-kitsboards/psoc-4-cy8ckit-049-4xxx-prototyping-kits) is used here along with the [MiniProg](http://www.cypress.com/documentation/development-kitsboards/cy8ckit-002-psoc-miniprog3-program-and-debug-kit). 
The MiniProg isn't necessary as the PSoC device can be programmed using the bootloader, but I haven't tried that feature yet. 

## Software
A serial communication terminal application is needed to interact with the Signal Generator. I prefer to use Python's PySerial package which comes with an excellent `miniterm` program. It can be installed using `pip` as follows:  
```pip install pyserial```  
And connected to the Signal Generator using the following command:  
On Windows: ```python -m serial.tools.miniterm COM4 115200 -e```  
On Mac: ```python -m serial.tools.miniterm /dev/cu.usbmodem14231 115200 -e```  
  - `COM4` is the port for the PSoC 4 Prototyping kit on my Windows computer and `/dev/cu.usbmodem1431` is the port on my Mac. Use this command to see all available ports: `python -m serial.tools.list_ports`  
  - `115200` is the baud rate. 
  - `-e` enables the echo mode in `minitterm`  


## Commands  
The code has the following three commands built into it, type them in the terminal and hit Enter to see usage formats:
- `help`
- `dds`
