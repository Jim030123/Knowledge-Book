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