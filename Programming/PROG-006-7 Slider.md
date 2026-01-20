- To allow the user to adjust the number of servings.
```dart title:'recipe_detail.dart'
int _sliderVal = 1;

Slider(

	// 1
	min: 1,
	max: 10,
	divisions: 9,
	
	// 2
	label: '${_sliderval * widget.recipe.servings} serving',
	
	// 3
	value: _slider.Val.toDouble(),
	
	// 4
	onChanged: (newValue){
		set((){
			_sliderVal = newValue.round();
		});
	},
	
	// 5
	activeColor: Colors.green,
	inactiveColor: Colors.black,
),
```

| Section | Description                                                                                                                                                                                          |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***min***, ***max*** and ***divisions*** to define how the slider moves.<br><br>It moves between the values of 1 and 10, with 10 discreet stop. It can only have values of 1, 2, 3, 4, 5, 7, 8, 9 or |
| 2       | ***label*** updates as tge ***_sliderVal*** changes and displays a scaled number of servings.                                                                                                        |
| 3       | Slider works in ***double*** values, this converts the ***int*** variable.                                                                                                                           |
| 4       | Slider changes, this uses ***round()*** to convert the ***double*** value to an ***int***, then saves it in ***_sliderval***                                                                         |
| 5       | ***activeColor*** - between the minimum value and the thumb.<br>***inactiveColor*** - represent the rest.                                                                                            |
![[Pasted image 20251019153904.png]]
