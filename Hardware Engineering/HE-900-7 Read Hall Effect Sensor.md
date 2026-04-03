# Coding
```cpp
// Simple sketch to access the internal hall effect detector on the esp32.
// values can be quite low.

int val = 0;

void setup() {
	Serial.begin(9600);
}

// put your main code here, to run repeatedly
void loop() {
	// read hall effect sensor value
	val = hallRead();

	// print the results to the serial monitor
	Serial.println(val);
	delay(1000);
}
```

- Serial Monitor at baud rate: 9 600.
- Approximate a magnet to the ESP32 hall sensor and see the values increasing.
![[Pasted image 20260306103644.png]]

- Decreasing on the magnet pole that is facing the sensor.
![[Pasted image 20260306103736.png]]