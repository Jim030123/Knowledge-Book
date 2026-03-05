- ESP 32 PWM controller has 16 independent channels that can be configured to generate PWM signals with different properties.
# Steps will have to follow to dim an LED with PWM using the Arduino IDE
1. Need to choose a PWM channel. There are 16 channels from 0 -15.
2. Need to set PWM signal frequency. For LED: 5 000 Hz.
3. Need to set the signal's duty cycle resolution from 1 - 16 bits. Using 8  bits resolution, means can control LED brightness using a value from 0 - 255.
4. Need to specify to which GPIO or GPIOs the signal will appear.