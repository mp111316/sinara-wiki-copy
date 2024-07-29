# Sayma Smart Arbitrary Waveform Generator 

Sayma is a smart arbitrary waveform generator, providing 8 channels of 1.2 GSPS 16-bit DACs (2.4 GHz DAC clock) and 125 MSPS 16-bit ADCs. It consists of an AMC, providing the high-speed digital logic, and a RTM, holding the data converters and analog components.


|PCB | design files | schematics | manual |
|----|--------------|------------|--------|
|Sayma_AMC | [ARTIQ_EE/PCB_Sayma_AMC](https://github.com/sinara-hw/sinara/blob/master/ARTIQ_EE/SAYMA_AMC.pdf) | [here](https://github.com/sinara-hw/sinara/blob/master/ARTIQ_EE/SAYMA_AMC.pdf) | [link](https://github.com/m-labs/sinara/files/1770866/SaymaAMC.pdf) |
|Sayma_RTM | [ARTIQ_EE/PCB_Sayma_RTM](https://github.com/m-labs/sinara/tree/master/ARTIQ_EE/PCB_Sayma_RTM) | [here](https://github.com/m-labs/sinara/blob/master/ARTIQ_EE/Sayma_RTM.pdf) | [link](https://github.com/m-labs/sinara/files/1708297/SaymaRTM.pdf) |

The PCBs are double width, mid height AMC module. 

The schematics and layout are made with Mentor Xpedition. There is a free viewer: [visECAD Viewer](https://www.mentor.com/pcb/downloads/visecad-viewer/). Note that for Sayma v2 [Xpedition won’t be used ](https://github.com/sinara-hw/meta/issues/32#event-2151514176). 

## Sayma AMC
![](images/Sayma_AMC_rev1.0_front.jpg)

## Sayma RTM
![](images/Sayma_RTM_rev1.0_front.jpg)

## Sayma RTM with AFE and clock modules:
![](images/Sayma%20rtm%20top%20with%20moodules.PNG)


# Features

* May be used in a uTCA rack or stand-alone operation with fibre-based DRTIO link
* Analog input and output front-ends provided by plug-in [analog front-end modules](SaymaAFE) (eg BaseMod) for maximum flexibility.
* Extremely flexible [clocking options](SinaraClocking)
* Flexible feedback to SAWG parameters planned. Specification [here](Servo).

## Key AMC Components
* **FPGA**: XCKU040-1FFVA1156C Kintex Ultrascale, 520 I/O, 530K Logic Cells, Speed Grade 1, 20 GTH transceivers (up to 16.3 Gb/s) -- motivation for this FPGA choice is [here](https://github.com/m-labs/sinara/wiki/artiq_hardware#recommendation)
* **DRAM**: MT41K256M16TW-107:P, DDR3, 32 MB x 16 x 8 banks = 4 GB
* **clock recovery**: Si5324 is a precision clock multiplier and jitter attenuator

## Key RTM Components
* **DAC**: AD9154 4-channel high-speed data converter 
    * data rate is 1.2 GS/s at 16-bit
    * clock is up to 2.4 GHz (1x, 2x, 4x and 8x interpolating modes)
    * supports mix-mode to emphasize power in 3rd Nyquist Zone
    * interface is 8-lane JESD204B (subclass 1)
    * power consumption is 2.11 W
    * each Sayma has 2 AD9154 
* **ADC**: AD9656 is a 4-channel high-speed digitizer
    * data rate is 125 MS/s at 16-bit
    * clock is up to 125 MHz
    * 650 MHz analog bandwidth
    * interface is 8-lane, 8 Gb/s per lane, JESD204B (subclass 1)
    * each Sayma has 2 AD9656 
* **clock generation**: (summarized [here](SinaraClocking))
    * Sayma has several distinct clock domains
        * DAC, JESB204B output clock
        * ADC, JESD204B input clock
        * LO for analog mezzanines
    * These clocks may be generated using a low phase noise [Clock Mezzanine](ClockMezzanines) PCB. A single Clock Mezzanine can be shared by several Sayma in a uTCA crate using [Baikal] PCB and an RTM RF backplane. Alternately, each Sayma can have its own distinct Clock Mezzanine (local generation).
* **clock distribution** 
    * HMC7043 SPI 14-Output Fanout Buffer for JESD204B
    * HMC830 SPI fractional-N PLL
* **calibration ADC**: AD7194BCPZ is a 20-bit ADC for monitoring/calibration 

## Transceiver/connector usage

* SFP1: DRTIO downstream
* SFP2: DRTIO downstream
* SATA1: DRTIO upstream (different bitstream probably)
* SATA2 (swapped): DRTIO downstream
* FAT_PIPE1 (FABRICD): DRTIO upstream
* FAT_PIPE2 (FABRICE): not used
* FMC:
  * LA: FMC DIO32: TTL IO

### Front Panel LEDs
Front of board components: SMA USB/button SMA SFP SFP SMA FMC. Several 
LEDs lie under SFPs (left to right). 
- LD3: user defined "SFP2"
- LD6: red if MMC is in error state (set by MMC)
- LD20: LINK_UP (set by MAX24287) 
- LD18: MII1_MODE
- LD2: user defined "SFP2"
- LD5: user defined "SFP1"
- LD19: user defined

### RTM channels
Mapping of SMA connectors to functionality for RTM. 
```
O      
  O    sawg7
O
  O    sawg6
O 
  O    sawg5
O 
  O    sawg4
O
  O    sawg3
O
  O    sawg2
O
  O    sawg1
O 
  O    sawg0
O      input for 100 MHz clock, 10 dBm
```

### Debug Tools	

Sayma_AMC and Sayma_RTM have several RF debug ports. Use low-profile 90-deg adapters for debugging in chassis. 	
* __U.FL__: U.FL to  SMA adapter like the L-COM CA-UFLSBQC20. 	
* __SMP__: SMP to SMA adapter like CentricRF C574-086-12. 	
* __clock__: 1.2 GHz differential clock LVPECL; use 180 deg power splitter from eg MiniCircuits

## MMC Related

### Building OpenMMC Firmware For Sayma
```
mmc-firmware$ make
```

### Flashing MMC
The following steps do not require any physical modifications to Sayma v1 PCB. 
- Hardware: NXP LPCXpresso LPC-Link 2 Rev B, ribbon cable 
- Software: LPCXpresso (obtained from NXP website, Linux or Windows)
- Steps:
    - connect NXP J7 header -- ribbon -- AMC
    - connect USB to PC
        - on Linux: dmesg shows LPC-LINK2… /dev/ttyACM0	
    - create "New Project" for LPC1776. 
    - select program Flash icon (grey on right side)
    - select program Flash memory and file ```build/out/openMMC.axf```
    - no need to specify base address

### Flashing MMC with Flash Magic:
`mmc-firmware/build/out$ arm-none-eabi-objcopy -I binary -O ihex openMMC.bin openMMC.hex`

![](https://user-images.githubusercontent.com/11598020/38621736-c32fa116-3da1-11e8-9725-d01b5da09adb.png)

Flash `openMMC.hex` file generated with command above. Choose last COM port that shows up in Device Manager, when you connect USB to Sayma. Close all other terminals, that have this COM port open.

## MMC Terminal
The fourth serial interface exposed by Sayma over USB is MMC Console. How to use it is discussed [here](https://github.com/sinara-hw/sinara/issues/358#issuecomment-380463815) and [here](https://github.com/sinara-hw/sinara/issues/521#issuecomment-371195293). The MMC terminal works in FlashMagic and Terminalbpp, both on Windows. 

- 115200 8N1
- no hardware handshaking (CTS, RTS disabled)

Note that this does not work under Linux without making a board modification. See [link](https://github.com/sinara-hw/sinara/issues/542). 

## V1 Rework 

Following are white-wire changes identified after boards shipped from WUT to physicists.

- Slow start MOSFET for power. It’s located at the board edge, close to the AMC connector. [link](https://user-images.githubusercontent.com/4325054/48792964-e2bd4e80-ecf5-11e8-89fb-310052b136a4.jpg)

- [second](https://github.com/sinara-hw/sinara/issues/600#issuecomment-440341704) 

- [third](https://github.com/sinara-hw/sinara/issues/600#issuecomment-440342557), close to the RTM connector


