There were several discussions about possible backplane specification. Compact PCI Serial (CPCIS) standard seems to fit the EEM ecosystem quite nicely.
There are however several constraints:
- The CPCIS specification defines slots as 4HP only, this means that 8HP EEM modules would waste precious slots or would have to be modified to support [MCX connectors](https://github.com/sinara-hw/Sampler/issues/13).
- Another is I2C support. The CPCIS standard defines common I2C/SMBus across the backplane, EEM assumes individual buses between modules and the carrier board.
- CPCIS defines boards as 160mm long but existing EEM modules are also 160mm long, so all of them would have to support CPCIS connectors which makes them incompatible with the existing EEM ecosystem. Dual-connector boards are possible but can be implemented only on the new product releases. However both Schroff and CERN DI/OT offers 220mm version of CPCIS
- we have 8 LVDS and 16 LVDS (dual EEM) modules. Both modes need to be supported.

CERN plans to implement a slightly modified CPCIS chassis for their [Distributed IO Tier](http://accelconf.web.cern.ch/AccelConf/icalepcs2017/posters/thpha071_poster.pdf) system. The idea is to unify an essential part of the accelerator instrumentation. The only modification to existing CPCI backplane is the assembly of the backplane on 220mm depths. Such modified chassis can be ordered directly from [Schroff nVent](https://schroff.nvent.com/en/schroff/24579-416). The user can also modify it by using longer guide rails.
The 24579-416 backplane has additional space that can be used for the installation of DIO modules or adapters using ribbon cables with IDC connectors.
CERN also developed custom CPCIS components that better match their need:
- radiation hard 100W power supply, compatible with CPCIS specification
- 84HP backplane compatible with CPCIS chassis, utilizing 8x 6HP or 8x 4HP CPCIS modules. Two standard 8HP PSUs are used.
- Open source backplane and chassis were already developed: [CPCIS backplane and chassis](https://ohwr.org/project/diot-crate-hw/wikis/home)
- Controllers based on Rad-Tolerant FPGAs and standard SoCs like Zynq.

Their goals seem to be nearly identical to ours. To overcome the constraints we propose following CPSIs ecosystem:
- standard CPCIS chassis with backplane mounted on 220mm depth. The Power supply has a dedicated backplane mounted on 160mm.
- P1 connector is used to route 8 LVDS signals + 4 of second channel LVDS signals. P6 is used to route the remaining 4  of second channel LVDS signals. CERN needs to transfer MGT signals as well. 
- Existing EEM modules can be used in such 220mm chassis with [Adapter](https://github.com/sinara-hw/CompactPCISerial_EEM_Adapter/wiki).
- I2C access will be ensured by using PCI_EN lines which are dedicated to every CPCIS slot. Each module has 220Ohm pulldown to GND on PCI_EN line. The same line is used to enable analog multiplexer that connects EEM I2C bus with the backplane I2C bus. The controller will first probe the status of the line with a weak pull-up. If the low state is detected, it will overdrive the line with 3.3V signal and read the unique ID and board FRU content that describes module features like a unique name. The same signal is used to enter the debug mode. Each module equipped with FPGA will connect their JTAG pins to dedicated IO lines. The Controller then becomes the JTAG controller.
- to support both single EEM and dual EEM modules, the CPCIS Adapter module will have 2 connectors. Lower, P1 for first 8 + 2 LVDS links and upper, P6 for next 6 LVDS links.
- DRTIO clock can be distributed using a dedicated backplane line foreseen for the PCI clock distribution. Every adapter can convert it to the single-ended mode and route it to the MMCX connector. The EEM modules that need that clock can source it either from the Clocker module or from the adapter depending on required noise performance. Some modules already have dedicated clock connector (Samtes hermaphroditic connector)
- Existing 8HP modules can be used with CPCIS Adapter on the rightmost slot without wasting CPCIS slots. Any other position wastes one CPCIS slot. This can be mitigated within the Controller design.
- Dual channel (16 LVDS) modules are supported in every slot, but not all slots have the full support of the controller. Existing Kasli controller would support only 4 dual channel slots. The [ZU7 System board](https://ohwr.org/project/diot-sb-zu/wikis/home) supports dual channel configuration for all slots.
- The controller can be based on the existing Kasli v2.x module with an attached dedicated adapter board that routes all 12 IDC connectors to the backplane connector. There are two Kasli adapters available, one which routes 12 EEM slots to 4 double + 4 single; second that routes all EEM slots to 6 double ones.
- The ZynQ controller that is currently [being specified](https://github.com/sinara-hw/meta/issues/29) would follow the same IDC connector pinout to make use of identical CPCIS adapter as Kasli does.
- The ZynQ controller developed by CERN can be used natively. It will provide the FMC connector and larger SoC.


