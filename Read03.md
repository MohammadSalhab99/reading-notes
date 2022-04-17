# Read and write files in python

## What Is a File?
Before we can go into how to work with files in Python, it’s important to understand what exactly a file is and how modern operating systems handle some of their aspects.

At its core, a file is a contiguous set of bytes used to store data. This data is organized in a specific format and can be anything as simple as a text file or as complicated as a program executable. In the end, these byte files are then translated into binary 1 and 0 for easier processing by the computer.

Files on most modern file systems are composed of three main parts:

1- Header: metadata about the contents of the file (file name, size, type, and so on)
2- Data: contents of the file as written by the creator or editor
3- End of file (EOF): special character that indicates the end of the file

## File Paths
When you access a file on an operating system, a file path is required. The file path is a string that represents the location of a file. It’s broken up into three major parts:

1- Folder Path: the file folder location on the file system where subsequent folders are separated by a forward slash / (Unix) or backslash \ (Windows)
2- File Name: the actual name of the file
3- Extension: the end of the file path pre-pended with a period (.) used to indicate the file type
Here’s a quick example. Let’s say you have a file located within a file structure like this:

    /
    │
    ├── path/
    |   │
    │   ├── to/
    │   │   └── cats.gif
    │   │
    │   └── dog_breeds.txt
    |
    └── animals.csv
Let’s say you wanted to access the cats.gif file, and your current location was in the same folder as path. In order to access the file, you need to go through the path folder and then the to folder, finally arriving at the cats.gif file. The Folder Path is path/to/. The File Name is cats. The File Extension is .gif. So the full path is path/to/cats.gif.

Now let’s say that your current location or current working directory (cwd) is in the to folder of our example folder structure. Instead of referring to the cats.gif by the full path of path/to/cats.gif, the file can be simply referenced by the file name and extension cats.gif.

    /
    │
    ├── path/
    |   │
    |   ├── to/  ← Your current working directory (cwd) is here
    |   │   └── cats.gif  ← Accessing this file
    |   │
    |   └── dog_breeds.txt
    |
    └── animals.csv
But what about dog_breeds.txt? How would you access that without using the full path? You can use the special characters double-dot (..) to move one directory up. This means that ../dog_breeds.txt will reference the dog_breeds.txt file from the directory of to:

    /
    │
    ├── path/  ← Referencing this parent folder
    |   │
    |   ├── to/  ← Current working directory (cwd)
    |   │   └── cats.gif
    |   │
    |   └── dog_breeds.txt  ← Accessing this file
    |
    └── animals.csv
The double-dot (..) can be chained together to traverse multiple directories above the current directory. For example, to access animals.csv from the to folder, you would use ../../animals.csv.

## Line Endings
One problem often encountered when working with file data is the representation of a new line or line ending. The line ending has its roots from back in the Morse Code era, when a specific pro-sign was used to communicate the end of a transmission or the end of a line.

Later, this was standardized for teleprinters by both the International Organization for Standardization (ISO) and the American Standards Association (ASA). ASA standard states that line endings should use the sequence of the Carriage Return (CR or \r) and the Line Feed (LF or \n) characters (CR+LF or \r\n). The ISO standard however allowed for either the CR+LF characters or just the LF character.

Windows uses the CR+LF characters to indicate a new line, while Unix and the newer Mac versions use just the LF character. This can cause some complications when you’re processing files on an operating system that is different than the file’s source. Here’s a quick example. Let’s say that we examine the file dog_breeds.txt that was created on a Windows system:

    Pug\r\n
    Jack Russell Terrier\r\n
    English Springer Spaniel\r\n
    German Shepherd\r\n
    Staffordshire Bull Terrier\r\n
    Cavalier King Charles Spaniel\r\n
    Golden Retriever\r\n
    West Highland White Terrier\r\n
    Boxer\r\n
    Border Terrier\r\n
This same output will be interpreted on a Unix device differently:

    Pug\r
    \n
    Jack Russell Terrier\r
    \n
    English Springer Spaniel\r
    \n
    German Shepherd\r
    \n
    Staffordshire Bull Terrier\r
    \n
    Cavalier King Charles Spaniel\r
    \n
    Golden Retriever\r
    \n
    West Highland White Terrier\r
    \n
    Boxer\r
    \n
    Border Terrier\r
    \n
    This can make iterating over each line problematic, and you may need to account for situations like this.

## Character Encodings
Another common problem that you may face is the encoding of the byte data. An encoding is a translation from byte data to human readable characters. This is typically done by assigning a numerical value to represent a character. The two most common encodings are the ASCII and UNICODE Formats. ASCII can only store 128 characters, while Unicode can contain up to 1,114,112 characters.

ASCII is actually a subset of Unicode (UTF-8), meaning that ASCII and Unicode share the same numerical to character values. It’s important to note that parsing a file with the incorrect character encoding can lead to failures or misrepresentation of the character. For example, if a file was created using the UTF-8 encoding, and you try to parse it using the ASCII encoding, if there is a character that is outside of those 128 values, then an error will be thrown.

## Opening and Closing a File in Python
When you want to work with a file, the first thing to do is to open it. This is done by invoking the open() built-in function. open() has a single required argument that is the path to the file. open() has a single return, the file object:

file = open('dog_breeds.txt')
After you open a file, the next thing to learn is how to close it.

Warning: You should always make sure that an open file is properly closed.

It’s important to remember that it’s your responsibility to close the file. In most cases, upon termination of an application or script, a file will be closed eventually. However, there is no guarantee when exactly that will happen. This can lead to unwanted behavior including resource leaks. It’s also a best practice within Python (Pythonic) to make sure that your code behaves in a way that is well defined and reduces any unwanted behavior.

When you’re manipulating a file, there are two ways that you can use to ensure that a file is closed properly, even when encountering an error. The first way to close a file is to use the try-finally block:

reader = open('dog_breeds.txt')
try:
    # Further file processing goes here
finally:
    reader.close()
If you’re unfamiliar with what the try-finally block is, check out Python Exceptions: An Introduction.

The second way to close a file is to use the with statement:

with open('dog_breeds.txt') as reader:
    # Further file processing goes here
The with statement automatically takes care of closing the file once it leaves the with block, even in cases of error. I highly recommend that you use the with statement as much as possible, as it allows for cleaner code and makes handling any unexpected errors easier for you.

Most likely, you’ll also want to use the second positional argument, mode. This argument is a string that contains multiple characters to represent how you want to open the file. The default and most common is 'r', which represents opening the file in read-only mode as a text file:

with open('dog_breeds.txt', 'r') as reader:
    # Further file processing goes here
Other options for modes are fully documented online, but the most commonly used ones are the following:

Character |	Meaning
--- | --- 
'r'	|Open for reading (default)
'w'	|Open for writing, truncating (overwriting) the file first
'rb' or 'wb' |	Open in binary mode (read/write using byte data)


source :https://realpython.com/read-write-files-python/

# Exceptions

## Exceptions versus Syntax Errors
Syntax errors occur when the parser detects an incorrect statement. Observe the following example:

  >>> print( 0 / 0 ))
    File "<stdin>", line 1
      print( 0 / 0 ))
                    ^
  SyntaxError: invalid syntax
The arrow indicates where the parser ran into the syntax error. In this example, there was one bracket too many. Remove it and run your code again:

  >>> print( 0 / 0)
  Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
  ZeroDivisionError: integer division or modulo by zero
This time, you ran into an exception error. This type of error occurs whenever syntactically correct Python code results in an error. The last line of the message indicated what type of exception error you ran into.

Instead of showing the message exception error, Python details what type of exception error was encountered. In this case, it was a ZeroDivisionError. Python comes with various built-in exceptions as well as the possibility to create self-defined exceptions.

## Raising an Exception
We can use raise to throw an exception if a condition occurs. The statement can be complemented with a custom exception.


## The AssertionError Exception
Instead of waiting for a program to crash midway, you can also start by making an assertion in Python. We assert that a certain condition is met. If this condition turns out to be True, then that is excellent! The program can continue. If the condition turns out to be False, you can have the program throw an AssertionError exception.


## The try and except Block: Handling Exceptions
The try and except block in Python is used to catch and handle exceptions. Python executes code following the try statement as a “normal” part of the program. The code that follows the except statement is the program’s response to any exceptions in the preceding try clause.

### Here are the key takeaways:

- A try clause is executed up until the point where the first exception is encountered.
- Inside the except clause, or the exception handler, you determine how the program responds to the exception.
- You can anticipate multiple exceptions and differentiate how the program should respond to them.
  
  source: https://realpython.com/python-exceptions/
Aoid using bare except clauses.
