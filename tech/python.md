# Python
## "you'll write your code once, but will read it many times, so optimize for readability."

## Naming variables
- You can give your variables any name you like, but it's a good practice to choose a name that describes the data that the variable points to. Sometimes it's hard to choose the right name, but it's a worthwhile task. Ideally, the name would be as short as possible and as descriptive as possible. Generally speaking, you should be able to accomplish that in one or two words.

- A Python best practice is to use all lowercase letters for variable names. If you need more than one word to adequately describe the variable's purpose, separate the words with an underscore (_) character.

## Boolean expression
> *if ... elif ... else*
- A Boolean expression is any code that returns a Boolean value. 
- A Boolean value is either True or False and is its own data type in Python, just like str and int.
- As before, the code block following the **else** statement is just as important. All indented lines of code below the else statement become part of its code block and are executed with the Boolean expression if the if statement evaluates to False.
- If that Boolean expression evaluates to True, the indented code below it runs. All code blocks that belong to other if, elif, and else statements are ignored.
  - Double *if* will excute both expressions regardless the outcome (unless they are nested: different indentations).
 
- The bool() function converted the strings 'True' and 'False' to the Boolean value True. 
  - When the function is supplied with an empty string, it returns False, while any other non-empty string returns True.
- In Python, we use the equality operator == to create a Boolean expression that evaluates two values for equality.
## Code block
- In Python, a code block is defined by using indentation (e.g. Tab key to insert four individual spaces).
## Operator
- An operator is like a mini function. Operators perform an operation on operands which could be literal values, variable values, or any identifier like a method or class. 
  - Arithmetic operators
  - Assignment operators
  - Bitwise operators
  - Comparison operators: *==, !=, <, >, >=, <=*
  - Identity operators
  - Logical operators: *and, or, not*
  - Membership operators
## [Escape sequence](https://docs.microsoft.com/en-us/learn/modules/python-format-strings/2-exercise-format-string-literals)
-  **\\** creates a escape sequence
-  **\\'** single-quote escape sequence 
-  **\n** escape sequence creates a new line
-  **\t** escape sequence adds a tab to the string when it's displayed
## [String helper method](https://docs.microsoft.com/en-us/learn/modules/python-format-strings/3-exercise-string-helper-functions)
- f-strings print(f'{ }')
## Determine data type
- > Armed with a healthy skepticism, you need to perform data-type and value checks on the data before you perform actual operations on or with the data.
- > Values have data types, and variables do not. A variable is merely pointed to a value, and it can point to any value of any data type.
- *type()* function displays the data type of a specified value
- *isinstance()* function tells you whether the value is what you expected. (True/False) e.g. isinstance(5, int) 
- *isnumeric()* function returns a Boolean value if the string value can be converted into a numeric value. (True/False) e.g. var.isnumeric() == True
- *isalnum()* Ensures that the string has no special characters, such as %, $, #, @, or !.
- *isalpha()* Ensures that the string contains only letters of the alphabet.
- others: *isdecimal()	, istitle(), isupper(), islower()*
## Use the exit() function to end the execution of your program immediately.
## standard library
- Built-in functions: functions that have been built into the Python interpreter, such as print() 
  - They are usually functions that are used so often that it would be laborious to import them each time you need them.
- Importing modules: features and functions only needed occasionally
## Iteration (repeat code execution until a certain condition is met)
- The *while* statement allows you to create a looping structure that continues to loop through a code block **until a Boolean expression evaluates to False**.
- The *break* statement to exit out of a code block prematurely before the Boolean expression evaluates to False.
- The *else* statement to provide a second code block that runs after the while statement's Boolean expression evaluates to False.
- The *continue* statement to skip over the remainder of the code block and set the execution path back to the Boolean expression.
  - **=**	Assign
  - **+=** Add then assign (e.g. count = count + 1, equivalent to count += 1)
  - **-=** Substract then assign
  - **\*=** Multiply then assign
  - **%=**, **//=**, **\**=**
## list (manage related data)
-  The square brackets allow us to use a zero-based numeric value to access an element of the list. e.g. \[0] first item, \[-1] last item
-  Create a slice \[0:1] 
    -  the value on the left side of the colon is inclusive. So the slice includes the element at that index. 
    -  the value on the right side of the colon is exclusive. So the slice doesn't contain the element at that
- reverse(), sort()
- **pop()** helper function takes the item at the index that you pass in as an argument. It removes the item from the list and assigns it to a variable for processing.
- append(), remove() item from the list
    - Calling these functions permanently changes the order in which the elements of the list are stored in memory.
- **extend()** combine a new list with an existing list
- clear() remove all items from a list
- The *in* keyword allows us to iterate through each item in a list
#### The *break* statement allows you to break out of the for iteration.
#### Use the *continue* statement in a code block to skip the remaining logic and move to the next item in a list in a for statement.
- random.choice(): randomly select an item from a list. 
- random.choices(, k= ): randomly select a number of items from a list and return a list of items. 

## function

```
def say_hello(name):
  print(f'Hello {name}!')
say_hello('Bob')
```
- default value
```
def say_hello(name='World'):
  print(f'Hello {name}!')
say_hello()
say_hello('Bob')
```
- improved version (user friendly)
```
def say_hi(name = 'user'):
    print(f'Hello {name} !')

name = input('please input your name here: ')
say_hi(name)
```
- Variables defined outside a function don't affect variables defined inside a function unless your code returns the inside value and then uses it. 
  - The scope of a function's variables is sealed off and hidden from code outside the function and the other way around.
```
value = 1

def some_function():
    value = 10
    return value

print(value)
some_function()
print(value)
```
