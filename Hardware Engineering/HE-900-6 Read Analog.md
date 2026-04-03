# Hardware Requirement
1. DSP32 DOIT DEVKIT V1 Board
2. Potentiometer
3. Breadboard
4. Jumper wires
# Schema
![[Pasted image 20260306094002.png]]

# Code
```cpp
// Potentiometer is connected to GPIO 34 (Analog ADC1_CH6)
const int potPin = 34;

// variable for storing the potentiometer value
int potValue = 0;

void setup() {
	Serial.begin(115200);
	delay(1000);
}

void loop() {

	// Reading potentiometer value
	potValue = analogRead(potPin);
	Serial.println(potValue);
	delay(500);
}
```

- Start by defining the GPIO 34 is defining the potentiometer.
- ***setup()***, initialize serial communication at baud rate of 115 200.
- ***loop()***, use the ***analogRead()*** to read the analog input from the potPin.
- print the values read from the potentiometer in the serial monitor.
![[Pasted image 20260306100547.png]]