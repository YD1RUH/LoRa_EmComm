# LoRa_EmComm
An Implementation of LoRa for EmComm (Emergency Communication) or (TacComm) Tactical Communication

<p>
  <img src="https://github.com/YD1RUH/LoRa_EmComm/blob/main/image.jpg?raw=true" alt="LoRa_EmComm" width="60%">
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
- **Chat Room**, like a usual chat, but I've limited only for 220 Character.
- **Gel Loc**, For beacon Your node location. Manually input **Latitude** and **Longitude**. Beacon **Interval** Start from 30 Second, to avoid collision packet.
- **Config Menu**, you don't need to compile or recompile your ESP32, It can be configured over webUI. you can configure (**Spreading Factor**, **Bandwidth**, **Gain**, **TX Power**, **Frequency**).
- **Key Gen**, if you want to chat privately with someone just make aggrement **passphrase** with your partner then **thick** Cheklist **Enable Encryption** to start secure chatting.

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=YD1RUH/LoRa_EmComm&type=Date)](https://www.star-history.com/#YD1RUH/LoRa_EmComm&Date)
