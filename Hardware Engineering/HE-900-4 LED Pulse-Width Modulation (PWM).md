- ESP 32 PWM controller has 16 independent channels that can be configured to generate PWM signals with different properties.

# Hardware Requirement
1. ESP32 DOIT DEVKIT V1 Board
2. 5mm LED
3. 330 Ohm resistor
4. Breadboard
5. Jumper wires
# Schema
![[Pasted image 20260305124913.png]]
# Steps will have to follow to dim an LED with PWM using the Arduino IDE
1. Need to choose a PWM channel. There are 16 channels from 0 -15.
2. Need to set PWM signal frequency. For LED: 5 000 Hz.
3. Need to set the signal's duty cycle resolution from 1 - 16 bits. Using 8  bits resolution, means can control LED brightness using a value from 0 - 255.
4. Need to specify to which GPIO or GPIOs the signal will appear.
5. Control the LED brightness using PWM, use the following function.
# Code
```cpp
// the number of the LED pin
const int ledPin = 16; // 16 corresponds to GPIO16

// setting PWM properties
const int freq = 5000;
const int ledChannel = 0;
const int resolution = 8;

void setup(){

	// configure LED PWM functionalitites
	ledcSetup(ledChannel, freq, resolution);
	
	// attach the channel to the GPIO to be controlled
	ledcAttachPin(ledPin, ledChannel);
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
}
```

- Define a frequency of 5 000 Hz, choose channel 0 to generate the signal and set a resolution of 8 bits.
- setup(), need to configure LED PWM with the properties by using the ***ledAttachPin()*** that accepts as arguments.
- ledChannel, the frequency and the resolution as follows

- Choose the GPIO, will get the signal form. ***ledAttachPin()*** function that accepts as arguments the GPIO where want to get the signal and the channel that is generating the signal.
- Loop, will vary the duty cycle between 0 and 255 to increase the LED brightness.
- Set the brightness of the LED, just need to use the ***ledcWrite()*** that accepts as arguments the channel that is generating the signal and duty cycle.
- Using 8 bit resolution, the duty cycle will be controlled using a value from 0 - 255. ***ledcWrite()***, use the channel that is generating the signal and not the GPIO.
