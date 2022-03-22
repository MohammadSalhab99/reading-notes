# What Are Dunder Methods?
In Python, special methods are a set of predefined methods you can use to enrich your classes. They are easy to recognize because they start and end with double underscores, for example __init__ or __str__.

As it quickly became tiresome to say under-under-method-under-under Pythonistas adopted the term “dunder methods”, a short form of “double under.”

## Enriching a Simple Account Class
Throughout this article I will enrich a simple Python class with various dunder methods to unlock the following language features:

* Initialization of new objects
* Object representation
* Enable iteration
* Operator overloading (comparison)
* Operator overloading (addition)
* Method invocation
* Context manager support (with statement)

## Object Initialization: __init__
Right upon starting my class I already need a special method. To construct account objects from the Account class I need a constructor which in Python is the __init__ dunder:

      class Account:
          """A simple account class"""

          def __init__(self, owner, amount=0):
              """
              This is the constructor that lets us create
              objects from this class
              """
              self.owner = owner
              self.amount = amount
              self._transactions = []
The constructor takes care of setting up the object. In this case it receives the owner name,
an optional start amount and defines an internal transactions list to keep track of deposits and withdrawals.
## Object Representation: __str__, __repr__
It’s common practice in Python to provide a string representation of your object for the consumer of your class (a bit like API documentation.) There are two ways to do this using dunder methods:

__repr__: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.

__str__: The “informal” or nicely printable string representation of an object. This is for the enduser.

##Conclusion
I hope you feel a little less afraid of dunder methods after reading this article. A strategic use of them makes your classes more Pythonic, because they emulate builtin types with Python-like behaviors.

As with any feature, please don’t overuse it. Operator overloading, for example, can get pretty obscure. Adding “karma” to a person object with +bob or tim << 3 is definitely possible using dunders—but might not be the most obvious or appropriate way to use these special methods. However, for common operations like comparison and additions they can be an elegant approach.

Showing each and every dunder method would make for a very long tutorial. If you want to learn more about dunder methods and the Python data model I recommend you go through the Python reference documentation.

Also, be sure to check out our dunder method coding challenge where you can experiment and put your newfound “dunder skills” to practice.
Source: https://dbader.org/blog/python-dunder-methods

## Statistics
Statistics module provides functions for calculating mathematical statistics of numeric Real-valued data.

mean(): Arithmetic mean (“average”) of data.
fmean(): Fast, floating point arithmetic mean.
geometric_mean(): Geometric mean of data.
harmonic_mean(): Harmonic mean of data.
median(): Median (middle value) of data.
median_low(): Low median of data.
median_high(): High median of data.
median_grouped(); Median, or 50th percentile, of grouped data.
mode(): Single mode (most common value) of discrete or nominal data.
multimode(): List of modes (most common values) of discrete or nominal data.
quantiles(): Divide data into intervals with equal probability.
pstdev(): Population standard deviation of data.
pvariance(): Population variance of data.
stdev(): Sample standard deviation of data.
variance(): Sample variance of data.
covariance(): Sample covariance for two variables.
correlation(): Pearson’s correlation coefficient for two variables.
linear_regression(): Slope and intercept for simple linear regression.

