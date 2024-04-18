# NTP

# ESP32 Time Synchronization with NTP Server and Wi-Fi

This Arduino sketch demonstrates how to use an ESP32 microcontroller to connect to a Wi-Fi network, synchronize its internal clock with an NTP (Network Time Protocol) server, and print formatted local time information via serial communication.

## Prerequisites

- Arduino IDE installed on your computer.
- ESP32 board selected and configured in the Arduino IDE.
- Serial monitor enabled in the Arduino IDE for viewing debug output.

## Setup Instructions

1. **Install Libraries**:
   - Ensure that the required libraries (`WiFi.h` and `time.h`) are included in your Arduino IDE. You can install these libraries via the Library Manager in Arduino IDE.

2. **Connect ESP32 to Wi-Fi**:
   - Modify the `ssid` and `password` variables in the sketch to match your Wi-Fi network credentials.

3. **Specify NTP Server and Time Zone**:
   - Update the `ntpServer`, `gmtOffset_sec`, and `daylightOffset_sec` variables in the sketch according to your location. Use a reliable NTP server address (e.g., `"pool.ntp.org"`) and specify the GMT offset and daylight saving time offset in seconds.

4. **Upload and Run the Sketch**:
   - Upload the sketch to your ESP32 board using the Arduino IDE.
   - Open the serial monitor (baud rate: `115200`) to view the output.

## Sketch Explanation

- **`setup()` Function**:
  - Initializes serial communication and connects the ESP32 to the specified Wi-Fi network.
  - Configures time settings using the `configTime()` function with the specified NTP server and time zone offsets.
  - Calls the `printLocalTime()` function to print the current local time once during setup.

- **`loop()` Function**:
  - Executes continuously after setup.
  - Calls the `printLocalTime()` function every 10 seconds (`delay(10000)`) to print updated local time information.

- **`printLocalTime()` Function**:
  - Attempts to obtain the current local time using the `getLocalTime()` function.
  - Formats and prints various components of the local time (day of the week, month, day, year, hour, minute, second) using `strftime()` with specific format specifiers (`"%A"`, `"%B"`, `"%d"`, `"%Y"`, `"%H"`, `"%I"`, `"%M"`, `"%S"`).

## Serial Output

- The sketch outputs formatted local time information to the serial monitor.
- Time variables (e.g., hour, day of the week) are printed using `strftime()` with custom format specifiers.

## Troubleshooting

- If the sketch fails to obtain time from the NTP server, ensure that the ESP32 is connected to the Wi-Fi network and has internet access.
- Check the serial monitor for error messages and debug information.

---
