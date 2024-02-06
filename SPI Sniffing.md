
## SPI Sniffing with Bus Pirate Commands

The Bus Pirate is a versatile tool that can be used for various tasks, including SPI sniffing. Here's a guide on how to use Bus Pirate commands for SPI sniffing:

**Before you begin:**

- Ensure you have the latest Bus Pirate firmware and software installed.
- Connect the Bus Pirate to your computer and target device according to the SPI pin layout.
- Identify the SPI clock speed, polarity, phase, and CS pin of your target device.

**Sniffing Modes:**

There are two main ways to perform SPI sniffing with Bus Pirate:

**1. Terminal Mode:**

- **Setup:**
  - Enter `SPI` mode on the Bus Pirate.
  - Configure the SPI settings using commands like:
    - `SPISpeed <speed>` (e.g., `SPISpeed 1000000` for 1MHz)
    - `SPIPolarity <polarity>` (0 for idle low, 1 for idle high)
    - `SPIPhase <phase>` (0 for middle sample, 1 for end sample)
    - `CSPin <pin number>` (e.g., `CSPin 3`)

- **Start Sniffing:**
  - Use `SPIRead` or `SPIWrite` commands to capture data.
    - `SPIRead`: Reads data from the MISO pin.
    - `SPIWrite <data>`: Writes data to the MOSI pin.
  - Use `SPIReadCont` for continuous sniffing.
  - Press `ESC` to stop sniffing.

**2. SPISniffer Utility:**  [Bus Pirate binary SPI sniffer utility documentation](http://dangerousprototypes.com/docs/Bus_Pirate_binary_SPI_sniffer_utility)

- **Download and run the SPISniffer utility from Dangerous Prototypes website.**  
- **Connect the Bus Pirate to your computer and run the utility.**
- **Select the COM port and set the baud rate.**
- **Choose the "Bus Pirate OLS mode".**
- **Configure the SPI settings in the "Capture" tab.**
- **Set triggers and filters if needed in the "Triggers" tab.**
- **Click "Start Capturing" to begin sniffing.**
- **The utility will display captured data in various formats.**

**Description:**

- The sniffed data will be displayed in hexadecimal format, usually representing bytes sent and received on the MOSI and MISO lines.
- You can analyze the data manually or use specialized tools depending on the SPI protocol and the expected output.
- Remember to adjust the SPI settings, capture duration, and filters based on your specific needs.

**Additional notes:**

- The Bus Pirate SPI sniffer has limited buffer size, so consider capturing shorter bursts or filtering data for specific events.
- For complex protocols or higher speeds, dedicated SPI analyzers might be more suitable.
- Always refer to the Bus Pirate documentation and specific application notes for detailed instructions and troubleshooting.

## Example


**Here's an example using the command `flashrom -p buspirate <polarity>:<phase>:<speed>:<cs> -r /dev/null`:**

**Assuming the following:**

- Your Bus Pirate is connected to `/dev/ttyUSB0`.
- Your target device uses SPI clock polarity 0 (idle low), phase 1 (end sample), a speed of 1 MHz, and a single chip select line.

**The command would be:**

```bash
flashrom -p buspirate_spi:dev=/dev/ttyUSB0,spispeed=1M,spimode=0:1:1 -r /dev/null
```

**Explanation:**

- `flashrom`: The program used to interact with flash chips.
- `-p buspirate_spi`: Specifies the Bus Pirate as the programmer.
- `dev=/dev/ttyUSB0`: Identifies the Bus Pirate's USB device name.
- `spispeed=1M`: Sets the SPI clock speed to 1 MHz.
- `spimode=0:1:1`: Sets the SPI mode to 0 (polarity 0, phase 1, 1 chip select).
- `-r /dev/null`: Instructs Flashrom to read data and discard it (not saving).

**Remember:**

- Replace the device name and SPI settings with values appropriate for your setup.
- Consult your target device's datasheet for accurate SPI parameters.
- If you encounter errors, check permissions, device names, SPI settings, and hardware connections.
- Refer to the Flashrom documentation for more advanced usage and troubleshooting.

---

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

