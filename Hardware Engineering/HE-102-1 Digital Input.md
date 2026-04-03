# digitalWrite()
- To control a digital output.
```cpp
digitalWrit(GPIO, STATE)
```
# digitalRead()
- To read a digital input, for example button, that accepts as argument.
```cpp
digitalRead(GPIO)
```

# touchRead()
- That accepts as argument, the GPIO want to read.
```cpp
touchRead(GPIO)
```

```cpp
// ESP32 Touch Test
// Just test touch pin - Touch0 is T0 which is on GPIO 4.

void setup(){
	Serial.begin(115200);
	delay(1000); // give me time to bring up serial monitor
	Serial.println("ESP32 Touch Test");
}

void loop(){
	Serial.println(touchRead(4)); // get value of Touch 0 pin = GPIO 4
	delay(1000);
}
```
## Testing the Example
- Connect a jumper wire to GPIO4, will touch the metal part of this wire that it senses the touch.
Tools > Serial Monitor
baud: 115200

Touch the wire connected to GPIO 4 and will see the values decreasing.
![[Pasted image 20260305120846.png]]

Tools > Serial Plotter
![[Pasted image 20260305120859.png]]

# analogRead()
- ESP32 supports measurements in 18 different channels. But only 15 are available in the DEVKIT V1 DOIT board.
```cpp
analogRead(GPIO)
```
![[Pasted image 20260306093055.png]]
