# Interrupts
- To trigger an event with a PIR motion sensor, use interrupts. 
- Interrupts, don't need to constantly check the current value of a pin. When change is detected, an event is triggered.
## digitalPinToInterrupt
```cpp
attachInterrupt(digitalPinToInterrupt(GPIO), function, mode)
```
![[Pasted image 20260306110501.png]]
# Mode
- 5 different mode:
1. Low
   To trigger the interrupt whenever the pin is LOW.
2. High
   To trigger the interrupt whenever the pin is HIGH.
3. Change
   To trigger the interrupt whenever the pin changes value.
   HIGH to LOW
   LOW to HIGH
4. Falling
   For when the pin goes from HIGH to LOW.
5. Rising
   To trigger when the pin goes from LOW to HIGH.
# Timer
## delay()
```cpp
delay(time in milisecond)
```
- Delays is a blocking function. Blocking functions prevent a program from doing anything else until that particular task is completed. Need multiple tasks to occur at the same time.
## mills()
Return the number of milliseconds that have passed since the program started.