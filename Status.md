Following is a table of hardware in the Sinara project along with development status. Development status is tracked for both the hardware and hardware-enabling firmware/software. 

## Hardware Status
Background on the Sinara development process is helpful to understand the hardware status flags. New Sinara hardware progresses through several development steps. Refer to the [Sinara Style Guide](https://github.com/sinara-hw/meta/wiki/StyleGuide) for additional details. 
- The proponent of the new hardware initiates a request for comment (RFQ) at [Sinara meta Issues](https://github.com/sinara-hw/meta/issues).  
  - Advertise the RFQ at [M-Labs Forum](https://forum.m-labs.hk/), email, twitter, etc.
  - In consult with respondents to the RFQ the proponent chooses a hardware project name. 
- The [Warsaw team](https://github.com/sinara-hw/meta/wiki/Team#warsaw-technosystem) typically leads the PCB layout and modeling work. The Warsaw team also creates [new Sinara project repositories](https://github.com/sinara-hw/) upon request and can grant write access to the [sinara-hw](https://github.com/sinara-hw/) GitHub organization.
- The proponent creates a new [high-level wiki page](https://github.com/sinara-hw/meta/wiki), inserts a link into the sidebar and add an entry on the [Sinara Hardware Status](https://github.com/sinara-hw/meta/wiki/Status) page
- The hardware status is
  1) __RFQ__ request for comments
  2) __design review__ community is reviewing schematics and layout tagged as a Revision Candidate (eg [Thermostat releases](https://github.com/sinara-hw/Thermostat/tags)); discussion and bug reports take place in Issues at the hardware repository (e.g. [Thermostat Issues](https://github.com/sinara-hw/Thermostat/issues)) 
  3) __prototype__ prototype has been produced and is being tested by proponent; if bugs are found the design is edited and status reverts to (ii)
  4)  __production__ hardware is sufficiently bug-free to be produced in volume
  5) __discontinued__ 

__WARNING__ Just because Sinara hardware status is Production does not imply that the firmware/software is stable and recommended for routine use. See Firmware/Software status column. 

## Firmware/Software Status

The development of software and firmware to support the configuration and operation of Sinara hardware is tightly coupled to hardware development, but it is considered a logically distinct effort as there may be several software drivers targeting a hardware design. For example,  [Booster](https://github.com/sinara-hw/Booster) has [open and restricted-source](https://github.com/sinara-hw/Booster/wiki) firmware. As such the software and firmware development is pursued in separate git repositories, not in the Sinara hardware repositories.  Links to the corresponding software/firmware are provided in the hardware project wiki page for each project (eg [Thermostat](https://github.com/sinara-hw/Thermostat/wiki) firmware is [here](https://git.m-labs.hk/m-labs/thermostat)). 

### Types of firmware/software support

- Some Sinara hardware requires no firmware or software. 

- Some Sinara hardware designs are stand-alone with respect to ARTIQ. They may require software and firmware for full functionality.   

- Some Sinara hardware is supported by software/firmware elements that enable tight integration with ARTIQ. For instance, Kali operation with ARTIQ depends on [Migen](https://github.com/m-labs/migen/tree/master/migen/build/platforms/sinara), [MiSOC](https://github.com/m-labs/misoc/blob/master/misoc/targets/kasli.py) and [ARTIQ](https://github.com/m-labs/artiq/tree/master/artiq/gateware/targets) integrations. 

#### Status labels

- __none required__ indicates that there is no software/firmware required nor any Migen, MiSOC or ARTIQ integration
- __development__ indicates that the software/firmware is under development 
- __testing__ the software/firmware is available but not yet stable
- __stable__ indicates that there is a stable release which is suitable for routine laboratory use; still, not every bug may be squashed so take a look at open Issues to better understand the status (eg [M-Labs Thermostat firmware Issues](https://git.m-labs.hk/M-Labs/thermostat/issues))
- NA indicates not applicable

## DIOT Status
DIOT is a new form factor for Sinara 3U hardware that includes standardized geometry and backplane. The backplane is thought to be an improvement over the ribbon cables that implement EEM. You can read more about this in an [ECTI 2023 poster](https://github.com/sinara-hw/meta/files/12801670/ECTI_DIOT_RC8.pdf) and [here](https://github.com/sinara-hw/meta/issues/84). As of 7/2024 only a limited number of boards are available that support DIOT. 

|   | Board name    | Board description | HW Status |  Firmware/Software Status  | DIOT |
| - | ------------- | ------------      | --------------        | --------------   | ------- |
| 1 | [Booster](https://github.com/sinara-hw/Booster/wiki) | 8-channel stand-alone RF amplifier |  production | stable | NA |
| 2 | [Sayma AMC](https://github.com/sinara-hw/Sayma_AMC/wiki) | AMC module with Kintex US FPGA, FMC, RTM and 2 SFPs | production | testing | NA |
| 3 | [Sayma RTM](https://github.com/sinara-hw/Sayma_RTM/wiki) | RTM module with 8x DAC, 8x ADC, 4 AFE + clock mezzanines| production | testing | NA |
| 4 | [Metlino](https://github.com/sinara-hw/Metlino/wiki) | MCH Tongue 3&4 module with 3 SFPs, 2 VHDCI and Kintex US FPGA|  production  |  testing | NA |
| 5 | [uTCA micro-chassis](https://github.com/gkasprow/MicroTCA-chassis/wiki) | uTCA micro-chassis for single AMC + RTM  | v1.1 proto production  | new Linux MMC development | NA |
| 6 | [Kasli](https://github.com/sinara-hw/Kasli/wiki) | 3U  Artix FPGA and up to 8 extension modules|  production | stable | Yes |
| 7 | [DIO-BNC](https://github.com/sinara-hw/DIO_BNC/wiki) | 3U module with 8 BNC and LVTTL@50Ohm |  production | stable | not planned |
| 8 | [Zotino](https://github.com/sinara-hw/Zotino/wiki)| 3U module - 32 channel +/- 12V DAC |  production | stable | planned |
| 9 | [DIO-RJ45](https://github.com/sinara-hw/DIO_RJ45/wiki) |3U module - 4x RJ45 connectors each with 4 LVDS bidir ports |  production | stable | planned |
| 10 | [DIO_SMA](https://github.com/sinara-hw/DIO_SMA/wiki) | 3U module with 8 SMA and LVTTL@50Ohm |  production | stable | use DIO MCX |
| 11 | [VHDCI Carrier](https://github.com/sinara-hw/VHDCI_Carrier/wiki) | VHDCI carrier for 8 3U modules | production | stable | NA |
| 12 | [Sampler (Novo)](https://github.com/sinara-hw/Sampler/wiki) |  3U module with multichannel ADC | production | stable | planned MCX version |
| 13 | [Urukul](https://github.com/sinara-hw/Urukul/wiki) | 3U module with 4x  1 GS/s DDS |   production | stable | planned |
| 14 | [Kasli-SOC](https://github.com/sinara-hw/Kasli-SOC/wiki) | ZynQ 7 version of Kasli controller | production | testing | planned |
| 15 | PCB_AMC_SATA | adapter between Sayma AMC and several SATA ports | working, discontinued | none required |  NA |
| 16 | PCB_eRTM15_ Baikal | Clock distribution module for uRFB | schematics and layout done, discontinued |  |  NA |
| 17 | [Mordovia_MCH_CLK](https://github.com/sinara-hw/Mordovia_MCH_CLK/wiki) | Triple clock fanout that provides access to M-LVDS and TELCOM clocks | v1.1 development | none required | NA |
| 18 | [BaseMod](https://github.com/sinara-hw/BaseMod/wiki) | AFE for Sayma RTM |  production | stable | NA |
| 19 | PCB_mezzanine_ analog_template | AFE template/test board for Sayma RTM | proto delivered | none required | NA |
| 20 | [MixMod](https://github.com/sinara-hw/MixMod/wiki) | upconversion AFE for Sayma RTM | designed, discontinued | discontinued | NA |
| 21 | PCB_mezzanine_ clock | clock module for Sayma RTM | discontinued |  | NA |
| 22 | PCB_mezzanine_ clock_template | clock module template/test board for Sayma RTM | working, discontinued | none required | NA |
| 23 | PCB_RTM_ loopback | test module for Sayma AMC GTX characterisation | working, discontinued | none required | NA |
| 24 | [CompactPCISerial _EEM_Adapter ](https://github.com/sinara-hw/CompactPCISerial_EEM_Adapter/wiki) | Compact PCI Serial to EEM adapter. Enables utilisation of existing EEM ecosystem in standard CPCIS chassis | proto tests | none required | NA |
| 25 | PCB_RTM_SATA | SATA breakout module for Sayma AMC | working, discontinued | none required  | NA |
| 26 | [Grabber](https://github.com/sinara-hw/Grabber/wiki)| 3U module with Camera Link | production | stable | planned |
| 27 | [SATA-SFP](https://github.com/sinara-hw/SATA_SFP/wiki) | media converter | production | stable | NA |
| 28 | [Shuttler](https://github.com/sinara-hw/Shuttler/wiki)| FMC card with 16x 125 MSPS 14-bit DAC | prototype debugging | development | Yes |
| 29 | [Thermostat](https://github.com/sinara-hw/Thermostat/wiki) | two channel precise TEC temperature controller |  production | usable but not yet stable  | NA |
| 30 | [Banker](https://github.com/sinara-hw/Banker/wiki) | 3U module with 128 channel 3.3V/5V digital IO with versatile IO extenders |  production | stable | planned |
| 31 | [Stabilizer](https://github.com/sinara-hw/Stabilizer/wiki) | 3U  module, 2-channel microcontroller servo with EEM and Ethernet based on STM32 CPU | production | stable | planned |
| 32 | [Fastino](https://github.com/sinara-hw/Fastino/wiki) | 3U module with 32-channel, 16bit, 3MS/s per channel DAC card | production | stable | Yes |
| 33 | [Mirny](https://github.com/sinara-hw/mirny/wiki) | 3U module: 4-channel microwave synthesizer | production | stable | planned |
| 34 | [Humpback](https://github.com/sinara-hw/Humpback/wiki) | 3U module: General purpose STM32/ESP32/OrangePi/Beaglebone baseboard with FPGA |  working, discontinued |  | planned |
| 35 | [IDC_HD68_Adapter](https://github.com/sinara-hw/IDC_HD68_Adapter/wiki) | IDC to HD68 adaper for Zotino |  production | none required | NA |
| 36 | [RSOC-AMC](https://github.com/sinara-hw/RFSOC-AMC/wiki) | AMC module with octal 4GS/s ADC + 6GS/s DAC |  testing | development | NA |
| 37 | [Clocker](https://github.com/sinara-hw/Clocker/wiki) | Low noise clock distribution module | production | none required | NA |
| 38 | [Kasli CPCIS adapter](https://github.com/sinara-hw/CompactPCISerial_Kasli_Adapter) | DIOT 220mm adapter for Kasli | proto working, replaced by KASLI-DIOT | none required | NA |
| 39 | [Pounder](https://github.com/sinara-hw/Pounder/wiki) |  PDH lock signal generator - Stabilizer mezzanine | production | testing | planned |
| 40 | [Zapper](https://github.com/sinara-hw/Zapper/wiki) |  high-voltage PZT driver | v1.0 produced and tested | testing | planned |
| 41 | [SMA_IDC_Adapter](https://github.com/sinara-hw/SMA_IDC_Adapter/wiki) |  4HP SMA adapter for Zotino & Banker | production | none required  | NA |
| 42 | [BNC_IDC](https://github.com/sinara-hw/BNC_IDC/wiki) | 8HP Adapter for routing analog potentials / digital signals from Zotino/Banker IDC headers to BNC | production | none required | NA |
| 43 | [DIO_MCX_16](https://github.com/sinara-hw/DIO_MCX/wiki) | 16 channel 4HP fast DIO | production | none required | planned |
| 44 | [Stabilizer Piezo Driver](https://github.com/sinara-hw/Stabilizer_Piezo_Driver/wiki) | 2 channel HV piezo driver | proto working   | none required | NA |
| 45 | [Phaser](https://github.com/sinara-hw/Phaser/wiki) | 2 channel 1GSPS AWG/DDS + 2 channel 5MSPS ADC  | production | stable | planned |
| 46 | [Fast servo](https://github.com/sinara-hw/Fast_Servo/wiki) | Low latency + FPGA ADC/DAC servo | proto working | development | planned |
| 47 | [Banker_EDGE _2_DSUB](https://github.com/sinara-hw/Banker_EDGE_2_DSUB) | Banker DSUB extension for DIN rail | tested, ready for production  | none required | NA |
| 48 | [Banker_EDGE _2_BNC](https://github.com/sinara-hw/Banker_EDGE_2_BNC) | Banker 8xBNC extension for DIN rail | tested, ready for production  | none required | NA |
| 47 | [Banker_EDGE _2_SMA](https://github.com/sinara-hw/Banker_EDGE_2_SMA) | Banker 8xSMA extension for DIN rail | tested, ready for production  | none required | NA |
| 48 | [Banker _VHDCI_2_EDGE](https://github.com/sinara-hw/Banker_VHDCI_2_EDGE) | Banker VHDCI to DIN extension baseboard | tested, ready for production  | none required | NA |
| 49 | [Banker _VHDCI_2_EDGE_Buffered](https://github.com/sinara-hw/Banker_VHDCI_2_EDGE_Buffered) | Banker VHDCI to DIN buffered extension baseboard | tested, ready for production  | none required | NA |
| 50 | [Driver](https://github.com/sinara-hw/Driver/wiki) | Low noise current source for laser diodes | replaced by Kirdy | development | obsolete |
| 51 | [Line trigger](https://github.com/sinara-hw/Line_trigger/wiki) | Low jitter line trigger box | production | none required | NA |
| 52 | [Almazny](https://github.com/sinara-hw/Almazny/wiki) | 12GHz mezzanine for Mirny | production | development | planned |
| 53 | [Photodiode Amplifier](https://github.com/sinara-hw/Photodiode_amplifier/wiki) | general purpose photodiode amplifier for AI-ARTIQ | discontinued | none required | NA |
| 54 | [HV AMP 8CH](https://github.com/sinara-hw/HV_AMP_8CH/wiki) | +/-200V 1MHz 8 channel amplifier | production |  testing | NA |
| 55 | [DIO MCX 16 Isolated](https://github.com/sinara-hw/DIO_MCX_Isolated) | 16 channel fast DIO with individually isolated MCX IOs | ready for production | none required | Yes |
| 56 | [AUX PSU ](https://github.com/sinara-hw/AUX_PSU/wiki) | 3-channel programmable low noise supply | v1.1 production | none required | NA |
| 57 | [Shuttler Remote AFE](https://github.com/sinara-hw/Shuttler/wiki) | 16-channel low noise AFE for shuttler | production | development | NA |
| 58 | [AC power module](https://github.com/sinara-hw/EEM_PWR_MOD_AC/wiki) | 400W EEM power module | production | none required | NA |
| 59 | [Digital Photodiode](https://github.com/sinara-hw/DiPho/wiki) | Digital versatile photodiode | prototype debugging | development | NA |
| 60 | [SiLPA HE](https://github.com/sinara-hw/SiLPA_HE/wiki) | Simple high-efficiency wideband RF amplifier | RnD  | development | planned |
| 61 | [SiLPA HL](https://github.com/sinara-hw/SiLPA_HL/wiki) | Simple high-linearity wideband RF amplifier | proto tests | development  | Yes |
| 62 | [EEM FMC Carrier](https://github.com/sinara-hw/EEM_FMC_Carrier/wiki) | low cost EEM FMC HPC carrier | production | development | Yes |
| 63 | [Stamper](https://github.com/elhep/FMC_ADC100M_10B_TDC_16cha/wiki) | 16-channel TDC with ADC | v1.0 delivered, v1.1 in production | testing | Yes |
| 64 | [Metlino_Fabric&Timing](https://github.com/sinara-hw/FMC_Metlino_Fabric-Timing) | FMC adapter giving Metlino access to Fabric E and Telecom clocks | RnD | none required |  NA |
| 65 | [HV AMP 32](https://github.com/sinara-hw/HVAMP_32/wiki) | 8-channel booster amplifier for Zotino & Fastino | production | none required | Yes |
| 66 | [ Waver FMC ](https://github.com/sinara-hw/Waver_FMC/wiki) | 4-channel DC-coupled 10Vpp 1.5GS/s Arbitrary Waveform Generator | tested, ready for production | RnD | Yes |
| 67 | [ ZHL simple RF Amplifier ](https://github.com/sinara-hw/ZHL_RF_AMP_3U/wiki) | simple, 3U size MiniCircuit ZHL amplifier |  production | none required | not planned |
| 68 | [ IDC MCX adapter ](https://github.com/sinara-hw/IDC_MCX_Adapter/wiki) | 32-channel IDC to MCX adapter / Zotino/Fastino mezzanine | production | none required | NA |
| 69 | [ FMC-DIO-32LVDS ](https://ohwr.org/project/fmc-dio-32chlvdsa/wikis/home) | Universal 32-channel bi-directional LVDS card | production | stable | Yes |
| 70 | [Booster_HL](https://github.com/sinara-hw/Booster/wiki) | High linearity 8-channel stand-alone RF amplifier |  production | stable | NA |
| 71 | [RFSOC-SAWG](https://github.com/sinara-hw/RFSOC_SAWG/discussions) | High speed 10GS/s AWG in EEM/DIOT form factor | ready for prototyping | RFQ | Yes |
| 72 | [Floating HV PSU](https://github.com/sinara-hw/PSU_HV_ISOL/wiki) | FLoating (10kV) double HV PSU | proto tests | RnD | Yes |
| 73 | [STM System Board](https://github.com/sinara-hw/STM_Sys_Board/wiki) | Low cost STM32 DIOT system board | proto tests | RnD | Yes |
| 74 | [RF modulator](https://github.com/sinara-hw/modulator/wiki) | Versatile DC to 1GHz double modulator | proto production | none required | planned |
| 75 | [Thermostat EEM](https://github.com/sinara-hw/Thermostat_EEM/wiki) | Thermostat with 4 TECs and eight sensor channels in EEM form factor | production | useful but not stable | planned |
| 76 | [DIO-LVTTL-IDC-Tester](https://github.com/sinara-hw/DIO_TTL_IDC-tester/wiki) | Simple DIO & Controller/Tester module | production | none required | NA |
| 77 | [Fastino MUX 32:2](https://github.com/sinara-hw/Fastino_mux_32-2) | 32 channel DIOT/EEM/Stand alone mux for Fastino/Zotino  | proto tests | development | Yes |
| 78 | [DIOT extender card](https://github.com/sinara-hw/DIOT_SYS_extender_card) | DIOT system/peripheral board extender debug card | ready for prototyping | none required | Yes |
| 79 | [SPE router](https://github.com/sinara-hw/SPE_router) | Single Pair Ethernet router for DiPho | RnD | development | NA |
| 80 | [HD68 to BNC breakout](https://github.com/sinara-hw/HD68_BNC_Breakout) | HD68 to BNC/MCX stand-alone/3U adapter | production | none required | NA |
| 81 | [Magneto](https://github.com/sinara-hw/Magneto/wiki) | DC power current source for electromagnets | PCB assembly | RnD  | Yes |
| 82 | [VHF amplifier](https://github.com/sinara-hw/VHF_Amp/wiki) | 10W RF amplifier with modulator input | PCB review | none required | Yes |
| 83 | [HV DAC](https://github.com/sinara-hw/HV_DAC/wiki) | 1ppm stable HV DAC | SCH review | RnD | NA |
| 84 | [HV DAC REF](https://github.com/sinara-hw/VREF/wiki) | 0.5ppm reference card with compensation | RnD | none required  | Yes |
| 85 | [12G AWG](https://github.com/sinara-hw/12G_AWG/wiki) | 12GS/s quad channel FMC AWG | RnD  | RnD | Yes |
| 86 | [Fast PID controller](https://github.com/sinara-hw/UF_Servo/wiki) | 60MHz, <10ns delay PID controller | RnD | RnD | NA |
| 87 | [Wenzel Clock](https://github.com/sinara-hw/Wenzel_ref/wiki) | Low noise frequency reference | prototype testing | none required | Yes |
| 88 | [Kirdy](https://git.m-labs.hk/sinara-hw/kirdy) | laser current driver | prototype | testing | ? |

