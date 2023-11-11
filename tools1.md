# Pentesting SPI 

- ## Recon
    - Identify SPI Chips
        - Hardware Tools: Multimeter, Oscilloscope
        - Software Tools: Datasheets
    - Get Datasheets
        - Software Tools: Manufacturer websites
    - Map Pins to PCB
        - Hardware Tools: Multimeter, Oscilloscope

- ## Sniffing
    - Use Logic Analyzer
        - Hardware Tools: Saleae, Total Phase Beagle 
    - Tap SPI Lines
        - Hardware Tools: Test clips, Hookup wires
    - Sniff Unencrypted Data
        - Software Tools: Wireshark, Saleae

- ## Memory Extraction
    - Identify Memory Chip
        - Hardware Tools: Multimeter
        - Software Tools: Datasheets
    - Use Flash Dumper
        - Hardware Tools: DediProg, CH341A
        - Software Tools: Flashrom, OpenOCD
    - Dump Firmware
    - Extract Keys/Data

- ## Fault Injection
    - Use Glitching Tool
        - Hardware Tools: ChipWhisperer, FaceDancer
    - Target SPI Lines
    - Disrupt Communications
    - Corrupt Firmware/Data

- ## Physical Tampering
    - Decapsulate Chips
        - Hardware Tools: Fuming nitric acid
    - Use Microprobing
        - Hardware Tools: Microprobing workstation
    - Directly Access Buses

- ## Side-Channel Analysis  
    - Use SCA Tools
        - Hardware Tools: ChipWhisperer CW305
    - Capture Power Traces
    - Extract Encryption Keys
        - Software Tools: ChipWhisperer Analyzer

- ## Backdooring Firmware
    - Dump Firmware
        - Hardware Tools: DediProg, CH341A
        - Software Tools: Flashrom, OpenOCD 
    - Modify Firmware
        - Software Tools: Hex editors, IDA Pro
    - Write Backdoored Version
        - Hardware Tools: DediProg, CH341A
        - Software Tools: Flashrom, OpenOCD
