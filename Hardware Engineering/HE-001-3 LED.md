![[Pasted image 20260304110742.png]]
Left - Positive
Right - Negative

https://wokwi.com/projects/457524529845505025
![[Pasted image 20260304113017.png]]
![[Pasted image 20260304113814.png]]

```cpp title:'LED light on the Breadboard'
int ledPin = 4;

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  digitalWrite(ledPin, HIGH); // LED ON
  delay(1000);
  digitalWrite(ledPin, LOW);  // LED OFF
  delay(1000);
}
```![[Pasted image 20260304112559.png]]