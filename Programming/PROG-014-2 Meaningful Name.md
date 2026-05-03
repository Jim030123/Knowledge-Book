We name:
- variable
- functions 
- arguments
- classes
- packages
- files
- directories
# Use Intention-Revealing Names
- Choosing good names takes time but saves more than it takes.
>[!warning] If a name requires a comment, then the name does not reveal its intent
>

```java
int d; // elapsed time in days
```
- d reveals nothing. It does not evoke a sense of elapsed time, nor of days.
```java
int elapsedTimeInDays;
int daysSinceCreation;
int daysSinceModification;
int fileAgeInDays;
```


## Example: MineSweeper
```java
public List<int[]> getThem{}{
	List<int[]> list1 = new ArrayList<int[]>();
		for (int[] c: theList)
			if (x[0] == 4)
				list1.add(x);
		return list1; 
}
```

**Hard to tell what this code is doing**
- The problem isn't the simplicity of the code but the *implicitly* of the code. The degree which the context is not explicit in the code itself.
1. What kinds of things are in ***theList***?
2. What is the significance the zeroth subscript of an item in ***theList***?
3. What is the significance of the value 4?
4. How would I use the list being returned?
```java
public List<int[]> getFlaggedCells{}{
	List<int[]> flaggedCells = new ArrayList<int[]>();
		for (int[] cell: gameboard)
			if (cell(STATUS_VALUE) == FLAGGED)
				flaggedCells.add(cell);
		return flaggedCells; 
}
```

- Board is a list of cells called ***theList*** -> ***gameBoard***.
- Find that the 0th subscript is the location of a status values.
- Status value of 4 means "flagged"
```java
public List<Cell> getFlaggedCells{}{
	List<Cell> flaggedCells = new ArrayList<Cell>();
		for (Cell cell: gameboard)
			if (cell.isFlagged)
				flaggedCells.add(cell);
		return flaggedCells; 
}
```

- Write a simple class for cells instead of using an array of int.
- Can include an intention-revealing function (isFlagged) to hide the magic number.
# Avoid Disinformation
- Num = number
  Poor variable, which number of that thing?
- ***accountList***
  The word list means something specific to programmers. If the container holding the accounts is not actually a ***List***, it may lead to false conclusion.
  ***accountGroup***, ***bunchOfAccounts*** would be better.
- ***XYZControllerForEfficientHandlingOfStrings*** vs ***XYZControllerForEfficientStorageOfStrings***
  More distant. The words have frightfully similar shapes.
- Spelling
  It is helpful if names for very similar things sort together alphabetically and if the differences are very obvious, because the developer is likely to pick an object by name without seeing your copious comments or even the list of methods.
  
 **lower-case L or Uppercase O as variable names**
```java
int a = 1;
if (O == L)
	a = O1
else
	l = O1
```
- Using a different font so that the differences were more obvious.
# Make Meaningful Distinction
- Cant use the same name to refer to 2 different things in the same scope, might be tempted to change 1 name in an arbitrary way.
**Number-series naming**
$$(a_{1},a_{2},\dots,a_{N})$$
- They are not disinformative. They provide no clue to the author's intention.
```java
public static void copyChars(char a1[], char a2[]){
	for (int i = 0; i <a1.length; i++){
		a2[i] = a1[i];
	}
}
```

This function reads much more better when ***source*** and ***destination*** are used for the argument names.

>[!example] Have a ***Product*** class.
> - ***ProductInfo*** or ***ProductData*** made the names different without making them mean anything different.
> - ***Info*** and ***Data*** are indistinct noise words like ***a***, ***an*** and ***the***.

>[!note] Nothing wrong with using prefix convetion
> - Decide to call a variable ***theZork*** because you already another variable named ***zork***.

- ***Table*** should never appear in a table name.
- ***Name*** should bever be a floating point number.
```java
getActiveAccount();
getActiveAccounts();
getActiveAccountInfo();
```

- ***moneyAmount*** is indistinguishable form ***money***.
- ***customerInfo*** is indistinguishable from ***customer***.
- ***accountData*** is indistinguishable from ***account***.
- ***theMessage*** is indistinguishable from ***message***.
## Use Pronounceable Names

```java
class DtaRrd102{
	private Date genymdhms;
	private Date modymdhms;
	private final String pszqint = "102";
}
```

to

```java
class Customer{
	private Date generationTimestamp;
	private Date modificationTimestamp;
	private final String pszqint = "102";
}
```

## Use Searchable Names
- May turn up the digit as pat of file names, other constant definition and in various expressions where the values is used with different intent.
- ***e*** is a poor choice for any variable for a programmer might need to search. It is the most common letter in the English language and likely to show up in every passage of text in every program.
- The length of a name should correspond to the size of its scope.
- Variable or constant might be seen or used in multiple places in a body of code, it is imperative to give it a search-friendly name.
```java
for (int j = 0;j < 34; j++){
	s += (t[j] * 4) / 5;
}
```

to 

```java
int realDaysPerIdealDay = 4;
const int WORK_DAYS_PER_WEEK = 5;

int sum = 0;

for (int j = 0; j < NUMBER_OF_TASKS; j++){

	int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
	int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
	sum += realTaskWeeks
}
```