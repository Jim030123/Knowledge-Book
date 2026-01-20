- Responsive widget for web applications is a pivotal task that strikes a balance between optimal use of screen real estate, readability and visual appeal.
- When transitioning from mobile to web views, it's crucial to consider how the menu's layout adapts to larger screens.
  ![[Pasted image 20251023222225.png]]
## Primary strategics
- Option 1: Full Screen Stretch
  This approach extends the menu across the full width of the screen. While it maximizes space, it can also make the menu appear too large.
  
  This vastness can overwhelm users, presenting too much information at once and detracting from the ability to focus on individual items.
- Option 2: Fixed Width
  This design is more aligned with standard web browsing expectations. It offers a structured layout with ample white space around the menu, which enhances visual appeal and improves content legibility.
# Implementing Responsive Design
1. Add constraint properties.
   - These represent the maximum allowable width and the percentage of screen width the menu should occupy on larger screens.
```dart title:'restaurant_page.dart'
static const double largeScreenPercentage = 0.9;
static const double maxWidth = 1000;
```

2.  Calculate constrained width.
   - This function ensures that on larger screens the menu width is proportional to the screen size, up a maximum width.
```dart title:'restaurant_page.dart'
double _calculateConstrainedWidth(double screenWidth){
	return (
		screenWidth > desktopThreshold
		? screenWidth * largeScreenPercentage
		: screenWidth
	)
	.clamp(
		0.0,
		maxWidth;
	)
}
```

3. Build method.
   - With these changes, restaurant menu will dynamically adapt to both mobile and web screen sizes. The result is a a seamless user experience across devices.
```dart title:'restaurant_page.dart'
@override
Widget build(BuildContext context){
	final screenWidth = MediaQuey.of(context).size.width;
	final constrainedWidth = _calculateConstrainedWidth(screenWidth);
	
	return Scaffold(
		body: Center(
			child: SizedBox(
				width: constrainedWidth,
				child: _buildCustomScrollView(),
			),
		),
	);
}
```

4. Hot reload.
   ![[Pasted image 20251023225324.png]]
5. Try resizing web browser window. Will observe how elegantly restaurant menu adapts to various screen sizes.
   ![[Pasted image 20251023225518.png]]