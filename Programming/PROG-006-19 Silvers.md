- Mobile view
  ![[Pasted image 20251023002605.png]]
- Web view
  ![[Pasted image 20251023002626.png]]
# ***RestaurantItem***'s component
![[Pasted image 20251023002734.png]]
- Title
- Description
- Price
- Popularity indicator
- Image
- Add button, to add an item to the cart.

# Slivers
- Provide various ways to lay out a list of children in a scrolling view.
- It give developers fine-grained control over scroll behaviour, animation and the geometry of scrolling elements, making the building blocks for complex scrollable areas.
  ![[Pasted image 20251023003159.png]]
# Types of Slivers
- Slivers operate within the ***CustomScrollView*** which allows them to combine different scrolling behaviours in a single scroll view.
- ***SliverList*** and ***SliverGrid*** are the sliver equivalents of ***ListView*** and ***GridView***.
- ***SliverAppBar*** is a highly flexible app bar that can expand, collapse, float and snap as scroll.
- ***SliverToBoxAdapter*** allows to place a single non-silver widget within a ***CustomScrollView***.
- ***SilverFillRemaining*** and ***SilverViewport*** lett size children based the remaining space in the viewpoint.
# Building the Restaurant Page
- When users click on a restaurant in the ***Food Near Me*** section, app will direct them to this page that displays the restaurant's menu.
```dart title:'lib/screens/restaurant_page.dart'
// 1
import 'package:flutter/material.dart';
import '../models/restaurant.dart';

// 2
class RestaurantPage extends StatefulWidget{
	final Restaurant restaurant;
	
	// 3
	const RestaurantPage({
		super.key,
		required this.restaurant.
	});
	
	@override
	State<RestaurantPage> createState() => _RestaurantPageState();
}

// 4
class _RestaurantPageState extends State<RestaurantPage>{
	@override
	Widget build(BuildContext context){
		
		// 5
		return Scaffold(
			body: Center(
				child: Text(
					'Restaurant Page',
					style: TextStyle(fontsize: 16.0),
				),
			),
		);
	}
}
```

| Section | Description                                                                                                                          |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| 1       | Import necessary package and classes.                                                                                                |
| 2       | Define a new class ***RestaurantPage*** as a ***StatefulWidget***.                                                                   |
| 3       | ***RestaurantPage*** takes in a ***restaurant*** object which contains data such as restaurant info and menu to display on the page. |
| 4       | ***_RestaurantPageState*** is a class that holds the state for ***RestaurantPage.***                                                 |
| 5       | ***build() method*** currently returns a temporary placeholder text that displays ***Restaurant*** page.                             |
# Building a Silver for the RestaurantPage
```dart title:'restaurant_page.dart'
CustomScrollView _buildCustomScrollView(){
	return CustomScrollView(
		slivers: [
			SliverToBoxAdapter(
			 child: Container(
				 height: 200.0,
				 color: Colors.red,			 	
				 ),
			 ),
			 SliverToBoxAdapter(
				 child:Container(
					 height: 300.0,
					 color: Colors.grren,
				 ),
			 ),
			 SilverFillRemaining(
				 child: Container(
					color: Colors.blue, 
				),
			 ),
		],
	);
}
```

This function returns a ***CustomScrollView***, a versatile widget that coordinates a variety of silver widgets to create a multifaceted scrolling interface:
- ***SliverToBoxAdpater*** - handy widget that adapts a standard, non-silver widget for use within a slicer list.
- ***SilverFillRemaining*** - sizes its children to occupy the available remaining space in the viewport, perfect for expanding content areas.
1. Replace following child in the ***ScrollView***.
```dart title:'restaurant_page.dart'
child:_buildCustomScrollView
```

2. Hot reload.
   ![[Pasted image 20251023093303.png]]
# Building a Silver App Bar
- The users scrolls up, the app bar will remain at the top and shrink the regular app bar size.
  ![[Pasted image 20251023104950.png]]
- 1. Build the Silver App Bar.
```dart title:'restaurant_page.dart'
SliverAppBar _buildSliverAppBar(){
	
	// 1
	return SilverAppBar(
	
		// 2
		pinned:true,
		
		// 3
		expandedHeight: 300.0,
		
		// 4
		flexibleSpace: FlexibleSpaceBar(
		
			// 5
			background: Center(
			
				// 6
				child: Padding(
					padding: const EdgeInsets,only(
						left: 16.0,
						right: 16.0,
						top: 64.0,
					),
					
					// 7
					child: Stack(
						children:[
						
							// 8
							Container(
								margin: const EdgeInsets.only(bottom: 30.0),
								decoration: BoxDecoration(
									color: Color.gret,
									borderRadius: BorderRadius.circular(16.0),
									// 9
									image: DecorationImage(
										image: AssetImage(widget.restaurant.imageUrl),
										fix: BoxFit.cover,
									),
								),
							),
							
							// 10
							const Postioned(
								bottom: 0.0,
								left: 16.0,
								child: CircleAvatar(
									radius: 30,
									child: Icon(
										Icon.store,
										color:Colors.white,
									),
								),
							),
						],
					)
				)
			)
		)
	)
}
```

| Section | Description                                                                          |
| ------- | ------------------------------------------------------------------------------------ |
| 1       | The function returns a ***SliverAppBar*** widget that creates a collapsible app bar. |
| 2       | Keep the app bar pinned at the top of the view.                                      |
| 3       | Specify expandedHeight of 300.0 pixels for maximum height when fully expanded.       |
| 4       | ***FlexibleSpaceBar*** - the collapsible part of the app bar.                        |
| 5       | Within the ***FlexibleSpaceBar***, set a background widget.                          |
| 6       | Apply some padding to creates internal spacing for the background.                   |
| 7       | Arrange elements using a ***Stack***.                                                |
| 8       | Create a ***Container*** for the backdrop with styling.                              |
| 9       | Show the restaurant image as a background using ***DecorationImage***.               |
| 10      | Place a circular icon at the bottom left using ***Positioned*** widget.              |

2. Add the app bar to custom scroll view
```dart title:'restaurant_app.dart'
_buildSilverAppBar(),
```

3. Hot reload.
   ![[Pasted image 20251023111922.png]]
# Building the Restaurant Info Section
![[Pasted image 20251023112235.png]]
```dart
// 1
SliverToBoxAdapter _buildInfoSection() {
	
	// 2
	final textTheme = Theme.of(context).textTheme;
	
	// 3
	final restaurant = widget.restaurant;
	
	// 4
	return SliverToBoxAdapter(
		
		// 5
		padding: const EdgeInsets.all(16.0),
		
		// 6
		child: Column(
			crossAxisAlignment: CrossAxisAlignment.start,
			children:[
				
				// 7
				Text(
					restaurant.name,
					style: textTheme.headlineLarge.
				),
				Text(
					restaurant.address, 
					style: textTheme.bodySmall,),
				Text(
					rstaurant.getRatingAndDistance(),
					style: textTheme.bodySmall,
				),
				Text(
					restaurant.attributes, 
					style: textTheme.labelSmall,
				),	
			],
		),
	);
}
```

| Section | Description                                                                             |
| ------- | --------------------------------------------------------------------------------------- |
| 1       | ***buildInfoSection()*** - To construct a UI section for the restauran's details.       |
| 2       | Retrieve the application's text styles for consistent theming.                          |
| 3       | Access the restaurant's data passed to the widget.                                      |
| 4       | ***SliverToBoxAdapter*** - To enable a column of text widgets a silver-based layout.    |
| 5       | Apply padding around the column for spacing.                                            |
| 6       | Create a column and align text elements to the start of the column.                     |
| 7       | Display the restaurant's name, address, rating and attributes with styled text widgets. |
2. Add Restaurant Info Section
```dart title:'restaurant_page.dart'
_buildInfoSection(),
```

3. Hot reload. 
   ![[Pasted image 20251023114226.png]]