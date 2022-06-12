You are here: Home / Basics / List Comprehensions in Python
List Comprehensions in Python
Author: Josh Petty
Last Updated: August 30, 2021

Table of Contents
Syntax
Create a List with range()
Create a List Using Loops and List Comprehension in Python
Multiplying Parts of a List
Show the first letter of each word using Python
Lower/Upper case converter using Python
Print numbers only from a given string
Parsing a file using list comprehension
Using functions in list comprehensions
In conclusion
Related Posts
Chances are you’ll use a lot of lists as a Python programmer. While we’re all big fans of for loops (and nested for loops), Python provides a more concise method for handling lists and list comprehension. 

In order to keep your code elegant and readable, it’s recommended that you use Python’s comprehension features.

List comprehension is a powerful and concise method for creating lists in Python that becomes essential the more you work with lists, and lists of lists.


Syntax
Consider the following example:


my_new_list = [ expression for item in list ]

You can see from this example that three ingredients are necessary for a python list comprehension to work.

First is the expression we’d like to carry out. expression inside the square brackets.
Second is the object that the expression will work on. item inside the square brackets.
Finally, we need an iterable list of objects to build our new list from. list inside the square brackets.
To understand the list comprehension, imagine it like this: you’re going to perform an expression on each item in the list. The expression will determine what item is eventually stored in the output list. 

Not only can you perform expressions on an entire list in a single line of code, but, as we’ll see later, it’s possible to add conditional statements in the form of filters, which allows for more precision in the way lists are handled.

Notes about Lists Comprehensions
List comprehension methods are an elegant way to create and manage lists. 
In Python, list comprehensions are a more compact way of creating lists. 
More flexible than for loops, list comprehension is usually faster than other methods.
Create a List with range()
Let’s start by creating a list of numbers using Python list comprehensions. We’ll take advantage of Python’s range() method as a way to create a list of digits.


Example 1: Creating a list with list comprehensions

# construct a basic list using range() and list comprehensions
# syntax
# [ expression for item in list ]
digits = [x for x in range(10)]

print(digits)
Output

[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
Let’s break down this python example by starting with the first ‘x’. This is our expression. It doesn’t do anything because we’re simply recording the number. The second ‘x’ represents each item in the list created by the range() method.

In the python example above, we’re using the range() method to generate a list of numbers. Python iterates(or loops) through each item in that range, and saves a copy of the item in a new list called digits.

Perhaps that seems redundant? That’s only because you’ve yet to see the real potential of list comprehension.

Create a List Using Loops and List Comprehension in Python
To better illustrate how a list comprehension can be used to write more efficient Python code, we’ll take a look at a side by side comparison. 


In the following example, you’ll see two different techniques for creating a Python list. The first is a for loop. We’ll use it to construct a list of the powers of two.

Example 2: Comparing list creation methods in Python

First, create a list and loop through it. Add an expression, in this example, we’ll raise x to the power of 2.

# create a list using a for loop
squares = []

for x in range(10):
    # raise x to the power of 2
    squares.append(x**2)

print(squares)
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
Output

The same thing can be done using a list comprehension, but with a fraction of the code. Let’s take a look at how to create a list of squares using the list comprehension method.

# create a list using list comprehension
squares = [x**2 for x in range(10)]

print(squares)
Even in this basic example, it’s obvious that list comprehensions reduce the code necessary to complete rather complicated task when working with a list.


Multiplying Parts of a List
What if we wanted to multiply every number in a list by three in Python? We could write a for loop and store the results in a new list, or we could use list comprehensions.

Example 3: Multiplication with list comprehensions

# create a list with list comprehensions
multiples_of_three = [ x*3 for x in range(10) ]

print(multiples_of_three)
Output

[0, 3, 6, 9, 12, 15, 18, 21, 24, 27]
By taking advantage of list comprehensions, it’s possible to work on only part of a list. For instance, if you only wanted the even numbers in a given range, you could find them using a filter.

Adding a filter to the list comprehension allows for greater flexibility. By using filters, we can select certain items from the list, while excluding others. This is an advanced feature of lists in Python.

even_numbers = [ x for x in range(1,20) if x % 2 == 0]
Output


[2, 4, 6, 8, 10, 12, 14, 16, 18]
Show the first letter of each word using Python
So far we’ve seen examples of building a list of numbers in Python. Next, let’s try working with strings and the various ways list comprehensions can be used to elegantly handle a list of strings.

Example 4: Using list comprehensions with strings

# a list of the names of popular authors
authors = ["Ernest Hemingway","Langston Hughes","Frank Herbert","Toni Morrison",
    "Emily Dickson","Stephen King"]

# create an acronym from the first letter of the author's names
letters = [ name[0] for name in authors ]
print(letters)
Output

['E', 'L', 'F', 'T', 'E', 'S']
List comprehensions can make solving issues involving strings much easier using simplified expressions. These methods can save time and precious lines of code.

Example 5: Separating the characters in a string


# use list comprehension to print the letters in a string
letters = [ letter for letter in "20,000 Leagues Under The Sea"]

print(letters)
Output

['2', '0', ',', '0', '0', '0', ' ', 'L', 'e', 'a', 'g', 'u', 'e', 's', ' ', 'U', 'n', 'd', 'e', 'r', ' ', 'T', 'h', 'e', ' ', 'S', 'e', 'a']
Lower/Upper case converter using Python
Using list comprehension to loop through a string in Python, it’s possible to convert strings from lower case to upper case, and vice versa. 

Making use of Python’s lower() and upper() methods, we’ll use list comprehension to achieve this common task.

Example 6: Changing a letter’s case

lower_case = [ letter.lower() for letter in ['A','B','C'] ]
upper_case = [ letter.upper() for letter in ['a','b','c'] ]

print(lower_case, upper_case)
Output


['a', 'b', 'c'] ['A', 'B', 'C']
Print numbers only from a given string
Another interesting exercise is to extract numbers from a string. For example, we may have a database of names and phone numbers.

It would be useful if we could separate the phone numbers from the names. Using list comprehensions, we can do just that.

Taking advantage of Python’s isdigit() method, we can extract the phone number from the user data.

Example 7: Identify numbers in a string using the isdigit() method

# user data entered as name and phone number
user_data = "Elvis Presley 987-654-3210"
phone_number = [ x for x in user_data if x.isdigit()]

print(phone_number)
Output

['9', '8', '7', '6', '5', '4', '3', '2', '1', '0']
Parsing a file using list comprehension
It’s also possible to read files in Python using list comprehension. To demonstrate, I’ve created a file called dreams.txt and pasted the following text, a short poem by Langston Hughes.


Hold fast to dreams
For if dreams die
Life is a broken-winged bird
That cannot fly.
-Langston Hughes

Using list comprehension, we can iterate through the lines of text in the file and store their contents in a new list.

Example 8: Reading a poem with list comprehensions

# open the file in read-only mode
file = open("dreams.txt", 'r')
poem = [ line for line in file ]

for line in poem:
    print(line)
Output

Hold fast to dreams

For if dreams die

Life is a broken-winged bird

That cannot fly.

-Langston Hughs
Using functions in list comprehensions
So far we’ve seen how to use list comprehension to generate lists using some basic Python methods like lower() and upper(). But what if we wanted to use our own Python functions?


Not only can we write our own functions with list comprehensions, but we can also add filters to better control the statements.

Example 9: Adding arguments to list comprehension

# list comprehension with functions
# create a function that returns a number doubled
def double(x):
    return x*2

nums = [double(x) for x in range(1,10)]
print(nums)
Output

[2, 4, 6, 8, 10, 12, 14, 16, 18]
Filtering elements from the list can be done using additional arguments. In the following example, only even numbers are selected.

# add a filter so we only double even numbers
even_nums = [double(x) for x in range(1,10) if x%2 == 0]
print(even_nums)
Output

[4, 8, 12, 16]
Additional arguments can be added to create more complex logic:


nums = [x+y for x in [1,2,3] for y in [10,20,30]]
print(nums)
Output

[11, 21, 31, 12, 22, 32, 13, 23, 33]
In conclusion
Hopefully you’ve seen the potential of list comprehensions and how they can be used to write more elegant Python code. Writing compact code is essential for maintaining programs and working with teams. 

Learning to make use of advanced features like list comprehension will save time and improve productivity. 

Not only will your colleagues thank you when your Python code is more concise and easier to read, but you’ll thank yourself when you come back to a program you haven’t worked on in months and the code is manageable.

