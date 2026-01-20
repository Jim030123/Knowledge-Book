# DevTools
Provides all kinds of awesome tools to help debug Flutter app:

| Tools             | Description                                                                                                            |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Flutter Inspector | Used to explore and debug the widget tree.                                                                             |
| Performance       | Allows to analyze Flutter frame charts, timeline events and  CPU profiler.                                             |
| CPU Profiler      | Allows you to record and profile your Flutter app session.                                                             |
| Memory            | Shows how objects in Dart are allocated, which helps find memory leaks.                                                |
| Debugger          | Supports breakpoints and variable inspection on the call stack. Also allows to step though code right within DevTools. |
| Network           | Allows to inspect HTTP, HTTPS and web socket traffic within Flutter app.                                               |
| Logging           | Displays events fired on the Dart runtime and app-level log events.                                                    |
| App Size          | Help analyze total app size.                                                                                           |
![[Pasted image 20251020170842.png]]
>[!tip] Tip
>It works best with the Google Chrome web browser. Click the setting to switch between dark and light mode.

1. Select a widget on the left to see its layout on the right.
![[Pasted image 20251020171023.png]]
# Flutter Inspector
## What are the benefit?
- Visualize widget tree.
- Inspect the properties of specific widget in the tree.
- Experiment with different layout configurations using the ***Layout Explorer***.
- Enable slow animation to show how transitions look.

## What are tools inside?

| Tools                     | Description                                                                                                                                                                                                                                                                       |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Select Widget Mode        | When enabled, this allows to tap a particular widget on a device or simulator to inspect its properties.<br><br>Clicking any element in the widget tree also highlights the widget on the device and jumps to the exact line of code.<br><br>![[Pasted image 20251020172836.png]] |
| Refresh Tree              | Simply reloads the current widget's info.<br><br>Depending on if your browser is expanded or collapsed, will see one of the following toolsets.<br><br>![[Pasted image 20251020173141.png]]<br><br>![[Pasted image 20251020173245.png]]                                           |
| Slow Animation            | Slows down the animation, can visually inspect the UI transitions.<br><br>![[Pasted image 20251020195128.png]]                                                                                                                                                                    |
| Show Guideline            | Shows visual debugging hints. That allows to check widgets' borders, padding and alignment.<br><br>![[Pasted image 20251020195329.png]]<br>![[Pasted image 20251020195345.png]]                                                                                                   |
| Show Baselines            | When enabled, this tells RenderBox to paint a line under each text's baseline.<br><br>![[Pasted image 20251020200345.png]]<br>![[Pasted image 20251020200359.png]]                                                                                                                |
| Highlight Repaints        | Adds a random border to a widget every time Flutter repaints it. Useful if want to unnecessary repaints.<br>![[Pasted image 20251020200457.png]]<br><br>Disco mode<br>![[Pasted image 20251020200525.png]]                                                                        |
| Highlight Overside Images | Tells which images in app are oversized.<br>![[Pasted image 20251020200609.png]]<br><br>if an image is oversized, it will invert the image colors and flip it upside down.<br>![[Pasted image 20251020200712.png]]                                                                |
# Inspecting the Widget Tree
1. In the emulator, select the first tab,  
2. Click Refresh Tree in DevTools.
3. Select ***CategoryCard*** and click ***Widget Details Tree tab***
   ![[Pasted image 20251020200939.png]]
	- In the left panel, there's a portion of the Flutter widget tree under investigation, starting from the root.
	- When tap a specific widget in the tree, can inspect its sub-tree, as shown in the Widget Details Tree tab om the right pane;.
	- Details Tree represents the element tree and displays all the important properties that make up the widget. It references ***renderObject***

4. Click ***Text*** widget, will see all the properties can configure.
   ![[Pasted image 20251020201320.png]]
## Inspecting like a Pro
- Hover over any widget and it will show a pop up with all the properties.
- Click on a widget to print the widget's object, properties and state in the console.
  ![[Pasted image 20251020201715.png]]
# Layout Explorer (LE)
- To visualize how ***Text*** widget is laid out within the ***Stack***.
Handy for modifying flex widget layouts in real-time. Support modifying:
- mainAxisAlignment
- crossAxisAlignment
- flex
- fit
![[Pasted image 20251020201746.png]]
1. Make sure device is running and Dev Tools is open in browser.
2. Click ***Post*** in the bottom navigation bar.
3. Click the ***Refresh Tree*** button.
4. Select the ***Row*** element in the tree.
5. Click ***Layout Explorer***.
   ![[Pasted image 20251020202007.png]]

6. Click start within the Cross Axis and change the value to stretch.
   ![[Pasted image 20251020202242.png]]
	- Useful when need to inspect and tweak layouts at runtime.
	- Feel free to experiment and play around with the LE. Can create simple column or row widgets to mess around with the layout axis.