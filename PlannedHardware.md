This page contains hardware projects that are being discussed and considered to become part of Sinara. These projects range from ideas waiting for further specification and funding to well-advanced physicist-designed projects that haven't been professionally developed/tested yet.  

This page may not be totally up to date so you should also check the [Meta Issues](https://github.com/sinara-hw/RFSOC-AMC/wiki) for latest hardware development discussions and to pitch your own ideas.

# Stamper

Provisional name for a TDC EEM. 

Discussion [here](https://github.com/sinara-hw/meta/issues/9).

WUT designed a [16ch TDC+DAC](https://github.com/elhep/FMC_ADC100M_10B_TDC_16cha/wiki) for a different project. ARTIQ support is planned.

# Ingester
- Fast uTCA ADC
- >=100MSPS. 1GSPS?
- 8 channels?

# Blaster
- 12 GSPS SAWG RTM card for direct microwave synthesis for sc qubits ([issue #183](https://github.com/m-labs/sinara/issues/183))
- Details [here](https://github.com/sinara-hw/sinara/wiki/Blaster)
- Development of [RFSOC-AMC](https://github.com/sinara-hw/RFSOC-AMC/wiki) has overlap. Details [here](https://github.com/sinara-hw/RFSOC-AMC/issues/1)

# Thermometer: Temperature Logger

- Non-real time (?)
- Eurocard size
- Controlled via ethernet: RJ45 jack on front panel; microprocessor (same rust/smoltcp stack as IonPack?); simple, SCPI-like text-based interface
- Same power connector/power supply as Kasli (connector on front panel)
- Same EEPROM as EEMs for serial number, etc
- Maybe combine with temperature controller board
- what kind of sensor: 10k thermistor? PT100? DS1820
- What accuracy/stability?
- 4+ inputs

Much overlap with [Thermostat_EEM](https://github.com/sinara-hw/Thermostat_EEM/wiki): 4ch Temp Controller

# Laser diagnostics

- Port Oxford WaND to Kasli. (Current version here https://github.com/OxfordIonTrapGroup/wand)
- Multi channel laser diagnostics 
- Multiple lasers connected via a multi-mode fiberised optical switch (switch controlled via ethernet by Kasli)
- Digitises Optical Spectrum Analyser outputs (OSA)
- Logs wavelength on wavemeter
- Simple feedback loops to lock laser to wavemeter
- Nice GUI
- Detect lasers starting to go multi-mode?


# Driver: Laser diode current controller

- Details [here](https://github.com/sinara-hw/Driver/issues/1)


# Simple RF Amplifier

- Details [here](https://github.com/sinara-hw/meta/issues/50)
