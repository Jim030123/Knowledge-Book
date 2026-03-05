# Hardware Requirement
1. ESP32 DOIT DEVKIT V1 Board
2. 5mm LED
3. 330 Ohm resistor
4. Breadboard
5. Jumper wires
6. Aluminium Paper
# Schema
![[Pasted image 20260305121438.png]]
7. Grab a piece of aluminium foil, cut a small square and wrap it around the wire in the following figure.
![[Pasted image 20260305121114.png]]
8. Tools > serial monitor.
9. Touch the aluminium foil, will see the values changing again.
# Code
```cpp
// set pin numbers
const int touchPin = 4;
const int ledPin = 16;

// change with your threshold value
const int threshold = 20;

// variable for storing the touch pin value
int touchValue;

void setup(){
Serial.begin(115200);
delay(1000); // give me time to bring up serial monitor

// initialize the LED pin as an output:
pinMode (ledPin, OUTPUT);
}

void loop(){

// read the state of the pushbutton value:
touchValue = touchRead(touchPin);
Serial.print(touchValue);

// check if the touchValue is below the threshold
// if it is, set ledPin to HIGH
if(touchValue < threshold){
 
 // turn LED on
 digitalWrite(ledPin, HIGH);
 Serial.println(" - LED on");
}

else{
 
 // turn LED off
 digitalWrite(ledPin, LOW);
 Serial.println(" - LED off");
}

delay(500);
}
```

Read the touch value from the pin are defined and lights up an LED when the value is below the thresholds, means when place finger in the aluminium pad.