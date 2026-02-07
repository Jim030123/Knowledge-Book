# Stateless Widget
- The state or properties of a stateless widget can't be altered once it's built. When properties don't need to change over time.
- The widget is inserted into the widget tree for the first time.
- The state of a dependency or inherited widget - ancestor node - changes.
 
![[Pasted image 20251020214611.png]]

# Stateful Widgets
- Preserve state, which is useful when parts of UI need to change dynamically.
- - It store their mutable in separate ***State*** class. Every stateful widget must override and implement ***createState()***.
>[!note] Example
>Favourite button to toggle a simple Boolean value on and off.

![[Pasted image 20251020214928.png]]
## State Object Lifecycle
- Every widget's ***build()*** method takes a ***BuildContext*** as an argument. Can access the ***element*** for any widget through the ***BuildContext***.
![[Pasted image 20251020215454.png]]

1. When assign the build context to the widget, an internal flag, mounted, is set to ***true***.
2. ***initState()*** is the first method called after a widget is created. This is similar to ***onCreate()*** in Android or ***viewDidLoad()*** in iOS.
3. First time the framework builds a widget, it calls ***didChangeDependencies()*** after ***initState()***. It might call ***didChangeDependencies()*** again if your state object depends on an ***inherited widget*** that has changed. There's more on inherited widgets below.
4. The framework calls ***build()*** after ***didChangeDependencies()***. This function is the most important for developers because it's called every time a widget needs rendering. Every widget in the tree triggers a ***build()*** method recursively.
5. The framework calls ***didUpdateWidget(_)*** when a parent widget makes a change or needs to redraw the UI. When that happens, will get the ***oldWidget*** instance as a parameter, can compare it with current widget and do any additional logic.
6. Whether want to modify the state in widget, call ***setState()***. The framework then marks the widget as ***dirty*** and triggers a ***build()*** again.
7. When remove the object from the tree, the framework calls deactivate().
8. The framework calls dispose() when permanently remove the object and its state from the tree.
>[!note] 
>Asynchronous code should always check if the mounted property is true before calling ***setstate()***, because the widget may no longer be part of the widget tree.
## Adding Stateful Widgets
- ***RestaurantLandscapeCard*** is currently a ***StatelessWidget***, which means the widget can't manage state dynamically. To fix this, will change this card into a ***StatefulWidget***.
1. Open ***restaurant_landscape_card.dart*** and right click ***RestaurantLandscapeCard***.
2. Click ***Show Content Actions*** from the menu that pops up. ![[Pasted image 20251020221620.png]]
3. Select ***Convert to StatefulWidget***.![[Pasted image 20251020221856.png]]
```dart  title:'restaurant_landscape_card.dart'
class RestaurantLandscapeCard extends StatefulWidget{
	...
	
	@override
	State<RestaurantLandscapeCard> createState() => _RestaurantLandscapeCardState();
}

class _RestaurantLandscapeCard extebds State<RestaurantLandscapeCard>{
	@override
	Widget build(BuildContext context){
	
		...
		
	}
	
}

```
- Refactor converted ***RestaurantLandscapeCard*** from a ***StatelessWidget*** into a ***StatefulWidget***. It added a ***createState()*** implementation.
- The refactor also created the ***_RestaurantLandscapeCardState*** state class. It stores mutable data that change can change over the lifetime of the widget.
## Implementing Stateful Widgets
```dart
bool _isFavourited = false;
```

```dart title:'restaurant_landscape_card.dart'
// 1
child: Stack(
	fit:StackFit.expand,
	children: [
		
		// 2
		Image.asset(
			widget.restaurant.imageUrl,
			fit: BoxFit.cover,
		),
		
		// 3
		Positioned(
			top: 4.0,
			right: 4.0,
			child: IconButton(
				
				// 4
				icon: Icon(_isFavourited
					? Icons.favourite
					: Icons.favourite_border,
				),
				iconSize: 30.0,
				color: Colors.red[400],
				
				// 5
				onPressed: (){
					setState((){
						_isFavourited = !_isFavourited;
					});
				},
			),
		),
	],
)
```


| Section | Description                                                                                                                                                   |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***Stack*** - Overlays multiple elements. It's used to layer a favourite button over a restaurant's images, ensuring utilize the full space.                  |
| 2       | The restaurant's image is displayed, with a scaling set to fill the entire container.                                                                         |
| 3       | ***IconButton*** - positioned at the top-right corner of the image, serving as the favourite action.                                                          |
| 4       | Icon displayed depends on the ***_is_Favourited*** status.<br><br>A filled heart represents a favourite, while an outlined heart indicates otherwise.         |
| 5       | Tapping the favourite button toggles ***_is_Favourite*** state, effectively switching between the 2 heart icons. This is done via a call to ***setState()***. |

![[Pasted image 20251022171425.png]]

## Examining the Widget Tree
- Recall that the framework will construct the widget tree, for every widget instance, create an element object.
  ![[Pasted image 20251022171647.png]]
- When user taps the heart button, ***setState()*** run and toggles ***_isFavourited*** to true. Internally, the state object marks this element as ***dirty***. That trigger a call to ***build()***.
  ![[Pasted image 20251022171859.png]]
- It removes the old widget and replaces it with a new instance of ***Icon*** that contains the filled heart icon.
  ![[Pasted image 20251022172012.png]]
- The framework only updates the widgets that need to be changed.

# Inherited Widget
- Let access state information from the parent elements in the tree hierarchy.
- To pass the data down a parameter on each nested widget.
  ![[Pasted image 20251022172426.png]]
- Lifting state up - adopting an inherited widget in tree. Can reference the data from any its descendants.
>[!note] Example
>- Accessing a ***Theme*** object to change the UI's appearance.
>- Calling an API service object to fetch data from the web.
>- Subscribing to streams to update the UI according to the data received.