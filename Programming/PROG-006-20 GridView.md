- A 2D array of scrollable widgets. Similar to its linear counterpart, the ***ListView*** supports both horizontal and vertical scrolling, but it arranges its children in a grid format.
  ![[Pasted image 20251023115317.png]]
- ***GridView.count()***
  Great fir creating a grid with a fixed number of tiles in the cross-axis.
- ***GridView.builder()***
  Similarly to ListView.builder() by lazily constructing items as they're scrolled into the viewport, ideal for displaying a large or indeterminate number of items.
- ***GridView.custom()***
  Offers the highest level of customization, letting use a custom ***SliverGridDelegate*** fpr precise
- ***GridView.extent()***
  Allow to specify the maximum extent of the tiles in the cross-axis, it will determine the number of tiles in each row or column dynamically based on the available space.
## Parameters
- ***crossAxisSpacing***
  The spacing between each child in the cross-axis.
- ***mainAxisSpacing***
  The spacing between each child on the main axis.
- ***crossAxisCount***
  The number of children in the cross-axis.
- ***shrinkWrap***
  Controls the fixed scroll area size.
- ***physics***
  Control how the scroll view responds to user input.
- ***primary***
  Helps Flutter determine which scroll view is the primary one.
- ***scrollDirection***
  Controls the axis which the view will scroll.
# Understanding the Cross and Main Axis
- The main axis always corresponds to the scroll direction. 
- If scroll direction is horizontal, can think of this as a ***Row***. The main axis represents the horizontal direction.
  ![[Pasted image 20251023121644.png]]
- If scroll direction is vertical, can think of it as a ***Column***. The main axis represents the vertical direction.
  ![[Pasted image 20251023121737.png]]
# Understanding Grid Delegates
- It help you figure out the spacing and the number of columns to use to lay out the children in a ***GridView***.
Flutter provides 2 delegates can use out of the box:
- ***SilverGridDelegateWithFixedCrossAxisCount***
  That has a fixed number of tiles along the cross-axis.
- ***SilverGridDelegateWithMaxCrossAxisExtent***
  Creates a layout with tiles that have a maximum cross-axis extent.

# Building the Grid View Section
- GridView is a great widget to make app responsive on different screens.
- Depending on the screen width, could have the grid view display 1 or 2 columns to show more information and leverage the real estate of a bigger screen.
  ![[Pasted image 20251023123150.png]]
1. ***buildGridItem*** in ***restaurant_page.dart***.
   - This function takes an index and uses it to access a specific item from the restaurant's menu. Creates a ***RestaurantItem*** widget for that menu item.
   - By wrapping the widget in an ***InkWell***, lay the groundwork for interactive functionality such as opening a detail view in a bottom sheet upon tapping.
```dart title:'restaurant_page.dart'
Widget _buildGridItem(int index){
	final item = widget.restaurant.items[index];
	return Inkwell(
		onTap: (){
		},
		child: RestaurantItem(item:item),
	);
}
```

2. Import at the top of the file:
```dart title:'restaurant_page.dart'
import '../components/restaurant_item.dart';
```

3. Building the Section Title.
```dart title:'restaurant_page.dart'
Widget _sectionTitle(String title){
	return Padding(
		padding: const EdgeInsets.all(8.0),
		child: Text(
			title,
			style: const Text(
				fontSize: 24,
				fontWeight: FontWeight.bold,
			),
		)
	);
}
```

4. Building the Grid View
```dart titlw:'restaurant_page.dart'
// 1
GridView _buildGridVew(int columns){
	
	// 2
	return GridView.builder(
		padding: const EdgeInsect.all(0),
		
		// 3
		gridDelegate: SilverGridDelegateWithFixedCrossAxisCount(
			mainAxisSpacing: 16,
			crossAxisSpacing: 16,
			childAspectRatio: 3.5,
			crossAxisCount: columns,
		),
		
		// 4
		itemBuilder: (context, index) => _buildGridItem(index),
		
		// 5
		itemCount: widget.restaurant.items.length,
		
		// 6
		shrinkWrap: true,
		
		// 7
		physics: const NeverScrollableScrollPhysics(),
	);
}
```

| Section | Description                                                                                                                                                            |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | The function ***_buildGridView()*** accepts the number columns as a parameter.<br><br>This is used to determine the number of columns to display on different devices. |
| 2       | ***GridView.builder()*** - Used for efficient, on-demand building of grid's column count and spacing.                                                                  |
| 3       | ***SliverGridDelegateWithFixedCrossAxisCount*** - Define the grid's column count and spacing.                                                                          |
| 4       | Each grid item is built ***via_buildGridItem()***, called within the ***itemBuilder *** callback.                                                                      |
| 5       | Set the number of items to display in the grid.                                                                                                                        |
| 6       | ***shrinkWrap: true*** - allow the ***GridView*** to size itself according to its children vertically.                                                                 |
| 7       | Set the physics to ***NeverScrollableScrollPhysocs*** - to prevent scrolling within the grid itself.                                                                   |
4. Building the Grid View ***Sliver*** Section. Add ***Desktop Therehold***.
   - This constant is used to determine whether to adapt the restaurant menu layout to big to small screens.
```dart title:'restaurant_page.dart'
static const desktopThreshold = 700;
```

5. Need to calculate the number of columns depending on the screen's width.
   - Depending on the screen width the screen width the function will either return 2 or 1.
```dart title:'restaurant_page.dart'
int calculateColumnCount(double screenWidth){
	return screenWidth > desktopThreshold? 2:1
}
```

6. Build Grid View Section 
```dart title:'restaurant_page.dart'
// 1
SliverToBoxAdapter _buildGridViewSection(String title){
	
	// 2
	final columns = calculateColumnCount(MediaQuery.of(context).size.width);
	
	// 3
	return SilverToBoxAdapter(
		
		// 4
		child: Container(
			padding: const EdgeInsets.all(16.0),
			
			// 5
			child: Column(
				crossAxisAlignment: crossAxisAlignment.start,
				children:[
					
					// 6
					_sectionTitle(title),
					
					// 7
					_buildGridView(columns),
				],
			),
		),
	);
}
```

| Section | Description                                                    |
| ------- | -------------------------------------------------------------- |
| 1       | Create a section with a title and grid view.                   |
| 2       | Calculate the number of columns based on the screen's width.   |
| 3       | Build a ***SilverToBoxAdapter*** to embed a non-silver widget. |
| 4       | Initialize a container for content with some padding.          |
| 5       | Set up a vertical layout with a ***Column*** widget.           |
| 6       | Add a section title using a custom method.                     |
| 7       | Add a grid view with the specified number of columns.          |
7.  Add menu item grid view section.
```dart title:'restaurant_page.dart'
_buildGridViewSection('Menu'),
```

8. Hot reload.
   ![[Pasted image 20251023221816.png]]
