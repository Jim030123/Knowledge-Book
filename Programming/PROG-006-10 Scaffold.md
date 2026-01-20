To implement all basic visual layout structure need. It's composed of the following parts:
- AppBar
- BottomSheet
- BottomNavigationBar
- Drawer
- FloatingActionButton
- SnackBar

![[Pasted image 20251020123139.png]]
# Home Widget
- Build large-scale apps, will start to compose a staircase of widgets. Widgets composed of other widgets can get really long and messy. Good idea to break widgets into separate files for readability.

```dart title:'lib/home.dart'
import 'package:flutter/material.dart';
import 'components/theme_button.dart';
import 'constants.dart';

class Home extends StatefulWidget{
	const Home({
		super.key,
		required this.changeTheme,
		required this.changecolor,
		required this.colorSelected,	
	});
	
	final void Function(bool useLightMode) changeTheme;
	final void Function(int value) changeColor;
	final ColorSelection colorSelected;
	
	@override
	State<Home> createState() => _HomeState();
}

class _HomeState extends State<Home> {
	
	@override
	Widget build(BuildContext context){
	
		return Scaffold(
				appbar: AppBar(
				elevation: 4.0
				backgroundColor: Theme.of(context).colorScheme.background,
				actions:[
					ThemeButton(
						changeThemeMode: widget.changeTheme,
					),
					ColorButton(
						changeColor: widget.changeColor,
						colorSelected: widget.colorSelected,
					),
				],
			),	
		);
	}
}
```

1. Import relevant .dart 
```dart title:'main.dart'
import 'home.dart';
```

2.  Replace ***home: Scaffold***
```dart title:'main.dart'
home: Home(
	changeTheme: changeThemeMode,
	changeColor: changeColor,
	colorSelected: colorSelected,
),
```

