# NavCore-UM982-V2

👉[NavCore-UM982-V2](https://yantechlab.com/products/yx-os57-um982-rtk-high-precision-gnss-module-centimeter-level-accuracy-for-professional-surveying)

## 1. Restore Default Settings

<img title="" src="https://github.com/YanTechHub/YanTechLab-NavCore-UM982-RTK/blob/main/Image/1.png?raw=true" alt="1.png" width="594">

After installing the **UPrecise** software, connect the device via serial port. Please ensure the **New Line** option is enabled in the serial settings.

```context
freset // Clear saved receiver settings, satellite ephemeris, position data, etc. Baud rate resets to 115200 bps
CONFIG COMX 115200 // Configure baud rate for COMX (X is the serial port number shown on your PC, CH341 driver required)
UNMASK GPS // Enable GPS
UNMASK BDS // Enable BeiDou
UNMASK GLO // Enable GLONASS
UNMASK GAL // Enable Galileo
UNMASK QZSS // Enable QZSS
GPRMC COM1 1 // Output GNGGA data at 1Hz
GPGSV COM1 1 // Output multi-system $GSV data at 1Hz
SAVECONFIG // Save configuration to receiver
```

---

## 2. Firmware Upgrade

In the **UPrecise** left navigation panel, click **Receiver Upgrade** to enter the firmware upgrade interface. Load the firmware file **UM982_R4.10Build23575**, then click **Soft reset** and **Start** sequentially. The upgrade process will proceed automatically.

![2.png](https://github.com/YanTechHub/YanTechLab-NavCore-UM982-RTK/blob/main/Image/2.png?raw=true)

---

## 3. Common Commands

| Command                | Description                                                                                                     | Parameters / Notes                                                                                                                                          |
| ---------------------- | --------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `freset`               | **Factory reset**<br>Clear all saved settings, ephemeris, and position data. Baud rate resets to **115200 bps** | No parameters                                                                                                                                               |
| `version`              | **Query firmware version**<br>Display the current receiver firmware version                                     | No parameters                                                                                                                                               |
| `config`               | **Query serial port status**<br>Display current baud rate and settings for all serial ports (COM1/2/3)          | No parameters                                                                                                                                               |
| `mask [system]`        | **Disable satellite system**<br>Disable the specified GNSS system                                               | `[system]`: `BDS`, `GPS`, `GLO`, `GAL`<br>Example: `mask BDS`                                                                                               |
| `unmask [system]`      | **Enable satellite system**<br>Enable the specified GNSS system (receiver tracks all systems by default)        | `[system]`: `BDS`, `GPS`, `GLO`, `GAL`<br>Example: `unmask BDS`                                                                                             |
| `config com[X] [baud]` | **Set serial port baud rate**<br>Configure the communication rate for a specified serial port                   | `[X]`: Port number (1/2/3)<br>`[baud]` supports: `9600`, `19200`, `38400`, `57600`, `115200`, `230400`, `460800`, `921600`<br>Example: `config com1 115200` |
| `unlog`                | **Stop data output**<br>Immediately stop all NMEA data output on the current serial port                        | No parameters                                                                                                                                               |
| `saveconfig`           | **Save configuration**<br>Write all current settings to non-volatile memory (persists after power cycle)        | No parameters                                                                                                                                               |
| `mode base`            | **Set to base station mode**<br>Switch receiver to base station operation mode                                  | No parameters                                                                                                                                               |
| `mode rover`           | **Set to rover mode**<br>Switch receiver to rover operation mode (**factory default mode**)                     | No parameters                                                                                                                                               |
| `gpgga com[X] [rate]`  | **Output GGA data**<br>Output GGA messages on the specified serial port at the set rate                         | `[X]`: Port number<br>`[rate]`: e.g., `1` for 1Hz<br>Example: `gpgga com1 1`                                                                                |
