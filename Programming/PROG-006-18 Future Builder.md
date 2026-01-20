- ***MockYummyService*** contains asynchronous function that a ***Future*** object. ***FutureBuilder*** helps determine the state of ***Future***.
```dart title:'explore_page.dart'
// 1
return FutureBuilder(
	
	// 2
	future: mockService.getExploreData(),
	
	// 3
	builder: (context, AsyncSnapshot<ExploreData>snapshot){
		
		// 4
		if (snapshot.connectionState == ConnectionState.done){
			
			// 5
			final restaurants = snapshot.data?.restaurants ?? [];
			final categories = snapshot.data?.categories ?? [];
			final posts = snapshot.data?.friendPosts ?? [];
			
			return const Center(
				child: SizedBox(
					child: Text('Show RestaurantSection'),
				),
			);
		} else{
			// 6
			return const Center(
				child: CircularProgressIndicator(),
			);
		}
	},
)
```

| Section | Desciption                                                                                                                                                                      |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***FutureBuilder*** - that works with asynchronous operations, allowing to build UI based on the latest snapshot of ***Future***.                                               |
| 2       | ***FutureBuilder()*** takes in future.<br><br>***getExploreData()*** - to fetch data which returns an instance of ***ExploreData***.                                            |
| 3       | ***builder()*** - decides what the UI should look like based on the current state of the ***Future***.  This is provided by the ***snapshot***.                                 |
| 4       | ***snapshot.connectionSate*** - The data is available to consume.                                                                                                               |
| 5       | Extract the data from ***snapshot.data***, providing default values if the data is null.<br><br>The widget return a placeholder, you will replace it with actual content later. |
| 6       | If the data is not ready to consume, show a loading spinner.                                                                                                                    |
![[Pasted image 20251022182700.png]]