
# Segment Button
![[Pasted image 20251027082408.png]]
1. This function updates the user's order type.
```dart title:'checkout_page.dart'
Widget _buildOrderSegmentType(){
	
	// 1
	return SegmentedButton(
		
		// 2
		showedSelectedIcon:false,
		
		// 3
		segment: const[
			ButtonSegment(
				value: 0,
				label: Text('Delivery'),
				icon: Icon(Icons.pedal_bike),
			),
			ButtonSegment(
				value: 1,
				label: Text('Pickup'),
				icon: Icon(Icons.local_mall),
			),
		],
		
		// 4
		selected: selectedSegment,
		
		// 5
		onSelectionChanged: onSegmentSelected,
	);
}
```

| Section | Description                                                                      |
| ------- | -------------------------------------------------------------------------------- |
| 1       | Returns a **SegmentedButton** widget.                                            |
| 2       | Hide the icons in the segmented button.                                          |
| 3       | Define 2 button segments for the user to choose. ***Delivery*** or ***Pickup***. |
| 4       | Set the selected segment.                                                        |
| 5       | When a user makes a choice update the selected segment.                          |

2. Add segment control.
```dart title:'checkout_page.dart'
const SizedBox(height: 16.0),
_buildOrderSegmentedType(),
```

3. Creating Order Summary.
![[Pasted image 20251027093918.png]]
```dart title:'chcekout_page.dart'
Widget _buildOrderSummary(BuildContext context){
	final colorTheme.of(context).colorScheme;
	
	return Expanded(
	
		child:ListView.builder
		
	)
}
```