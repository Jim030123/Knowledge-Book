# Hardware Requirement
1. ESP32 DOIT DEVKIT V1 Board
2. 5mm LED
3. 330 Ohm resistor
4. 10k Ohm resistor
5. Breadboard
6. Jumper wires
# Schema
![[Pasted image 20260305110341.png]]
```cpp
// set pin numbers
const int buttonPin = 4;   // pushbutton pin
const int ledPin = 16;     // LED pin

// variable for storing the pushbutton status
int buttonState = 0;

void setup() {
  Serial.begin(115200);

  // initialize the pushbutton pin as input
  pinMode(buttonPin, INPUT);

  // initialize the LED pin as output
  pinMode(ledPin, OUTPUT);
}

void loop() {

  // read the state of the pushbutton
  buttonState = digitalRead(buttonPin);

  // print button state to serial monitor
  Serial.println(buttonState);

  // check if the pushbutton is pressed
  if (buttonState == HIGH) {
    // turn LED on
    digitalWrite(ledPin, HIGH);
  } else {
    // turn LED off
    digitalWrite(ledPin, LOW);
  }

}
```