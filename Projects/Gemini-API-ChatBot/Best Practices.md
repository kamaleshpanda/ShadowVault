**Always use comma , instead of + in print**
#commavsplus 
Correct:
```
print("API KEY ", api_key)
```
Wrong:
```
print("API KEY " + api_key)
```
Reason:
Comma is safer because it automatically handles different data types and avoids errors.

Use *+* for string concatenation only.

```
first = "Kamalesh"  
last = "Panda"  
print(first + " " + last)
```
Output :- Kamalesh Panda

```
name = "Kamalesh"  
age = 20  
print(name + age)           ###ERROR
```
but to correct it use
```
age = 20  
print("Age is " + str(age))
```

