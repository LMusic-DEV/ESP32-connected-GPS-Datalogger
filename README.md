*Disclaimer: This project is primarily documented in French*
# Perform-Chandail
This project is a GPS data logger based on ESP32.
It features:
* A battery management system
* A GPS data logger (GPS provides: Speed, altitude, latitude, longitude, time, date)
* JSON data saving on SD
* Communication between ESP32 and a mobile app to send JSON data saved via Wi-Fi



**For more information see [Documentation](00_Documentation)**
## 1.0 First relase and beta test update (24/05/2024)
**Datalogger directory update**

Added Datalogger V8 :
* Enable/Disable JSON Stacking in SD
* Enable/Disable GPS datalogging

**Communication Directory update**

Added HTTP Web Server Test :
* "/" Root -> Print all the http commands avaliable
* "/list_files" -> lists all file on SD
* "/download?file=/gps_data_1.json" -> download the selected file on request
* "/remove_file?file=/gps_data_1.json" -> remove the selected file on request
* "/pointed_gps_data?file=/gps_data_1.json" -> Push the selected json on request
* "/gps_data" -> Push JSON file "/gps_data.json" on request
* "/gps_json_value?value=date" -> Push the value of the JSON  on request, in this case the date

**Added : Perform Chandail ESP32 directory added**

Includes : 
* Feature form HTTP Web server test code
* Feature from the Datalogger V8

## 0.2b Beta realease update (11/05/2024)
**Datalogger directory update:**
Added Datalogger V7
* LCD Withdrawn
* Calculates and writes on SD the route taken by GPS at the end of the race : Average Speed, duration, positive altitude change, total distance
* Option to disable writing GPS data to SD card every second

**Added: Communication directory**
* ESP32 Bluetooth Classic program capable of sending: File by segment of 128 octets, Files in a directory, File info (size, number of divisible packets...)
* Python test capable of receiving simple Bluetooth data (supports hello world command from the Bluetooth classic program, issue with acquisition of large string). If this solution doesn't work, an ESP32 will be an HTTP Server on WiFi AP capable of sending JSON files to the mobile device.

**Added: Documentation directory**
* Include schematic and PCB design of the project
## 0.1b Beta release (16/04/2024)
**Added: Datalogger directory**
* Datalogger V1: Records GPS data and saves it on the SD Card & push button in interruption that can stop recording and create a new file at every ESP32 start
* Datalogger V2: Features a timed buffer for GPS data acquisition and an RGB Led that can monitor the acquisition of data
* Datalogger V3: Modification on the naming of the "null" data, blocks the starting of the program if no SD card
* Datalogger V4/V5/V6: Implementation of a 3-way switch that changes between modes: Communication mode, Datalogger mode, and system off. Features Handling brutal stop*. Improved code clarity by subdividing into functions. Adding #define for colors

    -> V4: Features a writing erasing technique on SD that stops data acquisition when brutally stopped. Also features LCD data monitoring for battery tests **(does not work: file corruption)**

    -> V5: Features an EEPROM system that modifies the last file when it's in communication mode by adding {}]. Also features LCD data monitoring for battery tests **(working but not really reliable: file corruption)**

    -> **V6 & V6_LCD**: Features a push button that needs to be pressed to stop GPS data acquisition, then put ESP32 in sleep mode to save battery. LCD version features monitoring for battery tension and data of the datalogger



*brutal stop: means that ESP32 runs out of battery or is stopped by the user


**Added: Battery management directory**

**Added: Unitary tests directory**
