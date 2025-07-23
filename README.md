# LoRa_EmComm
An Implementation of LoRa for **EmComm (Emergency Communication)** or **(TacComm) Tactical Communication**

<p>
  <img src="https://github.com/YD1RUH/LoRa_EmComm/blob/main/image.jpg?raw=true" alt="LoRa_EmComm" width="80%">
</p>

## How to install
- clone this repository: `git clone https://github.com/YD1RUH/LoRa_EmComm.git`
- get in to directory: `cd LoRa_EmComm`
- install ESP driver, download from [here](https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads), choose `CP210x Windows Drivers`
- download esptool, you can download form [here](https://github.com/espressif/esptool/releases)
- unzip, then set the path directory of esptool that you unzip to `windows environtment variable`
- on directory `LoRa_EmComm`, open CMD and execute this command: `esptool --chip esp32 --port COM[change your port Detected] --baud 460800 write-flash 0x10000 firmware.bin 0x290000 spiffs.bin`
- wait until Upload Process done.

## How to use
1. **First**, LoRa_EmComm will be started as a **HotSpot**, information **SSID** and **Password** will be apear in **OLED**
2. After connected to LoRa_EmComm, **Recomended** to do configuration on **Config Menu**. after you Click **Save**, LoRa_EmComm will reboot then **SSID** and **Password** will be changes.
3. Connect again to **LoRa_EmComm** hotspot with your new configuration.

### Feature
- `Chat Room`, like a usual chat, but I've limited only for 220 Character.
- `Gel Loc`, For beacon Your node location. Manually input **Latitude** and **Longitude**. Beacon **Interval** Start from 30 Second, to avoid collision packet.
- `Config Menu`, you don't need to compile or recompile your ESP32, It can be configured over webUI. you can configure (**Spreading Factor**, **Bandwidth**, **Gain**, **TX Power**, **Frequency**).
- `Key Gen`, if you want to chat privately with someone just make aggrement **passphrase** with your partner then **thick** Cheklist **Enable Encryption** to start secure chatting.

## Feedback
- **Really apreciate** if your mind give me a feedbeack: [Submit Feedback](https://forms.gle/ndPy9DZC3oz5MFPu8)
- **Support** me: [Pateron](https://www.patreon.com/YD1RUH)

## Recommendation LoRa Configuration
<table border="1" cellpadding="8" cellspacing="0">
  <thead>
    <tr>
      <th>Environment</th>
      <th>SF (Spreading Factor)</th>
      <th>Bandwidth (kHz)</th>
      <th>TX Power (dBm)</th>
      <th>Gain (dB)</th>
      <th>Purpose / Effect</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Urban (Dense Buildings)</td>
      <td>SF9 – SF12</td>
      <td>125</td>
      <td>17–20</td>
      <td>4–6</td>
      <td>Good wall penetration; better reliability at the cost of data rate</td>
    </tr>
    <tr>
      <td>Suburban (Houses, Low-rise)</td>
      <td>SF8 – SF10</td>
      <td>125–250</td>
      <td>14–18</td>
      <td>3–5</td>
      <td>Balanced for moderate range and power efficiency</td>
    </tr>
    <tr>
      <td>Rural (Open Field)</td>
      <td>SF7 – SF9</td>
      <td>250–500</td>
      <td>14–17</td>
      <td>0–3</td>
      <td>Fast transmission, long distance in Line-of-Sight</td>
    </tr>
    <tr>
      <td>Indoor (Short Distance)</td>
      <td>SF7 – SF9</td>
      <td>250–500</td>
      <td>10–14</td>
      <td>0–2</td>
      <td>Low latency and power-efficient communication</td>
    </tr>
    <tr>
      <td>Hilly or Forested Terrain</td>
      <td>SF10 – SF12</td>
      <td>125</td>
      <td>17–20</td>
      <td>4–6</td>
      <td>Better performance through non-line-of-sight and foliage</td>
    </tr>
    <tr>
      <td>Critical/Long-Range Application</td>
      <td>SF11 – SF12</td>
      <td>125</td>
      <td>20</td>
      <td>6</td>
      <td>Max range and reliability, at the expense of speed and power</td>
    </tr>
  </tbody>
</table>

## History Developing
<table>
  <tr>
    <td>
      ESP32 simple LoRa Communication
    </td>
    <td>
      <ul>
        <li>operate using serial USB</li>
        <li>operate using Bluetooth Serial</li>
      </ul>
    </td>
    <td>
      <a href="https://x.com/octacons/status/1945113731215622381" target="_blank">footprint</a>
    </td>
  </tr>
  
  <tr>
    <td>
      Initiate using webUI hosted in TTGO LoRa32-OLED for interface communication
    </td>
    <td>
      <ul>
        <li>using identity (Callsign)</li>
        <li>send message with LoRa</li>
      </ul>
    </td>
    <td>
      <a href="https://x.com/octacons/status/1946737701832823204" target="_blank">footprint</a>
    </td>
  </tr>

  <tr>
    <td>
      Initiate using webUI hosted in TTGO LoRa32-OLED for interface communication
    </td>
    <td>
      <ul>
        <li>Adding Costumize SSID and Password hotspot over webUI</li>
        <li>Adding LoRa configuration over WebUI:
          <br>- Spreading Factor
          <br>- Bandwidth
          <br>- Gain
          <br>- TX Power
        </li>
      </ul>
    </td>
    <td>
      <a href="https://x.com/octacons/status/1947037142653517900" target="_blank">footprint</a>
    </td>
  </tr>

  <tr>
    <td>
      Cryptography Feature
    </td>
    <td>
      <ul>
        <li>Input Key using Passphrase -> hashed (SHA3) -> save to SPIFFS</li>
        <li>Enrypt Decrypt Message Feature</li>
      </ul>
    </td>
    <td>
      <a href="https://x.com/octacons/status/1947304588488650877" target="_blank">footprint</a>
    </td>
  </tr>

  <tr>
    <td>
      Geo Location For Static Station
    </td>
    <td>
      <ul>
        <li>Configure beacon parameter
          <br>- CALLSIGN
          <br>- Interval duration TX
          <br>- Latitude
          <br>- Longitude
        </li>
        <li>Compas Navigation (heading north)</li>
        <li>table list onther active node</li>
      </ul>
    </td>
    <td>
      <a href="https://x.com/octacons/status/1947605624105181541" target="_blank">footprint</a>
    </td>
  </tr>
</table>

## Next To Do ..
- Range test
