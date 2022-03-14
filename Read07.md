# Python Scope & the LEGB Rule
The scope can be dfined as the area of a program that you can access anything like vaiables ,funtions and objects defind within this scope only.
The most common scopes are :
The global Scope 
The local Scope

The Scopes Came because the basic programming languages have only the global names, and the maintaining and debugging to programs wrote with this languages was vary hard .

## Python Scope vs Namespace
Python scopes are implemented as dictionaries that map names to objects. These dictionaries are commonly called namespaces.


## Using the LEGB Rule for Python Scope
Python resolves names using the so-called LEGB rule,The letters LEGB stands for Local, Enclosing, Global, and Built-in.

Local scope :  is the code block or body of any Python function or lambda expression.

Enclosing scope : is a special scope that only exists for nested functions. This Scope give the access on names defined in the enclosing function to  the inner functions.

Global (or module):  scope is the top-most scope in a Python program, script, or module.

Built-in scope is a special Python scope that’s created or loaded whenever you run a script or open an interactive session.

