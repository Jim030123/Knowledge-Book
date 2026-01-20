![[Pasted image 20251022172953.png]]

# ListView
- It's linear scrollable widget that arranges its children linearly and supports horizontal and vertical scrolling.
  ![[Pasted image 20251022174129.png]]
4 constructor:
1. ***children***
   That will construct every single in the list. Should us this of have a small number of children.
2. ***ListView.builder()***
   Takes in an ***IndexedWidgetBuilder*** and builds the list demand. It will only construct the children that are visible onscreen. Should use this if need to display a large or infinite number of items.
3. ***ListView.separated()***
   Takes 2 ***IndexedWidgetBuilders: itemBuilder*** and ***separatorBuilder***. Useful if want to place a separator widget between item.
4. ***ListView.custom()***
   gives more fine-grain control over child items.

# Setting Up the Explore Screen
![[Pasted image 20251022175410.png]]
- ***RestaurantSection***
  A horizontal scroll view that lets pan through different restaurants.
- ***CategorySection***
  A horizontal scroll view that pans through different categories.
- ***PostSection***
  A vertical scroll view that shows what friends up.

1. ***lib*** folder, create a new directory called ***screens***.
   ![[Pasted image 20251022175902.png]]
2. Create a new file called ***explore_page.dart***.
```dart title:'explore_page.dart'
import 'package:flutter/material.dart';
import '../api/mock_yummy_service.dart';

class ExplorePage extends StatelessWidget{
	// 1
	final mockService = MockYummyService();
	ExplorePage({super.key});
	
	// 2
	@override
	Widget build(BuildContext context){
		return const Center(
			child:Text(
				'Explore Page Setup'
				style: TextStyle(fontSize: 32.0),
				),
		);
	}
}
```

| Section | Description                                          |
| ------- | ---------------------------------------------------- |
| 1       | Create a ***MockYummyService*** - to mock responses. |
| 2       | Display a placeholder text.                          |
2. Building Restaurant Section
![[Pasted image 20251022182849.png]]

```dart title:'libs/components/restaurant_section.dart'
import 'package:flutter/material.dart';

// 1
import '../components/restaurant_landscape_card.dart';
import '../models/restaurant.dart';

class RestaurantSection extends StatelessWidget{
	
	// 2
	final List<Restaurant> restaurants;
	
	const RestaurantSection({
		super.key,
		required this.restaurants,
	});
	
	@override
	Widget build(BuildContext context){
		
		// 3
		return Padding(
			padding: const EdgeInsets.all(8.0),
			
			// 4
			child: Column(
				crossAxisAlignment: CrossAxisAlignment.start,
				children:[
					const Padding(
						padding: EdgeInsects.only(
						left: 16.0,
						bottom: 8.0,
						),
						
						// 5
						child: Text(
							'Food near me',
							style: TextStyle(
								fontSize: 24,
								fontWeight: FontWeight.bold,
							),
						),
					),
					
					// 6
					Container(
						height:400,
						color: Colors.grey,
					),
				],
			),
		);
	}
}
```

| Section | Description                                                                          |
| ------- | ------------------------------------------------------------------------------------ |
| 1       | Import restaurant card component and model.                                          |
| 2       | ***RestaurantSection*** - ***StatelessWidget*** that requires a list of restaurants. |
| 3       | ***build()*** - start by applying some padding.                                      |
| 4       | Add a ***Column*** to place widgets in a vertical layout.                            |
| 5       | ***Text*** - This is the header for the "Food near me" section.                      |
| 6       | ***Container*** - 400 pixels tall and set the background color to ***grey***.        |
3.  Import relevant .dart file.
```dart title:'explore_page.dart'
import '../components/restaurant_section.dart';
```
4.  Return the ***RestaurantSection***.
```dart title:'explore_page.dart'
return RestaurantSection(restaurants: restaurnats);
```

![[Pasted image 20251022202056.png]]

5.   Implement the ***ListView***.
```dart title:'restaurant_section.dart'
// 1
SizedBox(
	height: 23,
	
	// 2
	child: ListView.builder(
		
		// 3
		scrollDirection: Axis.horizontal,
		
		// 4
		itemCount: restaurants.length,
		
		// 5
		itemBuilder: (context, index){
			
			// 6
			return SizedBox(
				width: 300,
				
				// 7
				child: RestaurantLandscapeCard(
					restaurant: restaurants [index],
				),
			);
		},
	),
),
```

| Section | Description                                                                                                               |
| ------- | ------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***ListView*** - have a fixed a fixed height of 230 pixels. It acts as a container to constraint the height of the child. |
| 2       | ***ListView.builder*** - dynamically creates a list of items based on the provided data.                                  |
| 3       | Configure the items in the ***ListView*** to scroll horizontally.                                                         |
| 4       | Set the ***itemCount*** to be the length of restaurants list. Determine how many times the list should render.            |
| 5       | ***itemBuilder*** - return a widget for a given index of the list. It's invoked for each item in the restaurant list.     |
| 6       | Set a fixed width of ***300*** pixels for every restaurant card.                                                          |
| 7       | Create a ***RestaurantLandscapeCard*** and pass in the restaurant object based on the current index.                      |
6.  Import relevant .dart file.
```dart
import 'restaurant_landscape_card.dart';
```

![[Pasted image 20251022203758.png]]

# Nested List Views
## Column Approach
![[Pasted image 20251022203932.png]]
### The Pros and Cons using this views

| Pros                                                                                                         | Cons                                                                                |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| ***RestaurantSection*** and ***CategorySection*** are oj because the scroll direction is horizontal.  ****** | ***PostSection*** scrolls in the vertical direction, but it only small scroll area. |
- This approach has a bad user experience because the content area is too small. The ***Cards*** already take up most of the screen.

## Nested ListView Approach
- Show 1 big rectangle boundary. ***ExplorePage*** holds the parent ***ListView***. There are only 3 children ***ListViews***, can use the default constructor, which returns an explicit list of children
![[Pasted image 20251022204356.png]]
### The benefit of this approach
- The scroll area is a lot bigger, using 70 - 80% of the screen.
- Can view more of friends' posts.
-  Can continue to scroll ***RestaurantSection*** or ***CategorySection*** in the horizontal direction.
-  When scroll upward. Flutter listens to the scroll event of the parent ***ListView***.

``` dart title:'explore_page.dart'
// 1
return ListView(
	
	// 2
	shrinkWrap: true,
	
	// 3
	scrollDirection: Axis.vertical,
	
	// 4
	children: [
		RestaurantSection(restaurants: restaurants),
		Container(
			height: 300,
			color: Colors.green,
		),
		Container(
			height: 300,
			color: Colors.orangem
		),
	],
);
```

| Section | Description                                                               |
| ------- | ------------------------------------------------------------------------- |
| 1       | Initialize a scrollable list of widgets.                                  |
| 2       | ***shrinkWrap*** sizes the ***ListView*** based on its children's height. |
| 3       | The list scrolls vertically.                                              |
| 4       | The list contains 3 child list view widget.                               |
- Can still scroll the ***Cards*** horizontally. When scroll up and down, will notice the notice the entire area scrolls! 
![[Pasted image 20251022205929.png]]

1. Building Category Section
```dart title:'lib/components/category_section.dart'
import 'package:flutter/matrial.dart';
import '../models/food_category.dart';
import 'category_card.dart';

// 1
class CategorySection extends StatelessWidget{
	final List List<FoodCategory> categories;
	const CategorySection({
		super.key,
		required this.categories
	});
	
	@override
	Widget build(BuildContext context){
		// 2
		return Padding(
			padding: const EdgeInsets.all (8.0),
			
			// 3
			child: Column(
				crossAxisAlignment: CrossAxisAlignment.start,
				chilren:[
					
					// 4
					const Padding(
						padding: EdgeInsets.only(
							left: 16.0,
							bottom: 8.0
						),
						child: Text(
							'Categories',
							style: TextStyle(
								fontSize: 24,
								fontWeight: FontWeight.bold,
							),
						),
					),
					
					// 5
					SizedBox(
						height:275,
						child: ListView.builder(
							scrollDirection: Axis.horizontal,
							itemCount: categories.length,
							itemBuilder: (context, index){
							
								// 6
								return SizedBox(
									width: 200,
									child: CategoryCard(
										category:  categories[index],
									),
								);
							},
						),
					),
				],
			),
		);
	}
}
```

| Section | Description                                                                                                                            |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***CategorySection*** is a ***StatelessWidget***  - display a list of various food categories.                                         |
| 2       | ***Padding*** - to ensure 8.0 pixel space all arround                                                                                  |
| 3       | ***Column*** - used to ensure arrange child widget vertically                                                                          |
| 4       | Top of the column there is a title that displays "Categories"                                                                          |
| 5       | Horizontally-scrolling ***ListViewer.builder*** which displays a list of ***CategoryCard*** widgets, eacg with a height of 200 pixels, |
2. Add ***CategorySection*** in ***explore_page.dart***.
```dart title:'explore_page.dart'
CategorySection(categories: categories),
```
3. Import relevant .dart file.
```dart title:'explore_page.dart'
import '../components/category_section.dart';
```
![[Pasted image 20251022223349.png]]
4. Build post section structure. 
![[Pasted image 20251022223450.png]]
```dart title:'lib/components/post_section.dart'
import 'package:flutter/material.dart';
import '../models/post.dart';

// 1
class PostSection extends StatelessWidget{
	final List<Post> posts;
	const PostSection({
		super.key,
		required this.posts,
	});
	
	@override
	Widget build(BuildContext context){
		
		// 2
		return Padding(
			padding: const EdgeInsets.all(8.0),
			
			// 3
			child: Column(
				crossAxisAlignment:CrossAxisAlignment.start,
				children:[
					const Padding(
						padding: EdgeInsets.only(
							left: 16.0,
							bottom: 8.0
						),
						
						// 4
						child: Text(
							'Friend\'s Activity'
							style: Textstyle(
								fontSize: 2,
								fontWeight: FontWeight.bold,
							),
						),
					),
				],
			),
		);
	}

}
```

| Section | Description                                                                                  |
| ------- | -------------------------------------------------------------------------------------------- |
| 1       | ***PostSection*** - stateless widget and requires list of ***Posts***.                       |
| 2       | Apply overall padding of 8.0 pixels.                                                         |
| 3       | Create a ***Column*** to position the ***Text*** followed by the posts in a vertical layout. |
| 4       | Create the ***Text*** widget header.                                                         |
6. Build Post List View
```dart title:'Post List View'
// 1
ListView.separated(
	
	// 2
	primary: false,
	
	// 3
	shrinkWrap: true,
	
	// 4
	scrollDirection: Axis.vertical,
	
	// 5
	physics: const NeverScrollablePhysics(),
	itemCount: posts.length,
	
	// 6
	itemBuilder: (context, index){
		return PostCard(post: posts[index]);
	},
	separatorBuilder: (context, index){
		
		// 7
		return const SizedBox(height: 16);
	},	
),
```

| Section | Description                                                                                                                                                                        |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***ListView.separated*** with 2 ***IndexWidgetBuilder*** callbacks                                                                                                                 |
| 2       | Since nesting 2 list view, it's a good idea to set primary to ***false***.                                                                                                         |
| 3       | Set ***shrinkWrap*** to ***true*** to create a ***fixed-length*** scrollable list of items. This gives it a fixed height. If this were ***false***, get an unbounded height error. |
| 4       | Make this list view vertically scrollable.                                                                                                                                         |
| 5       | Set the scrolling physics to ***NeverScrollableScrollPhysics.***<br><br>Set ***primary*** to false, it's a good idea to disable the scrolling for this list view.                  |
| 6       | For every item in the list, create a ***Post*** widget.                                                                                                                            |
| 7       | For every item, also create a ***SizedBox*** to space each item by 16 pixels.                                                                                                      |

7. Add ***PostSection***.
```dart title:'explore_page.dart'
PostSection(posts:posts),
```

8. Import relevant .dart file.
```dart title:'explore_page.dart'
import '../components/post_section.dart';
```

| Light Mode                           | Dark Mode                            |
| ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20251023001506.png]] | ![[Pasted image 20251023001650.png]] |
# Other Scrollable Widgets
- CustomScollView
  A widget that creates custom scroll effects using slivers. To collapse navigation header on scroll.
  ![[Pasted image 20251023001941.png]]
- PageView
  A scrollable widget that scrolls page by page, making it perfect for an onboarding flow. It also supports a vertical scroll direction.
  ![[Pasted image 20251023002154.png]]
- StaggeredGridView
  That supports columns and rows of varying sizes. If need to support dynamic height and custom layouts that is most suitable.
  ![[Pasted image 20251023002312.png]]
- AlwaysScrollableScrollPhysics
- BouncingScrollPhysics
- ClampingScrollPhysics
- FixedExtentScrollPhysics
- NeverScrollableScrollPhysics
- PageScrollPhysicsRange
- MaintainingScrollPhysics