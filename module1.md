Module 1 - Introduction
=======================

The Python Programming Language
-------------------------------

Python was created by Guido Van Rossum in the Netherlands. The language itself was created to be as simple as possible to read. The Python philosophy is summarised in the Zen of Python, a collection of guidelines that every Python core developer follows and every Python programmer should follow (there is more to the Zen but I just show the most important ones for a beginner).

```
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
```

Python is a language that is gaining a lot of popularity lately because of its ease of use and its “batteries included” philosophy. These batteries mean that any Python installation comes with a very powerful set of features, for example, http connectors. sqlite (a relational database), csv readers amongst many other.

This “batteries included” approach is one of the things that makes the language very powerful because any python installation has most of the day to day things needed.

**TODO: Mention python versions and set the one we are going to use**

Python is a very well documented language. You can check the [official documentation](https://docs.python.org/VERSION) that has every information you will need and it also has many tutorials you can try out.

Python as an interpreted language
---------------------------------

As mentioned before for this workshop we’ll be using Python X.X. To install Python on a FreeBSD machine type on the console as root:

    $ pkg install python

After installing python you’ll have access to its interpreter. Just type `python` on a console terminal and you’ll get a python shell.

This shell is your interface to python. Let’s try printing something back:

    >>> print "Hello World"
    Hello World

This python shell is called the interpreter. In this shell you can do anything with python. Let's try a more advanced example. Open a python shell (just type `python` in the terminal) and try the following commands.

    >>> print "1 + 1 is", 1 + 1
    1 + 1 is 2
    
As you can see python also does simple math operations as you would expect. Let's try importing a module so we can use some advanced features.

    >>> from math impor sin
    >>> sin(1)
    0.8414709848078965
    
Here we are importing the `sin` function from the `math` module a more verbose way of reading the import line could be: from the math module import the sin function.

Imports and virtual environments
--------------------------------




Using a text editor to create python scripts
--------------------------------------------

Pretty easy right. Now let's try creating a python file that runs this code. Open your favourite text editor 