# DatePicker
![[Pasted image 20251027082827.png]]
1. User to select the date to pick up or have the food delivered.
```dart title:'checkout_page.dart'
// 1
String formatDate(DateTime? dateTime){
	
	// 2
	if  (dateTime == null){
		return 'Select Date';
	}
	
	
	// 3
	final formatter = DateFormat('yyyy-MM-dd');
	return formatter.dormat(dateTime);
}
```

| Section | Description                                                                                     |
| ------- | ----------------------------------------------------------------------------------------------- |
| 1       | This function takes an optional ***DateTime*** as a parameter.                                  |
| 2       | If the ***dateTime*** - null, return the text ***Select Date***, to ask the user sekect a date. |
| 3       | If the ***dateTime*** exists, return the formatted date.                                        |
2. Import relevant .dart package.
   Which provides internationalization helpers needed by ***DateFormat***.
```dart title:'checkout_page.dart'
import 'package:intl/intl.dart';
```
3. Select Date Picker
```dart title:'checkout_page.dart'
// 1
void _selectDate(BuildContext context) async{

	// 2
	final picked =await showDatePicker(
		
		// 3
		context: context,
		
		// 4
		initialDate: selectedDate ?? DateTime.now(),
		
		// 5
		firstDate: _firstDate,
		lastDate: _lastDate,
	);
	
	// 6
	if (picked != null && picked != selectedDate){
		setState((){
			selectedDate = picked;
		});
	}
}
```

| Section | Description                                                                                                                                                                     |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***_selectDate()*** - an asynchronous function that takes ***BuildContext*** as a parameter.                                                                                    |
| 2       | ***showDatePicker()*** - opens the date picker dialog. The function waits for the user to pick or cancel the date picker and stores it in the ***picked*** property.            |
| 3       | Pass in the context to display the dialog.                                                                                                                                      |
| 4       | ***initialDate*** - sets the selected date or defaults to the current date.                                                                                                     |
| 5       | Define the date range the user can pick from.                                                                                                                                   |
| 6       | If the picked date is not null and is different from the currently selected date, update the ***selectedDate*** and trigger a rebuild of the widget to reflect the new section. |
# TimePicker
![[Pasted image 20251027085402.png]]
1. Configurate Time of Day.
```dart title:'checkout_page.dart'
// 1
String formatTimeOfDay(TimeOfDay? timeOfDay){
	
	// 2
	if(timeOfDay == null){
		return 'Select Time';
	}
	
	// 3
	final hour = timeOfDay.hour.toString().padLeft(2, '0');
	final minute = timeOfDay.minute.toString().padLeft(2, '0');
	return '$hour:$minute';
}
```

| Section | Description                                                                                        |
| ------- | -------------------------------------------------------------------------------------------------- |
| 1       | This function takes in ***TimeOfDay*** as a parameter.                                             |
| 2       | If the ***timeOfDay*** is null, return ***Select Time*** to indicate to the user to select a time. |
| 3       | Otherwise, return the formatted time.                                                              |
2. Select Time Picker
```dart title:'checkout_page.dart'
// 1
void _selectTime(BuildContext context) async{
	
	// 2
	final picked = awiat showTimePicker(
		
		// 3
		context: context,
		
		// 4
		initialEntruMode: TimePickerEntryMode.input,
		
		// 5
		initialTime: SelectedTime ?? TimeOfDay.now(),
		
		// 6
		builder: (context, child){
			return MediaQuery(
				data: MediaQuery.of(context).copyWith(
					alwaysUse24HourFormat: true,
				),
				child: child!,
			);
		},
	);
	
	if (picked != null && picked != selectedTime){
		setState((){
			selectedTime = picked;
		});
	}
}
```

| Section | Description                                                                                                                                                                       |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | ***_selectTime()*** - an asynchronous function that takes ***BuildContext*** as a parameter.                                                                                      |
| 2       | ***ShowTimePicker()*** - opens the time picker dialog. The function waits for the user to pick or cancel the time picker and stores it in the ***picked*** property.              |
| 3       | Still pass in the context to display the dialog.                                                                                                                                  |
| 4       | ***initialEntryMode*** sets the mode to enter the time. ***input*** mode allows the user to enter values via the keyboard.                                                        |
| 5       | Set the ***initialTime*** to the ***selectedTime***, if null, default to the current time.                                                                                        |
| 6       | The ***builder()*** function builds the time picker. ***MediaQuery*** forces it to always show the 24-hour time format, regardless of the device's default setting.               |
| 7       | If the picked time is not null and is different from the currently selected time, update the ***selectedTime*** and trigger a rebuild of the widget to reflect the new selection. |
3. Showing the Date and Time Picker
```dart title:'Add Date and Time Picker'
// 1
const SizedBox(height: 16.0),

// 2
Row(
	// 3
	children:[
		TextButton(
			child:Text(formatDate(selectedDate)),
			onPressed: () => _selectDate(context),
	
		TextButton(
			child: Text(formatTimeofDay(selectedTime)),
			onPressed: () => _selectTime(context),
		),
	],
),
```

| Section | Description                                                                      |
| ------- | -------------------------------------------------------------------------------- |
| 1       | Add a ***16.0*** vertical space from the widget on top.                          |
| 2       | ***Row*** -  To display the 2 buttons horizontally.                              |
| 3       | The first text button displays ***Select Date*** or the currently selected dat.  |
| 4       | Tapping the button presents the date picker.                                     |
| 5       | The second text button display ***Select Time*** or the currently selected time. |
| 6       | Tapping the button presents the time picker.                                     |
| 7       | Add ***16.0*** vertical spacing between the widget below.                        |
![[Pasted image 20251027093814.png]]
# flutter_datetime_picker_plus