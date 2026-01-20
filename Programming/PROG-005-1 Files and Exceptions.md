# What is the File
- Files provide long-term retention of typically large amounts of data, even after the program that created the data terminated, so data maintained in files in persistent.
- Use JSON to serialize and deserialize objects to facilitate saving  those objects to secondary storage and transmitting which we'll use both the Python Standard Library's csv module and pandas to load and manipulate CSV data.
- Use with statement, programs typically request and release resource^[files] during program execution. Often, these are in limited supply or can be used only by 1 program at a time.

# What is Exception Handling
- Indicates an execution-time problem. You've seen exeptions of types ZeroDivisionError, NameError, ValueError, StatisticsError, TypeError, IndexError, KeyError and RuntimeError.
- Show how to deal with exceptions as they occur by using try statements and associated except classes to handle exceptions. 
# Modes for reading and writing
- Writing and appending modes create the file if it does not exist.
- The reading modes raise a FileNotFoundError if the file does not exist.

| Mode | Description                                                                                                               |
| ---- | ------------------------------------------------------------------------------------------------------------------------- |
| r    | Open a text file for reading. This is the default if the default if do not specify the file-open mode when you call open. |
| r+   |                                                                                                                           |
| rb   |                                                                                                                           |
| w    |                                                                                                                           |
| w+   |                                                                                                                           |
| wb+  |                                                                                                                           |
| a    |                                                                                                                           |
| a+   |                                                                                                                           |

## 1. User enter the input and record as .txt file
```python
with open('file_name.txt',',a+') as file:

	while True:
		attribute = input("Please enter something here:")
		
		if name == "0":
			break
		
		else:
			file.write(name + "\n")
	
	file.close()		
```

## 2. User read the file
```python
with open("file_name.txt", "r") as file

	file=file.readlines()
	
	print("All attributes in file")
	
	for attribute in file:
	print(name.strip())
```


## 3. Read CSV as 2 dimension data
```python
import csv

processedData = list()
total BMI = 0
averageBMI = 0

try:
	with open('file', 'r') as file:
	
	fileReader = csv.reader(file)
	
	fileData = list(fileReader)
	
	del fileData[0]
	
	try:
		for data in fileData:
			data[2] = float(data[2])
			totalBMI += data[2]
			processed.append(data)
			
	except ValueError:
		print(f"Row{data.index(data)+1} is skipped die tp omvalid data")
```

