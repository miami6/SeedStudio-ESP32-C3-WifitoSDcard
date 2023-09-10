# SeedStudio-ESP32-C3-WifitoSDcard
SeedStudio-ESP32-C3-WifitoSDcard

This code is for an Seed Studio ESP32-C3 board project that scans for nearby Wi-Fi networks, retrieves information about them, and saves that information to an SD card in a CSV (Comma-Separated Values) file format. Let's go through each function and its purpose:

1. `listDir(const char *dirname, uint8_t levels)`:
   - This function is declared but not defined in the provided code snippet. It appears to be part of a larger program or library but is not implemented here.

2. `createTestFile()`:
   - This function creates a test file named "test.txt" on the SD card if it doesn't already exist.
   - It writes the text "Test SD card." to the file.
   - It prints a message to the serial monitor to indicate whether the file creation was successful or if there was an error.

3. `setup()`:
   - This is the setup function, which is executed once when the Arduino is powered on or reset.
   - It initializes the serial communication for debugging purposes.
   - It attempts to initialize the SD card using the specified chip select pin (`chipSelect`). If successful, it prints a message indicating that the card is mounted.
   - It then lists the files in the root directory of the SD card using the undefined `listDir` function.
   - It calls the `createTestFile()` function to create a test file on the SD card.
   - Finally, it sets up the Arduino as a Wi-Fi station (client) and disconnects from any previously connected access point.

4. `generateNewFilename()`:
   - This function generates a new filename for the CSV files that will store the Wi-Fi scan results.
   - It uses a base filename (`baseFilename`), appends a numerical file number (incremented each time the function is called), and adds a file extension (`fileExtension`).
   - The generated filename is returned as a string.

5. `saveScanResultsToSDWithMAC(int scanCount)`:
   - This function saves the scan results of nearby Wi-Fi networks to an SD card file in CSV format.
   - It generates a new filename using the `generateNewFilename()` function.
   - It opens the file for writing and writes a header line with column names: "SSID, RSSI, Channel, Encryption, MAC."
   - It then iterates through the scan results, collecting information about each network (SSID, RSSI, channel, encryption type, and MAC address), and writes this information to the file as a CSV entry for each network.
   - After all the information is written, the file is closed.
   - A message indicating the successful saving of the scan results or an error message is printed to the serial monitor.

6. `loop()`:
   - This is the main loop of the Arduino program, which runs repeatedly after the `setup()` function has executed.
   - It starts by printing "Scan start" to the serial monitor.
   - It scans for nearby Wi-Fi networks using `WiFi.scanNetworks()` and stores the number of networks found in `n`.
   - If no networks are found (`n == 0`), it prints "No networks found" to the serial monitor.
   - If networks are found, it iterates through the scan results, printing information about each network to the serial monitor in a formatted table.
   - It then calls the `saveScanResultsToSDWithMAC(n)` function to save the scan results to the SD card.
   - After saving the results, it deletes the scan results to free up memory and waits for a brief period before scanning again (5 seconds in this case).

Please note that the `listDir` function is declared but not implemented in the provided code snippet. To understand its functionality, you would need to look at the rest of the code that includes its implementation.
