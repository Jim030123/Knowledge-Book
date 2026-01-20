
```dart
import 'package:flutter/material.dart';

import 'package:flutter/cupertino.dart'
```

![[Pasted image 20251020085852.png]]

# Theme Class
![[Pasted image 20251020090218.png]]

- ***ColorSection*** enum enables users to select and customize the app's appearance/
```dart title:'lib/constants.dart'
import 'package:flutter/material.dart'

// 1
enum ColorSelection{
	deepPurple('Deep Purple', Colors.deepPurple),
	purple('Purple', Colors.purple),
	indigo('Indigo', Colors.indigo),
	blue('Blue', Colors.blue),
	teal('Teal', Colors.teal),
	green('Green', Colors.green),
	yellow('Yellow', Colors.yellow),
	orange('Orange', Colors.orange),
	deepOrange('Deep Orange', Colors.orange),
	pink('Pink', Colors.pink);
	
	// 2
	const ColorSelection(
		this.label,
		this.color,
	);
	
	final String label;
	final Color color;
}
```

| Section | Description                            |
| ------- | -------------------------------------- |
| 1       | Structured color options.              |
| 2       | Each has a ***label*** and ***color*** |
# Applying the Theme

- Import predefined color themes

```dart title:'main.dart'
import 'constants.dart'
```

- Establish default theme mode and primary color
```dart title:'main.dart'
ThemeMode themeMode = ThemeMode.light
	ColorSelection colorSelected = ColorSelection.pink;
```

- Theme configurations. Sets the global theme mode. It defines both light and dark themes utilizing the color you previously specified, ensuring a cohesive and adaptive visual apperance across your app..
```dart title:'main.dart'
themeMode: themeMode,
theme: ThemeData(
	colorSchemeSeed:colorSelected.color,
	useMaterial3: true,
	brightness: Brightness.light,
),

darkTheme: ThemeData(
	colorSchemeSeed: colorSelected.color,
	useMaterial3: true,
	brightness: Brightness.dark,
)
```

- Need to remove ***const*** from the following 2 location.
```dart title:'main.dart'
runApp(const Yummy());

...

const Yummt({super.key});
```

# Change theme variation
![[Pasted image 20251020095753.png]]![[Pasted image 20251020095812.png]]

# Switching Themes
- Need to manage state by converting the ***Yummy*** widget to a ***StatefulWidget***.
1. Right click the class name ***Yummy***. Then click ***Show Context Actions*** from the menu that pops up:
![[Pasted image 20251020100044.png]]

2. Select ***Convert to StatefulWidget***.
![[Pasted image 20251020102856.png]]

```dart title:'main.dart'
// 1
class Yummy extends StatefulWidget{
	
	...
	
	@override
	State<Yummy> createState() => _Yummystate();
}

// 2
class _YummyState extends State<Yummy>{
	
	...
	
	@override
	Widget build(BuildContext context){
	}
}
```

| Section | Description                                                                                                                  |
| ------- | ---------------------------------------------------------------------------------------------------------------------------- |
| 1       | The refactor converted Yummy from a ***StatelessWidget*** into a ***StatefulWidget***.<br><br>It added a ***createState()*** |
| 2       | Refactor also created the  ***\_YummyState*** class. It stores mutable data that can change over the lifetime of the widget. |
# Implementing Theme State Changes
```dart title:'main.dart'
class _YummyState extends State<Yummy> {

...

	void changeThemeMode(bool useLightMode){
	
		// 1
		setState((){
			themeMode = useLightMode
				? ThemeMode.light 
				: ThemeMode.dark; 
		});
	}
	
	void changeColor(int value){
		setState((){
		
		// 2
		colorSelected = ColorSelection.values[value];
		});
	}
}
```

| Section | Description                                |
| ------- | ------------------------------------------ |
| 1       | Update theme mode based on user selection. |
| 2       | Update theme color based on user selection |
# Creating a Theme Button
```dart title:'theme_button.dart'
import 'package:flutter/material.dart';

class ThemeButton extends Stateless Widget{
	// 1
	const ThemeButton({
		Key? key,
		required this.change ThemeMode,
	}) : super(key: key);
	
	// 2
	final Function changeThemeMode;
	
	@override
	Widget build(BuildContext context){
		
		// 3
		final isBright = Theme.of(context).brightnes == Brightness.light;
		
		// 4
		return IconButton(
			? const Icon(Icons.dark_mode_outlined)
			: const Icon(Icons.light_mode_outlined),
		
		// 5
		onPressed: () => changeThemeMode(!isBright),
		);
	}
}


```

| Section | Description                                                                                                                                                                                                                     |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***ThemeButton*** - initialized with a construcutor requireing a function ***changeThemeMode*** parameter.                                                                                                                      |
| 2       | ***changeThemeMode*** - callback function passed as parameter to be called when the user presses the button. This function notifies the parent widget about the brightness change, enabling it to adjust the theme accordingly/ |
| 3       | ***isBright*** - Boolean that checks wheteher the current theme brightness is light.                                                                                                                                            |
| 4       | ***IconButton*** - that will display light or dark mode based on the ***isBright Boolean***.                                                                                                                                    |
| 5       | ***IconButton*** when pressed, toggles the theme brightness by invoking ***changeThemeMode***.                                                                                                                                  |
# Creating the Color Button
```dart title:'lib/component/color_button.dart'
import 'package:flutter/material.dart';
import'../constants.dart';

class ColorButton extends StatelessWidget{
	
	// 1
	const ColorButton({
		super.key,
		required this.changeColor,
		required this.colorSelected,
	});
	
	// 2
	final void Function(int) changeColor;
	final ColorSelection colorSelected;
	
	@override
	Widget build(BuildContext context){
	
		// 3
		return PopMenuButton(
			icon: Icon(
				Icons.opacity_outlined,
				color: Theme.of(context).colorScheme.onSurfaceVariant,
			),
			
			// 4
			shape: RoundedRectangleBorder(
				borderRadius: BorderRadius.circular(10),
			),
			
			// 5
			itemBuilder: (context){
			
				// 6
				return List.generate(
					ColorSelection.values.length,
					(index){
						final currentColor = ColorSelectin.values[index];
						
						// 7
						return PopupMenuItem(
							value: index,
							enabled: currentColor != colorSelected,
							children: [
								Padding(
									padding: const EdgeInsets.only(left:10),
									child: Icon(
										Icons.opacity_outlined,
										color: currentColor.color,
									),	
								),
								Padding(
									padding: const EdgeInsets.only(left: 20),
									child: Text(currentColor.label),
								),
							],
						);},
				);
			},
		
		// 8
		onSelected: changeColor,
		);
	}
}
```

| Section | Description                                                                                                         |
| ------- | ------------------------------------------------------------------------------------------------------------------- |
| 1       | Initializes ***ColorButton*** with the required callback and color.                                                 |
| 2       | Property ***changeColor*** - callback to handle the color selection and ***colorSelected*** is the color selection. |
| 3       | Create s a button that display a menu.                                                                              |
| 4       | Applies rounded corners to the popmenu.                                                                             |
| 5       | Generates the menu items.                                                                                           |
| 6       | Creates a list of color options from ***ColorSelection***.                                                          |
| 7       | Configures each menu item with an icon and text.                                                                    |
| 8       | Calls ***changeColor*** when an item is selected.                                                                   |
# Adding Action Buttons to the App Bar
1.  Import the relevant .dart file.
```dart title:'main.dart'
import 'components/theme_button.dart';
import 'components/color_button.dart';
```
2. Add action buttons.
```dart title:''
action:[
	ThemeButton(
		changeThemeMode: changeThemeMode,
	),
	ColorButton(
		changeColor:changeColor,
		colorSelected: colorSelected,
	),
],
```
3. Hot restart, switch between light and dark mode.
![[Pasted image 20251020122729.png]]