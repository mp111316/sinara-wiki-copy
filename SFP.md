Sinara Core Devices (Kasli, Sayma, Metlino) use SFP modules for several purposes.
- Core Device (eg Kasli) to Ethernet switch
- Synchronization of Core Devices via [DRTIO](https://m-labs.hk/artiq/manual/drtio.html?highlight=tree#using-drtio)

# Core Device to Ethernet switch
Use a transceiver rated for at least 1 Gb data rate. Examples include the following. 

- SFP to Copper RJ45 (1000BASE-T)SFP-GB-GE-T ([fs.com #11773](https://www.fs.com/products/12626.html)) 
    - tested with Kasli v1.0
- SFP to fiber transceiver pair
    - fiber: SM 9/125 OS2 single-mode simplex fiber patch cable with connectors LC/UPC-LC/UPC (not angle polished) (eg [sf.com p/n SM-LCU-LCU-SX-FS-2M-PVC](https://www.fs.com/products/40435.html))
    - 1000Base-X SFP transceiver A: SFP-GE-BX (Tx at 1310 nm Rx at 1490 nm) (eg [sf.com p/n 20184](https://www.fs.com/products/20184.html))
    - 1000Base-X SFP transceiver B: SFP-GE-BX (Tx at 1490 nm Rx at 1310 nm) (eg [sf.com p/n 29895](https://www.fs.com/products/29895.html)) 
    - tested with Kasli v1.0

## [DRTIO](https://m-labs.hk/artiq/manual/drtio.html?highlight=tree#using-drtio) Synchronization

For best performance with clock recovery use single mode bi-directional transceivers with two-channel wavelength division multiplexing (BiDi). The SFP modules at either end of the fiber differ based on the laser diode color and grating configuration. **For DRTIO it is [critical](https://forum.m-labs.hk/d/191-drtio-master-satellite-ping-failure) to use transceiver rated for at least 10 Gb data rate.**  

The following transceivers work as of 7/2021. 
* FS P/N: SFP-10G-BX #36351 :: Cisco SFP-10G-BXU Compatible 10GBASE-BX10-U BiDi SFP+ 1270nm-TX/1330nm-RX 10km DOM LC SMF Transceiver Module
* FS P/N: SFP-10G-BX #36353 :: Cisco SFP-10G-BXD Compatible 10GBASE-BX10-D BiDi SFP+ 1330nm-TX/1270nm-RX 10km DOM LC SMF Transceiver Module
* tested with Kasli v1.1
