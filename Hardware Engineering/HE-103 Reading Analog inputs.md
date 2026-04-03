- Means can measure varying levels between 0V and 3.3V. The voltage measured is then assigned to a value between 0 - 4095.
  0 V - 0
  3.3V - 4095
>[!note] Have margin of error
>![[Pasted image 20260305174117.png]]
>- Means that ESP32 is not able to distinguish 3.3V from 3.2V. Will get the same value for both voltages: 4095. 
>- Same happens for very low voltages for 0 V and 0.1V.
>-