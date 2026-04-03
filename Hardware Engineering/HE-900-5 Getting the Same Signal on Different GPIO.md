# Hardware Requirement
1. ESP32 DOIT DEVKIT V1 Board
2. 3 x 5 mm LED
3. 3 x 330 Ω Resistor
4. Breadboard
5. Jumper wires
![[Pasted image 20260305173140.png]]
```cpp
// the number of the LED pin

const int ledPin = 16; // 16 corresponds to GPIO16
const int ledPin2 = 17; // 17 corresponds to GPIO17
const int ledPin3 = 5; // 5 corresponds to GPIO5

// setting PWM properties
const int freq = 5000;
const int ledChannel = 0;
const int resolution = 8;

void setup(){

	// configure LED PWM functionalitites
	ledcSetup(ledChannel, freq, resolution);
	
	// attach the channel to the GPIO to be controlled
	ledcAttachPin(ledPin, ledChannel);
	ledcAttachPin(ledPin2, ledChannel);
	ledcAttachPin(ledPin3, ledChannel);
}

void loop(){

// increase the LED brightness
for(int dutyCycle = 0; dutyCycle <= 255; dutyCycle++){

 // changing the LED brightness with PWM
 ledcWrite(ledChannel, dutyCycle);
 delay(15);
}

// decrease the LED brightness
for(int dutyCycle = 255; dutyCycle >= 0; dutyCycle--){
 
 // changing the LED brightness with PWM
 ledcWrite(ledChannel, dutyCycle);
 delay(15);
}
```

- 2 more variables for 2 new LEDs that refer to GPIO7 and GPIO5.
- ***setup()***, have added the following lines to assign both GPIOs to channel 0. This means that we will get the same signal that is being generated on channel 0, on both GPIOs.