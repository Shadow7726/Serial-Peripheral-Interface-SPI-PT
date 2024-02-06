# Pentesting SPI

# References for Hardware Hacking and SPI Attack Surface

- [Hardware Attack Surface: SPI](https://payatu.com/wp-content/uploads/2022/12/c15.pdf)
- [HARDWARE HACKING 101: INTERFACING WITH SPI](https://riverloopsecurity.com/blog/2020/02/hw-101-spi/)
- [Dumping the Firmware from the Device Using Buspirate - SPI](https://www.iotpentest.com/2019/06/dumping-firmware-from-device-using.html)
- [Analyzing SPI (Serial Peripheral Interface)](https://nse.digital/pages/guides/hardware/spi.html)
- [Write-Up: SPI Flash for Bug Bounty Hunters](https://www.bugcrowd.com/resources/levelup/writeup-spi-flash-for-bug-bounty-hunters/)
- [SPI-Dump Flash Bus Pirate + flashrom](https://book.hacktricks.xyz/todo/hardware-hacking/spi)
- [An Introduction to Hardware Hacking](https://www.cyberark.com/resources/threat-research-blog/an-introduction-to-hardware-hacking)
- [Hardware-Hacking: Lifting Firmware](https://rift.stacktitan.com/lifting-firmware-part-one/)
- [Hardware-Hacking: Arduino R4 and a Microwire EEPROM](https://rift.stacktitan.com/hardware-hacking-arduino-r4-eeprom-and-microwire/)
- [Hack IoT Devices - Embedded Exploitation](https://blog.attify.com/hack-iot-devices-embedded-exploitation/)
- [Introduction to Hardware Hacking - Abricto Security](https://abrictosecurity.com/introduction-to-hardware-hacking-part-1/)
- [Hardware Hacking with the Beaglebone (Bl|H)ack](https://hardwear.io/document/Hardware-Hacking-with-the-Beaglebone-B-Hack.pdf)
- [Exploiting Embedded APIs by Dumping Firmware](https://danaepp.com/exploiting-embedded-apis-by-dumping-firmware)
- [Intro To Hardware Hacking - Dumping Your First Firmware](https://hex0punk.com/posts/intro-hw-hacking/)
- [Introduction to IoT Hardware Hacking - Hackers Arcade](https://hackersarcade.medium.com/introduction-to-iot-hardware-hacking-ca1d8adeebcb)
- [SPI and I2C hacking](https://hackyourmom.com/en/osvita/chastyna-8-zlom-aparatnoyi-chastyny-systemy-spi-ta-i2c/)
- [A-Z SPI Hacking Step by Step](https://jcjc-dev.com/2016/04/08/reversing-huawei-router-1-find-uart/)



This format includes the titles of the resources along with the links. You can copy and paste this format into your Markdown document, making it easier to refer to these resources.
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
