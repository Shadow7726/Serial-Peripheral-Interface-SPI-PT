## SPI Continuous Sniffing with Flashrom and Bus Pirate

While Bus Pirate itself allows SPI sniffing, combining it with Flashrom offers advantages like continuous logging and potentially higher speeds. Here's how to set up and use them for SPI sniffing:

### Hardware Setup:

1. **Connect the Bus Pirate to your computer and target device:**
    - Use the correct SPI pinout based on your target device's datasheet. Usually, this involves connecting:
        - MOSI (Master Out Slave In) from Bus Pirate to MOSI pin of target device
        - MISO (Master In Slave Out) from Bus Pirate to MISO pin of target device
        - SCK (Serial Clock) from Bus Pirate to SCK pin of target device
        - CS (Chip Select) from Bus Pirate to CS pin of target device (might require multiple CS lines for devices with multiple chips)
        - GND from Bus Pirate to GND of target device

2. **Power both devices:** Ensure both Bus Pirate and your target device have proper power supply.

### Software Setup:

1. **Install Flashrom:** Download and install Flashrom for your operating system from [flashrom.org](https://flashrom.org/).

2. **Identify SPI settings:** Determine the SPI clock speed, polarity, phase, and number of CS lines used by your target device. Consult its datasheet for these details.

### Sniffing with Flashrom:

1. **Open a terminal window.**

2. **Enter the following command, replacing placeholders with your settings:**

   ```bash
   flashrom -p buspirate <polarity>:<phase>:<speed>:<cs> -r /dev/null
   ```

   - `-p buspirate`: Specifies the programmer to use (Bus Pirate)
   - `<polarity>`: SPI clock polarity (0 for idle low, 1 for idle high)
   - `<phase>`: SPI clock phase (0 for middle sample, 1 for end sample)
   - `<speed>`: SPI clock speed in Hz (e.g., 1000000 for 1MHz)
   - `<cs>`: Number of CS lines to use (e.g., 1 for single chip, 2 for two chips)
   - `/dev/null`: Replace with a file path to save captured data if desired (optional)

3. **Press Enter to start sniffing.** Flashrom will continuously read data from the MISO line and discard it by default (writing to `/dev/null`).

4. **(Optional) Save captured data:** If you want to save the sniffed data, replace `/dev/null` in the command with a desired file path (e.g., `sniffed_data.bin`).

5. **Stop sniffing:** Press `Ctrl+C` in the terminal window to stop sniffing.

### Additional Notes:

- Flashrom might offer higher SPI speeds compared to Bus Pirate's built-in SPI mode.
- The sniffed data will be in raw binary format. You might need additional tools or knowledge of the SPI protocol to interpret it.
- Consider adjusting capture file size or using filters if dealing with large amounts of data.
- Always refer to the Flashrom documentation and Bus Pirate manual for more advanced usage and troubleshooting.

## Method 2

Here is an example of using a Bus Pirate with flashrom to continuously sniff SPI flash chip traffic:

1. **Connections:** Wire up the SPI flash chip to the Bus Pirate as per the table in the previous example. Ensure the chip is powered.

2. **Enter sniffing mode:**

   ```bash
   sudo bp-spi -m  
   > SNIF
   ```

   This puts the Bus Pirate in SPI sniffing mode.

3. **Start continuous sniffing:**

   ```bash
   > STREAM
   ```

   This will start streaming all SPI traffic detected by the Bus Pirate over the serial connection.

4. **In a new terminal, use flashrom to generate traffic:**

   ```bash
   sudo flashrom -p buspirate_spi:dev=/dev/ttyUSB0,spispeed=1M -r flash.dump
   ```

   This will read the flash chip contents using the Bus Pirate, which gets sniffed.

5. The first terminal will show the raw SPI commands and data being exchanged between flashrom and the chip.

6. **To stop,** press Ctrl+C in both terminals. 

So in summary:

- Use `bp-spi` sniffing mode and `STREAM` command to continuously output SPI traffic
- In another terminal, use flashrom to generate SPI reads/writes 
- Monitor the raw SPI commands and data on the sniffing Bus Pirate output

This allows you to non-intrusively see all the SPI flash traffic for analysis and debugging.
```
---

