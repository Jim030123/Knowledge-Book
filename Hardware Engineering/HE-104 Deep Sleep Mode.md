Can switch between different power modes:
- Active mode
- Modem Sleep mode
- Light Sleep mode
- Deep Sleep mode
![[Pasted image 20260306141718.png]]
![[Pasted image 20260306141731.png]]
![[Pasted image 20260306141745.png]]

# Why Deep Sleep Mode
![[Pasted image 20260306141852.png]]
- It will reduce the power consumption and batteries will last longer.
- In deep sleep mode neither CPU or Wi-Fi activities take place, but Ultra Low Power (ULP) co-processor can still be powered on.
- Can write a program for the ULP co-processor and store it in the RTC memory to access peripheral device, internal timers and internal sensors.
# RTC_GPIO Pins
![[Pasted image 20260306143007.png]]
## Wake-up source
ESP32 into deep sleep mode:
- Can use the timer, waking up ESP32 using predefined periods of time.
- Can use the touch pins.
- Can use the ULP co-processor can still be powered on.
# Writing a Deep Sleep Sketch
1. Need to configure the wake-up the ESP32. Can use 1 or combine more than 1 wake-up source.
2. Can decide what peripherals to shut down or keep on during deep sleep.
3) Use the ***esp_deep_sleep_start()*** to put ESP32 into deep sleep mode.