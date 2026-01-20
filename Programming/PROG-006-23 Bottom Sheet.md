1. Building a bottom sheet.
```dart title:'lib/screens/restaurant_page.dart'
// 1
void _showButtomSheet(Item iterm){
	
	// 2
	showModaBottomSheet<void>(
		
		// 3	
		isScrollControlled: true,
		
		// 4
		context: context,
		
		// 5
		constraints: const BoxConstraints(maxWidth: 480),
		
		// 6		
		builder: (context) => Container(
			color: Colors.red,
			height: 480,
		),
	);
}
```

| Section | Description                                                                                                         |
| ------- | ------------------------------------------------------------------------------------------------------------------- |
| 1       | ***_showBottomSheet()*** that accepts the selected menu item to display in the bottom sheet.                        |
| 2       | Create a modal bottom sheet that slides up from the bottom.                                                         |
| 3       | ***_isScrollControlled: true*** - to allow the bottom sheet to have dynamic height.                                 |
| 4       | Pass in the current context to display the bottom sheet.                                                            |
| 5       | Constraint the bottom sheet to have a max width of ***480***.<br><br>To support responsive UI on mobile or desktop. |
| 6       | ***builder()*** - return the details to display                                                                     |
2. Presenting the bottom sheet.
   ![[Pasted image 20251024121012.png]]
```dart title:'restaurant_page.dart'
Widget _buildGridItem(int index){
	final item = wodget.restaurant. items[index];
	
	return InkWell(
		onTap: () => showBottomSheet(item),
		child: RestaurantItem(item: item),
	);
}
```

3. Building Item Details
   When tap on a specific menu item shows a bottom sheet to focus on that specific item.
```dart title:'lib/components/item_details.dart'

import 'package:flutter/material.dart';
import '../models/cart_manager.dart';
import '../models/restaurant.dart';

class ItemDetails extends StatefulWidget{
	final Item item;
	final CartManager cartManager;
	final void Function() quantityUpdated;
	
	// 1
	const ItemDetails({
		super.key,
		required this.item,
		required this.cartManager,
		required this.quantityUpdated,
	});
	
	@override
	State<ItemDetails> createState() => _ItemDetailsState();
}

class _ItemDetailsState extends State<ItemDetails>{
	@override
	Widget build(BuildContext context){
	
		// 2
		final textTheme = Theme.of(context)
		.textTheme
		.apply(
			displayColor: Theme.of(context).colorScheme.onSurface
		);
		
		// 3
		final colorTheme = Theme.of(context).colorScheme;
		
		// 4
		final Padding(
			padding: const EdgeInsets.all(16.0),
			
			// 5
			child: Wrap(
				chilren: [
					
					// 6
					Column(
						crossAxisAlignment: CroddAxisAlignment.start,
						children:[
							Text(
								widget:item.name,
								style: textTheme.headlineMedium
							),
							Text(widget.item.description),
						],
					),
				],
			),
		);	
	}
}
```

| Section | Description                                                                                                                                                                                               |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***ItemDetails*** - takes in the selected item and cart manager to manage cart oprerations.<br><br>***quantityUpdated*** - a callback that notifies the parent widget that the user updated the quantity. |
| 2       | ***textTheme*** - ensure the text color matches the surface color of the color scheme.                                                                                                                    |
| 3       | ***colorTheme*** - ensures the app has a consistent color theme across all widget in app.                                                                                                                 |
| 4       | Add uniform padding of ***16.0*** all around.                                                                                                                                                             |
| 5       | ***Wrap*** - organizes children in horizontal or vertical runs, adjusting the layout based on space.                                                                                                      |
| 6       | ***Column*** - aligns child widgets vertically.                                                                                                                                                           |

![[Pasted image 20251024203324.png]]
4. Showing Item Details.
   ***quantityUpdated()*** - callback is invoked, call ***setState()*** to trigger a new render of the widget.
```dart title:'restaurant_page.dart'
builder: (context) => ItemDetails(
	item: item,
	cartManager: widget.cartManager,
	quantityUpdated: (){
		setState((){});
	},
),
```

5. Import relevant .dart file.
   ![[Pasted image 20251024211917.png]]
```dart title:'restaurant_page.dart'
import '../components/item_details.dart';
```

8.  Creating a Most Liked Badge
```dart title:'item_details.dart'
// 1
Widget _mostLikedBadge(ColorScheme colorTheme){
	
	// 2
	return Align(
		
		// 3
		alignment: Alignment.centerLeft,
		
		// 4
		child: Container(
			padding: const EdgeInsets.all(4.0),
			color: colorTheme.onPrimary,
			
			// 5
			child: const Text('#1 Most')
		),
	);
}
```

| Section | Description                                                                                                                        |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***_mostLikedBadge()*** - which in a ***ColorScheme***. This method will create a badge to indicate whether an item is most liked. |
| 2       | ***Align*** - used to align the badge within the parent widget.                                                                    |
| 3       | Align the widget center-left.                                                                                                      |
| 4       | ***Container*** - used to apply padding and color.                                                                                 |
| 5       | ***Text*** - used to display the content of the badge. It reads ***#1 Most Liked***.                                               |
9. Add ***16.0*** padding between the liked badge.
   ![[Pasted image 20251024215318.png]]
```dart title:'item_details.page'
const SizedBox(height: 16.0),
_mostLikedBadge(colorTheme),
const SizedBox(height: 16.0),
```

10. Showing an item image.
```dart title:'item_details.page'
// 1
Widget _itemImage(String imageUrl){
	
	// 2
	return Container(
		height:200,
		decoration: BoxDecoration(
			borderRadius: BorderRadius.circular(8.0),
			
			// 3
			image: DecorationImage(
				image: NetworkImage(imageUrl),
				fit: BoxFit.cover,
			),
		),
	);
}
```

| Section | Description                                                                      |
| ------- | -------------------------------------------------------------------------------- |
| 1       | ***_itemImage()*** - takes in an ***imageUrl***.                                 |
| 2       | Apply a container to style the image, adding a fixed height and rounded corners. |
| 3       | set the background image.                                                        |
11. Add 16.0 padding between ***SizedBox***.
    ![[Pasted image 20251024221359.png]]

```dart title:'item_details.page'
const SizedBox(height: 16.0),
_itemImage(widget.item.imageUrl),
const SizedBox(height: 16.0),
```

12. Creating a Widget to control the cart.
    Create a cart control component to update the quantity.
    ![[Pasted image 20251024221614.png]]
```dart title:'lib/components/cart_control.dart'
import 'package:flutter/material.dart';

class CartControl extends StatefulWidget{
	final void Function(int) addToCart;
	
	const CartControl({
		required this.addToCard,
		super.key,
	});
	
	@override
	State<CartControl> createState() => _CartControlState();
}

class _CartControlState extends State<CartControl>{
	int _cartNumber = 1;
	
	@override
	Widget build(BuildContext context){
		final colorScheme = Theme.of(context).colorScheme;
		return Row(
			mainAxisAlignment: MainAxisAlignment.spaceBetween,
			children:[
				Container(
					color: Colors.red,
					height: 44.0,
				),
			],
		);
	}
}
```

| Section | Description                                                                                                                              |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***CartControl*** - Define a stateful widget.                                                                                            |
| 2       | ***addToCart()*** - which returns an integer to specify the number of items in the cart.                                                 |
| 3       | Link this widget to its state ***_CartControlState()***.                                                                                 |
| 4       | Define the ***CartControl*** state class                                                                                                 |
| 5       | ***_cartNumber*** - private state variable, used to keep track of the quantity of items to be added to the cart. The default value is 1. |
| 6       | ***build()*** - retrieve the color scheme for consistency.                                                                               |
| 7       | Return a ***Row*** widget to layout children horizontally.                                                                               |
| 8       | Use ***MainAxisAlignment.spaceBetwwen*** to space the children evenly.                                                                   |
| 9       | Add a placeholder container which will eventually be replaced by cart control components.                                                |
13. Creating the Minus Button.
    ![[Pasted image 20251024223814.png]]
```dart title:'cart_control.dart'
Widget _buildMinusButton(){
	return IconButton(
		icon: const Icon(Icons.remove),
		onPressed: (){
			setState((){
				if(_cartNumber > 1){
					_cartNumber--;
				}
			});
		},
		
		tooltip: 'Decrease Cart Count',
	);
}
```

| Section | Description                                                                                                      |
| ------- | ---------------------------------------------------------------------------------------------------------------- |
| 1       | Create a button to decrease the number of items in the cart.                                                     |
| 2       | Initialize an ***IconButton*** with the ***remove*** symbol renders like a minus sign.                           |
| 3       | Configure the ***onPressed()*** - trigger a ***setState()*** to update the UI.                                   |
| 4       | Decrements ***_cartNumber*** by 1 if it's greater than 1 preventing it preventing it form it from going below 1. |
| 5       | Provide a tooltip for accessibility and user guidance.                                                           |
14. Creating cart number container. Add the container to display the quantity.
    ![[Pasted image 20251024225156.png]]
```dart title:'cart_control.dart'
// 1
Widget _buildCartNumberContainer(ColorScheme colorScheme){
	
	// 2
	return Container(
		padding: const EdgeInsets.symmetric(
			horizontal:16.0,
			vertical: 8.0,
		),
		
		// 3
		color: colorScheme.onPrimary,
		child:Text(_cartNumber.toString()),
	)

}
```

| Section | Description                                               |
| ------- | --------------------------------------------------------- |
| 1       | The method takes a ***ColorScheme*** to style the widget. |
| 2       | It returns a container with spacing and alignment.        |
| 3       | Displays the cart number as a text.                       |
15. Creating the Plus Button.
    The next step is to add the plus button.!
    [[Pasted image 20251025231533.png]]

```dart title:'cart_control.dart'
Widget _buildPlusButoon(){
	return IconBUtton(
		icon: const Icon(Icons.add),
		
		onPressed:() {
			setState((){
				_cartNumber++;
			});
		},
		tooltip: 'Increase Cart Count',
	);
}
```
16. Creating the Add to Cart button.
    ![[Pasted image 20251025232025.png]]
```Dart title:'cart_control.dart'
Widget _buildAddCartButton(){
	
	// 1
	return FilledButton(
		
		// 2
		onPressed: (){
			widget.addToCart(_cartNumber);
		},
		
		// 3
		child: const Text('Add to Cart'),
	);
}
```

| Section | Description                                                                                                              |
| ------- | ------------------------------------------------------------------------------------------------------------------------ |
| 1       | Intialize a ***FilledButton*** which a button that fills the button's background.                                        |
| 2       | When the user presses the button, trigger the ***addToCart()*** callback and pass the number of items the user selected. |
| 3       | The button displays the text ***Add to Cart***.                                                                          |
17. Showing the Cart Control Components.
```dart title:'cart_control.dart'
_buildMinusButton(),
_buildCartNumberContainer(colorScheme),
_buildPlusButton(),

const Spacer(),
_buildAddCartButton(),
```

18. Using the Cart Control
```dart title:'item_details.dart'
// 1
Widget _addToCartControl(Item item){
	
	// 2
	return CartContol(
	
		// 3
		addToCart: (number){
			const uuid = Uuid();
			final uniqueId = uuid.v4();
			final cartItem = CartItem(
				id: uniqueId,
				name: item.name,
				price: item.price,
				quantity: number,
			);
			
			// 4
			setState((){
				widget.cartManager.addItem(cartItem);
				
				// 5
				widget.quantityUpdated();
			});
			
			// 6
			Navigator.pop(context)
		}
	)
}
```

| Section | Description                                                                                                                                                                                        |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***_addToCartControl()***  -takes in the selected ***Item*** object.                                                                                                                               |
| 2       | It returns a ***CartControl*** widget.                                                                                                                                                             |
| 3       | ***addToCart()*** callback function will return the item quantity and create a new ***CartItem***. A ***Cart Item*** requires a uniquely generated id, item name, price and the quantity selected. |
| 4       | Update the state by adding the new cart item managed by ***CartManager***.                                                                                                                         |
| 5       | Invoke the callback to notify the parent widget that the quantity has been updated.                                                                                                                |
| 6       | Close the bottom sheet.                                                                                                                                                                            |
19.  Import relevant .dart package.
```dart title:'items_details.dart';
import 'package:uuid/uuid.dart';
import 'cart_contol.dart';
```
20. Applying the cart control
```dart title:'item_details.dart'
_addToCartControl(widget.item),
```
21. Hot reload.
    ![[Pasted image 20251025235819.png]]