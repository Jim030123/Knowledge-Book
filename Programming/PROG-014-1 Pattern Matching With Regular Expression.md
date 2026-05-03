- Allow to specify a pattern of text to search for:
>[!note] All text have their own format
>Is 011-2345 6789 but not 1 123, 456, 789

```python
def isPhoneNumber(text):  
	if len(text) != 13:  # 1
		return False  
  
# first 3 digits  
	for i in range(0,3):  
		if not text[i].isdecimal(): # 2
			return False  
	  
	# dash  
	if text[3] != '-': # 3 
		return False  
	  
	# next 4 digits  
	for i in range(4,8):  
		if not text[i].isdecimal(): # 4
			return False  
	  
	# space  
	if text[8] != ' ':  # 5
		return False  
	  
	# last 4 digits  
	for i in range(9,13): 
		if not text[i].isdecimal(): # 6
			return False  
	  
	return True # 7
  
print(isPhoneNumber('011-2345 6789'))  
print(isPhoneNumber('1 123, 456, 789'))
```
```
True
False
```

This ***isPhoneNumber()*** function checks whether string stored in text follows the format of a valid Malaysian phone number XXX-XXXX XXXX.
1. The function first checks whether the length of the string is 13 characters.
2. The loop checks the first 3 characters of the string. The ***isdecimal()*** ensures that each character is a numeric digit.
3. The 4th character must be a hyphen ***(-)***. If the character at position 3 is not ***(-)***.
4. This loop checks the next 4 characters. Each character must be a numeric digit.
5. The 9th must be a space between 2 number groups.
6. This loop checks the last 4 characters of the phone number. All characters must be digits.
7. If the program successfully passes all the checks above, it means the string follows the correct phone number format.
```python
message = 'Call me at 012-2345 6789 tomorrow. 011-2345 6789 is my office.'

for i in range(len(message));
	chunk = message[i:i+13] # 1
	
	if isPhoneNumber(chunk):
		print('Phone number found: ' + chunk)

print('Done')
```

```
Phone number found: 012-2345 6789
Phone number found: 011-2345 6789
Done
```

1. Each iteration of the ***for*** loop, a new chunk of 13 characters from ***message*** is assigned to the variable chunk.
   1st iteration ***i*** is ***0*** and ***chunk*** is assigned ***message[0:13]***
   Next iteration ***i*** is ***1*** and ***chunk*** is assigned ***message[1:13]***
   Pass ***chunk*** to ***isPhoneNumber()*** to see whether it matches phone number pattern and if so, you print the chunk.
   Once done going through ***message***, we print ***Done***.
# Regex
***\d*** in a regex stands for a digit character.
```python
\d\d\d-\d\d\d\d \d\d\d\d
```

Sophisticated, ***3*** in braces ***({3})***
```python
\d{3}-\d{4} \d{4}
```
## Creating Regex Object
```python
import re
```
### re.compile()
```python
phoneNumRegex = re.compile(r'\d{3}-\d{4} \d{4}')
```
## Marching Regex Objects
- Regex object's ***search()*** method searches the string it is passed for any matches to the regex.
- ***search()*** will return None if the regex pattern is not found in the string.
- ***search()*** method returns a Match object, which have a ***group()*** method will return the actual matched text from the searched string.
```python
phoneNumRegex = re.compile(r'\d{3}-\d{4} \d{4}')
mo = phoneNumRegex.search('My number is 012-3456 7890')
print('Phone number found: ' + mo.group())
```

- Knowing that ***mo*** contains a Match object and not the null value None, we can call ***group()*** on ***mo*** to return the match. 
## Grouping with Parentheses
- Can use the ***group()*** match object method to grab the matching text from just 1 group.
```python
(\d\d\d)-(\d\d\d\d \d\d\d\d)
```

- The 1st set of parentheses in regex string will be group 1.
- The 2nd set will be group 2.

```python

```