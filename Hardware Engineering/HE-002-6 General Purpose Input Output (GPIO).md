To connect:
- OLED monitor
- TFT monitor
- SD Card
- Sensor
Have 4 line:

| Line                       | Function                     | Example                                                |
| -------------------------- | ---------------------------- | ------------------------------------------------------ |
| Master Out Slave In (MOSI) | Main component send data     | ES32 sends data to an OLED                             |
| Master In Slave Out (MISO) | Main component received data | OLED sends data back                                   |
| Clock (CLK)                | It control timing            | Clock: ↑ ↓ ↑ ↓ ↑ ↓  <br>Data: 1 0 1 1 0 0              |
| Chip Select (CS)           | Select component             | ESP32 pulls 1 CS LOW to choose which device to talk to |
