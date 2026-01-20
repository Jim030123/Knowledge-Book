# 001: Flutter Doctor: Unable to determine bundled Java Version
![[Pasted image 20251017222912.png]]

>[!tip] Solution
>1. Determine which version Android Studio
>2. Find out Android Studio configuration JDK Path
>```bash
>C:\Program Files\Android\Android Studio\jbr
>```
>3. Configuration Flutter SDK
>```bash
>flutter config --jdk-dir "C:\Program Files\Android\Android Studio\jbr"
>```
>


## 002: Overflow

```bash
A RenderFlex overflowed by XX pixels on the right/bottom
```
- 如果是 **Column 或 Row 的 overflow**，可以用 `Flexible` 或 `Expanded` + `LayoutBuilder` 配合。    
- 如果是 **文本内容 overflow**，`TextOverflow.ellipsis` 或 `softWrap: true` 很常用。