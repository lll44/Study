





# Lists



```python
bicycles = ['trek', 'cannondale', 'redline', 'specialized']

print(bicycles) # ['trek', 'cannondale', 'redline', 'specialized']
print(bicycles[0]) # trek 
print(bicycles[0].title()) # Trek

# Access Items in Reverse
print(bicycles[-1]) # specialized

# Using Values
message = f"My first bicycle was a {bicycles[0].title()}."
print(message) # My first bicycle was a Trek.
 ```



###  Changing, Adding, Removing Elements

```python
motorcycles = ['suzuki', 'samsung']

# Append 
motorcycles.append('ducati')

# Insert
motorcycles.insert(0, 'yamaha')

# Remove
del motorcycles[2] 

# Pop - Removes last element
popped_motorcycle = motorcycles.pop()
popped_motorcycle = motorcycles.pop(1) # Pop at position 

# Remove by Value
motorcycles.remove('ducati') 
		# Only removes first occurence if multiple
  	# Loop to remove all occurences

```

When would you use pop instead of delete? When you need to use the removed value. 

### Sorting Lists

Typically data is added in unpredictable order. 

```python
cars = ['bmw', 'audi', 'toyota', 'subaru']

# Sort Permanently: list.sort()
cars.sort()
print(cars) # ['audi', 'bmw', 'subaru', 'toyota']

cars.sort(reverse=True)
print(cars) # ['toyota', 'subaru', 'bmw', 'audi']

# Reverse Order (Not alphabetic)
cars.reverse()

# Sort Temporarily: sorted()
print(sorted(cars))

# Length of list
len(cars)
```

Sorting lists can be complicated if values are not all lower or upper case, hence will require more advanced techniques later on. 

### Loop through Lists

```python
magicians = ['alice', 'david', 'carolina'] 
for name in magicians: # name can be anything, don't forget colon
	print(magician)
```

### Making Numerical Lists

```python
# range()
for value in range(1, 5):
	print(value) # prints 1-4
  
# Create List with Range
numbers = list(range(1, 6)) 
	print(numbers) # [1, 2, 3, 4, 5]

# Create List & Skip Numbers
even_numbers = list(range(2, 11, 2)) 
	print(even_numbers) #	[2, 4, 6, 8, 10]
  
# List by Square Numbers
squares = []
for value in range(1, 11): 
	squares.append(value**2)  
print(squares) # [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

### List Stats

``` python
digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]

min(digits) # 0
max(digits) # 9
sum(digits) # 45
```

### List Comprehensions

List comprehensions allows you to shorten code for lists in one line. You’ll see them a lot in other people’s code. To use the syntax: Name the list, define the expression, and then range in brackets

```python
squares = [value**2 for value in range(1, 11)] 
print(squares)
```

### Working with Part of a List

```python
players = ['charles', 'martina', 'michael', 'florence', 'eli'] 
print(players[1:4]) # ['martina', 'michael', 'florence']
print(players[:4]) # Starts at beginning to index
print(players[2:]) # Starts on Index 2
print(players[-3:]) # Start from last 3 items
print(players[::2]) # Skip every 2 items

for player in players[:3]: # Loop Through Slice
    print(player.title()) # Charles, Martina, Michael. 
```

### Copying to a separate List

```py
my_foods = ['pizza', 'falafel', 'carrot cake'] 
friend_foods = my_foods[:]

# Doesn't copy to seperate list, links instead
friend_foods = my_foods
```



### Tuples

Tuples are a list of immutable values, hence a list that cannot change. 

Lists are good for collections of items that change throughout it’s life. 

Lists use parentheses instead of square brackets. 

```py
dimensions = (200, 50)
dimensions[0] = 250 # Causes Error, It's immutable

my_t = (3,) # Single tuples require a comma. Not common unless tuples are generated automatically.

for dimension in dimensions:
	print(dimension) # 200, 50
```

## Python Style Conventions

The Python style guide was written with the understanding that code is read more often than it is written, because you start reading it as soon as you begin debugging. 

- Identation: Use four spaces per indentation. No tabs

- Line Length: Less than 80 characters,

- Blank Lines: Group parts of your program with a single blank line, double if they are important modules. 

    ## Control Flow

    ### If-elif-else

    if-elif-else is useful you need to only test one specific condition to test.

    ```pyt
    if x == 1 and y = 2:
    	print()
    elif x == 4 or y == 3:
    	print()
    	
    if age < 4:
    	price = 0 
    elif age < 18:
    	price = 25 
    elif age < 65:
    	price = 40
    elif age >= 65:
    	price = 20:	
    
    ```

    If you want only one block of code to run use if-elif-else, if more than  one block use a series of independent if statements. 

    If you have a specific final condition you are testing for, consider using a final elif block and omit the else block. As a result, you’ll gain extra confidence that your code will run only under the correct conditions.

    

    ### Check if in a list

    ```py
    requested_toppings = ['mushrooms', 'onions', 'pineapple'] 
    'mushrooms' in requested_toppings # True
    
    if 'brocolli' not in request_toppings:
    	print(f"{user.title()}, you can post a response if you wish.")
    ```

    

### Using if Statements with Lists

You can combine lists and if statements to watch for special values that need to be treated differently than other values in the list. You can manage changing conditions efficiently, such as availability of certain items in a restaurant through a shift. You can also prove your code works as expected in all situations. 

For example if we have a list of requested toppings we can print that they are being added, then have a special condition for unavailable toppings

```py
requested_toppings = ['mushrooms', 'green peppers', 'extra cheese']

for requested_topping in requested_toppings:
	if requested_topping == 'green peppers':
		print("Sorry, we are out of green peppers right now.") 
	else:
		print(f"Adding {requested_topping}.")

print("\nFinished making your pizza!")
```

Alternatively we can check if the list isn’t empty. 

```py
requested_toppings = [] 

if requested_toppings:
	for requested_topping in requested_toppings:
		print(f"Adding {requested_topping}.")
	print("\nFinished making your pizza!")

else:
	print("Are you sure you want a plain pizza?")
```

We can combine both approaches to track requested and available toppings

```py
available_toppings = ['mushrooms', 'olives', 'green peppers', 'pepperoni', 'pineapple', 'extra cheese']

requested_toppings = ['mushrooms', 'french fries', 'extra cheese']

for requested_topping in requested_toppings:
	if requested_topping in available_toppings:
		print(f"Adding {requested_topping}.") y 
	else:
		print(f"Sorry, we don't have {requested_topping}.")

print("\nFinished making your pizza!")
```

# Dictionaries

Understanding dictionaries allows you to model a variety of real­world objects more accurately. You’ll be able to create a dictionary representing a person and then store as much information as you want about that person. You can store their name, age, location, profession, and any other aspect of a person you can describe. You’ll be able to store any two kinds of information that can be matched up, such as a list of words and their meanings, a list of people’s names and their favorite numbers, a list of mountains and their elevations, and so forth.

Dictionaries are tricky to implement, but have huge use cases once implemented correctly.

Dictionaries is a collection of _key-value pairs_. Each key is conneted to a value. We use braces {} to define these keyvalue pairs. To access values we use square brackets []. 

### Simple Dictionary

```py
alien_0 = {'color': 'green', 'points': 5}

print(alien_0['color']) # green

new_points = alien_0['points'] 
	print(f"You just earned {new_points} points!")

alien_0 = {} # Starting Empty
alien_0['color'] = 'green' 
alien_0['points'] = 5
print(alien_0) # {'color': 'green', 'points': 5}

alien_0['color'] = 'yellow' # Modifying Values
print(f"The alien is now {alien_0['color']}.")
```

### Adding New Key-Value Pairs 

These are dynamic structures, you give the name of the dictionary followed by the new key in square brackets. 

```py
alien_0 = {'color': 'green', 'points': 5} 
print(alien_0)

alien_0['x_position'] = 0
alien_0['y_position'] = 25
print(alien_0) # {'color': 'green', 'points': 5, 'y_position': 25, 'x_position': 0}

```

As of Python 3.7, dictionaries retain the order in which they were defined.

### Complex Example

Give the names of the dictionary the key in square brackets, then the new value you want aassociated with that key.

```py
alien_0 = {'x_position': 0, 'y_position': 25, 'speed': 'medium'} 
print(f"Original position: {alien_0['x_position']}")

if alien_0['speed'] == 'slow':
	x_increment = 1 
elif alien_0['speed'] == 'medium':
	x_increment = 2 
else: # This must be a fast alien.
	x_increment = 3

# The new position is the old position plus the increment. 
alien_0['x_position'] = alien_0['x_position'] + x_increment
print(f"New position: {alien_0['x_position']}")
```

### Removing Key-Value Pairs

This removes them permanently

```py
alien_0 = {'color': 'green', 'points': 5} 
print(alien_0)

del alien_0['points'] 
print(alien_0) # {'color': 'green'}
```

### A Dictionary of Similar Objects

A dictionary is also useful for store on ekind of information about many objects. For example a the results of a simple poll. 

```py
favorite_languages = { 
	'jen': 'python', 
	'sarah': 'c', 
	'edward': 'ruby', 
	'phil': 'python', 
}

language = favorite_languages['sarah'].title() 
print(f"Sarah's favorite language is {language}.") # Sarah's favorite language is C.
```

### Using get() to Access Values

Using keys in square brackets to retrieve the value you’re interested in from a dictionary might cause one potential problem: if the key you ask for doesn’t exist, you’ll get an error.

With get() method you can set a default value to return if key doesn’t exist. If you leave the second value empty, it will return a special value None, meant to indicate absence of a value. Which is talked about in chapter 8.

```py
alien_0 = {'color': 'green', 'speed': 'slow'} 
print(alien_0['points']) # KeyError

point_value = alien_0.get('points', 'No point value assigned.') 
print(point_value)
```

## Looping Through a Dictionary

### Looping Through All Key-Value Pairs

```py
user_0 = {
	'username': 'efermi', 
	'first': 'enrico', 
	'last': 'fermi', 
}

for key, value in user_0.items(): 
  print(f"\nKey: {key}")
  print(f"Value: {value}")

# Key: last
# Value: fermi
# Key: first
# Value: enrico
# Key: username
# Value: efermi 

for k, v in user_0.items() # Alternative
	print(f"\nKey: {key}")
  print(f"Value: {value}")
  
  u for name, language in favorite_languages.items():

v print(f"{name.title()}'s favorite language is {language.title()}.")
```

This could be setup in two differnet w



