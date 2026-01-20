- Applying the right navigation structure makes it easy for users to navigate the information in app.
# BottomNavigationBar
1. Track current tab
```dart title:'home.dart'
int tab = 0;

```

2. Define a list of tabs the user can navigate between it.
```dart title:'home.dart'
List<NavigationDestination> appBarDestination = const [
	NavigationDestination(
		icon: Icon(Icons.credit_card),
		label: 'Catergory',
		selectedIcon: Icon(Icons.credit_card),
	),
	NavigationDestination(
		icon: Icon(Icons.credit_card),
		label: 'Post',
		selectedIcon: Icon(Icons.credit_card),
	),
	NavigationDestination(
		icon: Icon(Icons.credit_card),
		label: 'Restaurant',
		selectedIcon: Icon(Icons.credit_card),
	),
]
```

3. Add bottom navigation bar
```dart title:'home.dart'
// 1
bottomNavigationBar: NavigationBar(
	
	// 2
	selectedIndex: tab,
	
	// 3
	onDestinationSelected: (index){
		setState((){
			tab = index;
		});
	},
	
	// 4
	destinations: appBarDestinations,
)
```


| Section | Description                                              |
| ------- | -------------------------------------------------------- |
| 1       | Assigns ***NavigationBar*** to ***bottomNavigationBar*** |
| 2       | Set the active ***tab*** using ***selectedIndex***       |
| 3       | Updates the active tab on user selection.                |
| 4       | Defines the lists of tabs with ***appBarDestinations***  |
![[Pasted image 20251020130505.png]]

# Navigating between Pages
1.  This contains a list of container with different colors. Will replace each one with a unique card soon.
```dart title:'home.dart'
final pages = [
	Container(color: Colord.red),
	Container(color: Colord.green),
	Container(color: Colord.blue),
]
```

2. Displays 1 widget from pages based on the tab index, preserving the state of all widgets in stack.
```dart title:'home.dart'
body: IndexedStack(
	index: tab,
	children: pages,
),
```

3. Restart the app.
![[Pasted image 20251020132100.png]]

# Navigating.push
```dart title:'lib/components/restaurant_landscape_card.dart'
// 1
Navigator.push(
	
	// 2
	context,
	
	// 3
	MaterialPageRoute(
		// 4
		builder: (context) => 
			RestaurantPage(
				restaurant: widget.restaurant,
			)
	),
);
```

| Section | Description                                                                           |
| ------- | ------------------------------------------------------------------------------------- |
| 1       | ***Navigator.push*** start the navigation to a new screens                            |
| 2       | ***context*** tells Flutter where the navigation starts from within the widget tree.  |
| 3       | ***MatrialPageRoute*** used to create a route with a standard transition animation.   |
| 4       | Navigate to RestaurantPage and pass in the current restaurant object to be displayed. |
