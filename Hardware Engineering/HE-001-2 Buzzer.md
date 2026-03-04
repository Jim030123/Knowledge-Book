# Active Buzzer
```c++
#define BUZZER 4  
  
void setup() {  
pinMode(BUZZER, OUTPUT);  
}  
  
void loop() {  
digitalWrite(BUZZER, HIGH);  
delay(1000);  
  
digitalWrite(BUZZER, LOW);  
delay(1000);  
}
```

# Passive Buzzer
```c++
#define BUZZER 4  
  
void setup() {  
ledcSetup(0, 2000, 8);  
ledcAttachPin(BUZZER, 0);  
}  
  
void loop() {  
ledcWriteTone(0, 2000);  
delay(1000);  
  
ledcWriteTone(0, 0);  
delay(1000);  
}
```