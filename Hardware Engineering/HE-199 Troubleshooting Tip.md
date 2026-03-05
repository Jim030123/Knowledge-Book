# 001 - Failed to connect to ESP32: Timed out... Connecting...
When try to upload new sketch to ESP32 and fails to connect to board. It means that ESP32 is not in flashing or uploading mode.

## Solution
1. Hold-down the "BOOT" button in ESP32 board.
2. Press "Upload" button in the Arduino IDE to upload a new sketch.
3. See "connecting..." message in Arduino IDE, release the finger from the "BOOT" button
![[Pasted image 20260305101231.png]]
# 002 - Don't see the COM Port in Arduino IDE
![[Pasted image 20260305101339.png]]
# 002-1 USB Driver Missing
## Solution
1. Download the CP2102 drivers on the Silicon labs website.
2. Need install the ESP32 CP210x USB to UART Bridge VCP Drivers.
3. Restart the Arduino IDE.

# 002-2  USB cable without data wires
## Solution
1. Double-check that are using a USB cable with data wires.
2. USB from powerbanks often don't have data wires.^[Will never establish a serial communication with ESP32]
