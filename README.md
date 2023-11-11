# Pentesting SPI

| Area | Steps | Hardware Tools | Software Tools |
|-|-|-|-|  
| Recon | Identify SPI Chips | [Multimeter](https://www.keysight.com/en/pd-1985909/keysight-digital-multimeters?cc=US&lc=eng), [Oscilloscope](https://www.tek.com/oscilloscope/mso5000-mixed-signal-oscilloscope-series) | [Datasheets](https://www.alldatasheet.com) |
|  | Get Datasheets | | [Manufacturer Websites](https://www.microchip.com/design-centers/memory) |
|  | Map Pins to PCB | [Multimeter](https://www.keysight.com/en/pd-1985909/keysight-digital-multimeters?cc=US&lc=eng), [Oscilloscope](https://www.tek.com/oscilloscope/mso5000-mixed-signal-oscilloscope-series) | |
| Sniffing | Use Logic Analyzer | [Saleae](https://www.saleae.com), [Total Phase Beagle](https://www.totalphase.com/protocols/spi/) | [Wireshark](https://www.wireshark.org/), [Saleae](https://www.saleae.com) |  
|  | Tap SPI Lines | [Test Clips](https://www.adafruit.com/product/1003), [Hookup Wire](https://www.adafruit.com/product/1954) | |
|  | Sniff Unencrypted Data | | [Wireshark](https://www.wireshark.org/), [Saleae](https://www.saleae.com) |
| Memory Extraction | Identify Memory Chip | [Multimeter](https://www.keysight.com/en/pd-1985909/keysight-digital-multimeters?cc=US&lc=eng) | [Datasheets](https://www.alldatasheet.com) |
|  | Use Flash Dumper | [DediProg](https://www.dediprog.com/), [CH341A](https://www.amazon.com/GarFoo-Programmer-Flashing-kkmoon-Raspberry/dp/B0939VVZRB?tag=krtosi-20) | [Flashrom](https://flashrom.org/Flashrom), [OpenOCD](https://xpack.github.io/openocd/) | 
|  | Dump Firmware | | |   
|  | Extract Keys/Data | | |
| Fault Injection | Use Glitching Tool | [ChipWhisperer](https://www.newae.com/tools/chipwhisperer), [FaceDancer](https://github.com/bishopfox/facedancer) |  |
|  | Target SPI Lines |  |  |  
|  | Disrupt Communications |  |  |
|  | Corrupt Firmware/Data |  |  |
| Physical Tampering | Decapsulate Chips | [Fuming Nitric Acid](https://www.sigmaaldrich.com/US/en/product/aldrich/438073) |  |  
|  | Use Microprobing | [Microprobing Station](https://www.saygus.com/process-analysis/cavity-chemical-decapsulation-microprobing/) |  |
|  | Directly Access Buses |  |  |
| Side-Channel Analysis | Use SCA Tools | [ChipWhisperer CW305](https://www.newae.com/tools/chipwhisperer-cw305-soc-fpga-board) |  |
|  | Capture Power Traces |  |  |   
|  | Extract Encryption Keys |  | [ChipWhisperer Analyzer](https://wiki.newae.com/ChipWhisperer/Main#ChipWhisperer_Analyzer) |
| Backdooring Firmware | Dump Firmware | [DediProg](https://www.dediprog.com/), [CH341A](https://www.amazon.com/GarFoo-Programmer-Flashing-kkmoon-Raspberry/dp/B0939VVZRB?tag=krtosi-20) | [Flashrom](https://flashrom.org/Flashrom), [OpenOCD](https://xpack.github.io/openocd/) |
| | Modify Firmware | | [Hex Editors](http://www.softpedia.com/get/Programming/Other-Programming-Files/Hex-Editors.shtml), [IDA Pro](https://www.hex-rays.com/ida-pro/) | 
| | Write Backdoored Version | [DediProg](https://www.dediprog.com/), [CH341A](https://www.amazon.com/GarFoo-Programmer-Flashing-kkmoon-Raspberry/dp/B0939VVZRB?tag=krtosi-20) | [Flashrom](https://flashrom.org/Flashrom), [OpenOCD](https://xpack.github.io/openocd/) |
