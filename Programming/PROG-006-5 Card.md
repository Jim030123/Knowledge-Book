- Define an area an area of the UI where have laid out related information about a specific entity. 
>[!note] Example
>Music app might have labels for an labels for an album's title, artist and release date along with an image for the album cover and maybe a control for rating it with stars.

![[Pasted image 20251018223407.png]]
# Card Widget
```dart
Widget buildRecipeCard (Recipe recipe){

	// 1
	return Card(
	
		// 2
		child: Column(
			
			// 3
			childeren: <Widget>[
			
				// 4
				Image(image: AssetImage(recipe.imageUrl)),
				
				// 5
				Text(recipe.label),
			],
		),
	);
}
```

| Section | Description                                                                                                    |
| ------- | -------------------------------------------------------------------------------------------------------------- |
| 1       | Return a ***Card*** from ***buildRecipeCard()***.                                                              |
| 2       | ***Card***'s child property is a ***Column***. A ***Column*** is a widget that defines a vertical layout.      |
| 3       | ***Column*** has 2 childeren.                                                                                  |
| 4       | ***Image(image: AssetImage())*** - the Image fetched from the local asst bundle defined in ***pubspec.yaml***. |
| 5       | ***Text*** - It will contain the ***recipe.label*** value.                                                     |
```dart
return buildRecipeCard(Recipe.samples[index]);
```
# RoundedRectangleBorder
```dart
Card (

	// 1
	elevation: 2.0,
	
	// 2
	shape: RoundedRectangleBorder(
		borderRadius: BorderRadius.circular(10.0)),
	
	// 2	
	child: Padding(
		padding: const EdgeInsets.all(16.0),
		
		// 4
		child: Column(
			children: <Widget>[
				Image(image: AssetImage(recipe.imageURL)),
				
				// 5
				const SizedBox(
				height: 14.0,
				),
				
				// 6
				Text(
					recipe.label,
					style: const TextStyle(
						fontSize: 20.0,
						fontWeight: FontWeight.w700,
						fontFamily: 'Palatino',	
					),
				),
			],
		),
	);
)
```


| Section | Description                                                                                                                                     |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***elevation*** - how high off the screen the card is, affecting its shadow.                                                                    |
| 2       | ***shape*** - handles the shape of the card. This code defines a rounded rectangle with a ***10.0*** corner radius.                             |
| 3       | ***Padding*** - insets its child's contents by the specific ***padding*** value.                                                                |
| 4       | padding child is still same vertical ***Column*** with the image and text                                                                       |
| 5       | ***SizedBox*** - blank view with a fixed size.                                                                                                  |
| 6       | Customize ***Text*** widgets with a ***style*** object. Specified a ***Palatino*** font with a size ***20.0*** and a bold weight of ***w700***. |

| Before Modify                        | After Modify                         |
| ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20251018224544.png]] | ![[Pasted image 20251018232122.png]] |
