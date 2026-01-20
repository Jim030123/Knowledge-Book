![[Pasted image 20251025235905.png]]
User will be able to do the following:
- Select whether the order is delivered or picked up.
- Name of the recipient.
- Select date and time.
- Manage the cart items.
- Submit their order.

# Adding a Drawer
1. Define Drawer Max Width
```dart title:'restaurant_page.dart'
static const double drawerWidth=375.0;
```
2. Define a constant variable to determine the max width of the drawer.
   ***_buildEndDrawer()*** function creates a simple drawer with a specific width and a placeholder red container.
```dart title:'restaurant_page.dart'
Widget _buildEndDrawer(){
	return SizedBox(
		width:drawerWidth,
		child: Container(color:Colors.red),
	);
}
```
3. Apply Drawer. 
   The scaffold widget is a top-level widget used in Flutter to implement the basic visual layout structure of an app. It includes the ***endDrawer*** property to do define a drawer that slides in from the right.
```dart title:'restaurant_page.dart'
endDrawer: _buildEndDrawer(),
```
4. Adding a Floating Action Button.
   Use a floating action button when clicked on present the drawer.
   ![[Pasted image 20251026001403.png]]
```dart title:'restaurant.dart'
final GlobalKey<ScaffoldState> scaffoldKey = GlobalKey<ScaffoldState>();
```
- Having a ***GlobalKey*** for ***Scaffold*** allows to control the scaffold from anywhere in code.
- This particularly useful for opening drawers, snack bars or any other action that requires a reference to the ***ScaffoldState***.
5. Add Scaffold Key.
```dart title:'restaurant.dart'
key: scaffoldKey,
```

6. Find and replace.
- It will try to access the scaffold's current state and open the drawer. The ***!*** operator asserts that the current state is not null.
```dart title:'restaurant.dart'
void openDrawer(){
	scaffoldKey.currentState!.openEndDrawer();
}
```
7. Add a Floating Action Button
```dart title:'restaurant.dart'
// 1
Widget _buildFloatingActionButton(){
	
	// 2
	return FloatingActionButton.extended(
		
		// 3
		onPressed: openDrawer,
		
		// 4
		tooltip:'Cart',
		
		// 5
		icon: const Icon(Icons.shopping_cart),
		
		// 6
		label: Text('${widget.cartManager.items.length} Items in cart')
	)
}
```

| Section | Description                                                                                               |
| ------- | --------------------------------------------------------------------------------------------------------- |
| 1       | The function returns a ***FloatingActionButton*** widget.                                                 |
| 2       | Instantiate a ***FloatingActionButton.extend*** which allows the button to have both an icon and a label. |
| 3       | When the button is pressed, ***OpenDrawer()*** is invoked.                                                |
| 4       | Show a tooltip for accessibility.                                                                         |
| 5       | Set the button's icon.                                                                                    |
| 6       | The label displays the number of items in the cart.                                                       |
8. Apply Floating Action Button.
```dart title:'restaurant.dart'
floatingActionButton: _buildFloatingActionButton(),
```

9.  Perform a hot reload.
![[Pasted image 20251026204131.png]]
# Creating the Checkout Page
1. Checkout Page structure
```dart title:'lib/screens/checkout_page.dart'
// 1
import 'package:flutter/material.dart';
import '../models/cart_manager.dart';
import '../models/order_manager.dart';

class CheckoutPage extends StatefulWidget{
	
	// 2
	final CartManager cartManager;
	
	// 3
	final Function() didUpdate;
	
	// 4
	final Function(Order) onSubmit;
	
	const CheckoutPage({
		super.key,
		required this.cartManager,
		required this.didUpdate,
		required this.onSubmit,
	});
	
	@override
	State<CheckoutPage> createState() => _CheckoutPageState();
}

class _CheckoutPageState extends State<CheckoutPage>{

	@override
	Widget build(BuildContext context){
		
		// 5
		final textTheme = Theme.of(context)
		.textTheme
		.apply(
			displayColor: Theme.of(context).colorScheme.onSurface
		);
		
		// 6
		return Scaffold(
			
			// 7
			appBar: AppBar(
				leading: IconButton(
					icon const Icon(Icons.arrow_back),
					onPressed:() => Navigator.of(context).pop(),
				),
			),
			
			// 8
			body: Padding(
				padding: const EdgeInsets.all(16.0),
				child: Column(
					crossAxisAlignment: CrossAxisAlignment.stretch,
					children:[
						Text(
							'Order Details',
							style:textTheme.headlineSmall,
						),
					],
				),
			),
		);
	}
}
```


| Section | Description                                                                                               |
| ------- | --------------------------------------------------------------------------------------------------------- |
| 1       | Import necessary ***material*** library and manager models.                                               |
| 2       | ***CheckoutPage*** - a stateful widget that requires ***CartManager*** - to manage and update cart items. |
| 3       | Declare ***didUpdate()*** callback to notify that the user tapped on the submit button                    |
| 4       | Create an ***onSubmit()*** callback to notify the user tapped on the submit button.                       |
| 5       | Retrieve the current text theme and apply the color theme to be consistent throughout the app.            |
| 6       | Create a ***Scaffold*** widget that sets the app bar and body.                                            |
| 7       | ***appBar*** - displays a back button dismisses the drawer when clicked.                                  |
| 8       | The body sets up padding and uses a ***Column*** widget to layout child widgets vertically.               |
2.  Using the Checkout Page.
```dart title:'restaurant_page.dart'
// 1
 child: Drawer(
	
	// 2
	 child: CheckoutPage(
		 
		 // 3
		 cartManager: widget.cartManager,
		 
		 // 4
		 didUpdate:(){
			 setState((){});
		 },
		 
		 // 5
		 onSubmit: (order){
			 widget.ordersManager.addOrder(order);
			 Navigator.popUntil(context, (route) => route.isFirst);
		 },	 
	 ),
 ),
```

| Section | Description                                                                                           |
| ------- | ----------------------------------------------------------------------------------------------------- |
| 1       | Initialize the ***Drawer*** - that slides the side of the screen.                                     |
| 2       | Use ***CheckoutPage*** as the primary content of the drawer.                                          |
| 3       | Pass in ***cartManager*** to manage and display cart items.                                           |
| 4       | Configure the ***didUpdate()*** callback to refresh the state of the parent widget.                   |
| 5       | Set ***onSubmit()*** -when the user taps on the submit button, add a new order and closes the drawer. |
3. Import relevant .dart file.
```dart title:'restaurant_page.dart'
import 'checkout_page.dart';
```
![[Pasted image 20251026212222.png]]4. Adding Checkout State Properties
```dart title:'checkout_page.dart'
final Map<int, Widget>myTabs = const <int, Widget>{
	0: Text('Delivery'),
	1: Text('Self Pick-Up'),
};

Set<int> selectedSegment = {0};

TimeofDay? selectedTime;

DateTime? selectedDate;

final DateTime _firstDate = DateTime(DateTime.now().year - 2);
final DateTime _lastDate = DateTime(DateTime.now().year + 1);

final TextEditingController _nameController = TextEditingController();
```

| Section | Description                                                                              |
| ------- | ---------------------------------------------------------------------------------------- |
| 1       | Declare a mapping from integer to delivery type.                                         |
| 2       | Determines whether the user selected Delivery or Self-Pick-Up.                           |
| 3       | ***selectedTime*** stores the selected time.                                             |
| 4       | ***selectedDate*** stores the selected date.                                             |
| 5       | ***_firstDate*** and ***_lastDate*** determines the date range the user can select from. |
| 6       | ***_nameController*** refer to the text field used to enter the customer's name.         |
5. Adding a Segmented Control.
   This is a way for users to toggle between food delivery or pick-up.

```dart title:'checkout_page.dart'
void onSegmentSelected(Set<int> segmentIndex){
	setState((){
		selectedSegment = segmentIndex;
	});
}
```
6. Creating Order Summary
```dart title:'checkout_page.dart'

// 1
Widget _buildOrderSummary(BuildContext context){
	
	// 2
	final colorTheme = Theme.of(context).colorScheme;
	
	// 3
	return Expanded(
		
		// 4
		child: ListView.builder(
			
			// 4
			itemCount: widget.cartManager.items.length,
			itemBuilder:(context, index){
				
				// 5
				final item = widget.cartManage.itemAt(index);
				
				// 7
				return ListTile(
					leading: Container(
						padding: const EdgeInsets.all(8.0).
						decoration: Boxdecoration(
							borderRaius: const BordedrRaius.all(
								Radius.circular(8.0)
							),
							border: Border.all(
								color: colorTheme.primary,
								width: 2.0,
							),
						),
						
						child: ClopRRect(
							borderRadius: const BorderRadius.all(
								Radius.circular(8.0)
							),
							child: Text('x$(item.quantity)'),
						)
					),
					title: Text(item.name),
					subtitle: Text('Price: \$${item.price}'),
				);
			},
		),
	);
}
```


| Section | Description                                                                                                             |
| ------- | ----------------------------------------------------------------------------------------------------------------------- |
| 1       | ***_buildOrderSummary()*** - Takes a ***BuildContext*** as a parameter.                                                 |
| 2       | Retrieve the color theme for consistency throughout app.                                                                |
| 3       | Return an Expanded widget that allows ***ListView*** to use all available space in its parent widget.                   |
| 4       | Use ***ListView.builder()*** - To create a scrollable list of items.                                                    |
| 5       | Set item count.                                                                                                         |
| 6       | Build each item by retrieving the menu item for a given index.                                                          |
| 7       | Construct a ***ListTile*** - to display the menu item selected, display the quantity and the total price for each item. |

8. Add order summary and a title.
```dart title:'chcekout_page.dart'
const Text('Order Summary'),
_buildOrderSummary(context),
```

9. Hot Reload.
   ![[Pasted image 20251027101358.png]]
# Deleting Item from an Order
1. The user will swipe left wo remove a menu item.
   ![[Pasted image 20251027101456.png]]
2. Right click ***ListTile*** widget on the line below and select ***Show Context Actions***.
   ![[Pasted image 20251027101609.png]]
3.  Wrap with widget.   
   ![[Pasted image 20251027101710.png]]
4. Rename widget to ***Dismissible*** and the following properties to the widget just above the child.
```dart title:'checkout_page.dart'
// 1
key: Key(item.id),

// 2
direction: Container(),

// 3
background: Container(),

// 4
secondaryBackground: const SizedBox(
	child: Row(
		mainAxisAlignment: MainAxisAlignment.end,
		children:[
			Icon(Icons.delete),
		],
	),
),

// 5
onDismissed: (direction){
	setState((){
		widget.cartManaer.removeItem(item.id);
	});
	
	// 6
	widget.didUpdate();
},
```

| Section | Description                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| 1       | Key - used to uniquely identify each dismissible item in the list.                             |
| 2       | Configurate the dismiss ***direction*** swiping from right to left.                            |
| 3       | Set an empty background container.                                                             |
| 4       | Set a secondary background and show a delete (trash) icon aligned to the right end.            |
| 5       | When ***onDismissed()*** is triggered, call ***setState()*** to remove the item from the cart. |
| 6       | Invoke ***didUpdate()*** to notify the parent to refresh the UI to perform other actions.      |
5. Need a submit button to process the order.
```dart title:'checkout_page.dart'
Widget _buildSumbitButton(){
	
	// 1
	return ElevatedButton(
		
		// 2
		onPressed: widget.cartManager.isEmpty ? null
		
		// 3
		:(){
			final selectedSegment = this.selectedSegment;
			final selectedTime = this.selectedTime;
			final selectedDate = this.selectedDate;
			final name = _nameContorller.text;
			final items = widget.cartManager.items;
			
			
			// 4
			final order = Order(
				selectedSegment: selected Segment,
				selectedTime: selectedTime,
				selectedDate: selectedDate,
				name: name,
				items:items,	
			);
			
			// 5
			widget.cartManager.resetCart();
			
			// 6
			widget.onSubmit(order);
		},
		child: Padding(
			padding: const EdgeInsets.all(16.0),
			child: Text(
				'''Submit Order - \$$ {widget.cartManager,totalCost.toStringAsFixed(2)}'''
			),
		),
	);
}
```

| Section | Description                                                                                                                        |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| 1       | The function returns an ***ElevatedButton*** widget..                                                                              |
| 2       | When the cart is empty, ***onPressed()*** disables the button by setting it to ***null***.                                         |
| 3       | If the cart is not empty, ***onPressed()*** retrieves all the user data such as selected order type, date, name and list of items. |
| 4       | Create an order object.                                                                                                            |
| 5       | Reset the cart.                                                                                                                    |
| 6       | Submit the order.                                                                                                                  |
| 7       | Show the total cost of the order.                                                                                                  |
6. Add Submit Order Button
```dart title:'checkout_page.dart'
_buildSubmitButton(),
```
7. Hot Reload.
   ![[Pasted image 20251027140815.png]]
# Building the Order Page
1. Building Order Page Structure.
![[Pasted image 20251027140928.png]]
```dart title:'lib/screens/myorders_page.dart'
import 'package:flutter/material.dart';
import '../models/order_manager.dary'

class MyOrdersPage extends StatelessWidget{
	final OrderManager orderManager;
	
	// 1
	const MyOrdersPasge({
		super.key,
		required this.orderManager,
	});
	
	@override
	Widget build(BuildContext context){
		final textTheme = Theme.of(context)
		.textTheme
		.apply(
			displayColor: Theme.of(context).colorScheme.onSurface
		);
		
		// 2
		return Scaffold(
			appBar: AppBar(
				centerTitle: false,
				title: Text(
					'My Orders',
					style: textTheme.headlineMedium
				),
			),
			
			// 3
			body: ListView.builder(
				
				// 4
				itemCount: orderManager.totalOrders,
				itemBuilder: (context, index){
					
					// 5
					return OrderTile(order: orderManager.orders[index]);
				},
			),
		);
	}
}

// 6
class OrderTile extends StatelessWidget{
	final Order order;
	
	const OrderTile({
		super.key, required this.order
	});
	
	@override
	Widget build(BuildContext context){
		final textTheme = Theme.of(context)
			.text Theme
			.apply(
				displayColor: Theme.of(context).colorScheme.onSurface
			);
			
		// 7
		return ListTile(
			leading: ClipRRect(
				borderRadius: BorderRadius.circular(8.0),
				
				// 8
				child: Image.asset(
					'assets/food/burger.webp',
					width: 50.0,
					height: 50.0,
					fit: BoxFit.cover,
				),
			),
			
			// 9
			title: Column(
				crossAxisAlignment: CrossAxisAlignment.start,
				children:[
					Text(
						'Scheduled',
						style: textTheme.bodyLarge,
					),
					Text(order.getFormattedOrderInfo()),
					Text('Items: ${order.items.length}'),
				],
			),
		);
	}

}
```

| Section | Description                                                                                |
| ------- | ------------------------------------------------------------------------------------------ |
| 1       | It takes an ***orderManager*** as a parameter. This used to retrieve the list of orders.   |
| 2       | It defines a ***Scaffold*** that has an ***AppBar***.                                      |
| 3       | Displays a ***ListView*** in the body.                                                     |
| 4       | Sets the list view count.                                                                  |
| 5       | For each order, it creates an ***OrderTile*** widget and passes the current order's index. |
| 6       | It defines an ***OrderTile*** widget to display the order.                                 |
| 7       | A tilewraps a ***ListTile*.**                                                              |
| 8       | The ***ListTile*** leading widget is an image with rounded corners.                        |
| 9       | The title displays a ***Column*** to align the order details vertically.                   |

2. Showing the Orders Page.
```dart title:'home.dart'
MyOrderPage(orderManager: widget.orders.Manager),
```
3. Import relevant .dart file.
```dart title:'home.dart'
import 'screens/myorders_page.dart'
```
![[Pasted image 20251027144318.png]]