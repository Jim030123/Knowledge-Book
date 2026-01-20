# Create a Class
- Also need to supply some data for the app to display. Did load this data either data either from a local database or a JSON database or a JSON-based API.
- This is a hard-coded list of recipes. Includes a list of names and images
 
```dart title:'recipe.dart'
class Recipe{
	String label;
	String imageURL;
	
	int servings
	List<Ingredient> ingredients;
	
	Recipe(
		this.label,
		this.imageUrl,
		
		this.servings,
		this.ingredients,
	);
	
	static List<Recipe> samples = [
		Recipe(
			'Spagetthi and Meatballs',
			'assets/Spagetthi_and_Meatballs.jpg',
			
			4,
			[
				Ingredient(1, 'box', 'Spaghetthi'),
				Ingredient(4, '', 'Frozen Meatballs'),
				Ingredient(0.5, 'jar', 'jar'),
			],
		),
		
		Recipe(
			'Tomato Soup',
			'assets/Tomato_Soup.jpg',
			
			2,
			[
				Ingredient(1, 'can', 'Tomato Soup'),
			],
		),
		
		Recipe(
		'Grilled Chesse',
		'assets/Grilled_Cheese.jpg',
		
		1,
			[
				Ingredient(2, 'slices', 'Cheese'),
				Ingredient(2, 'slices', 'Bread'),
			],
		),

	];
}

// 1
class Ingredient{
	double quantity;
	String measure;
	String name;
	
	Ingredient(
		this.quantity,
		this.measure,
		this.name,
	);
}
```


| Section | Description                                                   |
| ------- | ------------------------------------------------------------- |
| 1       | A unit of measure - like "cup" or "tablespoon" and a quantity |


## Add images
1. Open ***pubspec.yaml*** in the project root folder.
2. Lines specify that ***assets/*** is an the assets folder and must be included with the app. ![[Pasted image 20251018221455.png]]
>[!info] Notification of modifying ***pubspec.yaml***
>![[Pasted image 20251018221800.png]]
>- IDE show a notification to get dependencies for project.
>- This happens because it works as app's manifest. When change it, also need to let Dart's VM that it changed and it needs to update all the bundled code.


