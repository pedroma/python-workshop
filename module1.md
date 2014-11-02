Module 1 - Introduction
=======================

The Python Programming Language
-------------------------------

Python was created by Guido Van Rossum in the Netherlands. The language itself was created to be as simple as possible to read an use. Guido is still a huge part of Python and he is known in the community as the benevolent dictator for life (BDFL). The Python philosophy is summarised in the [Zen of Python](http://legacy.python.org/dev/peps/pep-0020/), a collection of guidelines that every Python core developer follows and every Python programmer should follow. The most important ones for people starting with Python are:

    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Readability counts.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.

Python is a language that is gaining a lot of [popularity as a learning language](http://cacm.acm.org/blogs/blog-cacm/176450-python-is-now-the-most-popular-introductory-teaching-language-at-top-us-universities/fulltext) because of its ease of use and its “batteries included” philosophy. These batteries mean that any Python standard distribution comes with a very powerful set of libraries to help overcome common simple problem. For example, http connectors, sqlite (a relational database), csv readers, a simple http server (actually called `SimpleHTTPServer`) amongst many other.

The current version of Python is 3.4. But for this workshop we'll use version 2.7 which is in FreeBSD's repositories. Everything we do here also applies to python 3.4.

Python is a very well documented language. You can check the [official documentation](https://docs.python.org/2.7) that has every information you will need and also many tutorials you can try out.

Python as an interpreted language
---------------------------------

As mentioned before for this workshop we’ll be using Python 2.7. To install Python on a FreeBSD machine type on the console as root:

    $ pkg install python

After installing python you’ll have access to the interpreter. Just type `python` on a console terminal and you’ll get a python shell.

This shell is your interface to python, with it you can do anything that python can do. Let’s try printing something back:

    >>> print "Hello World"
    Hello World
    
As a side note: if you see print being used with parentheses, like `print("hello")` don't worry, it also works but only in version before 3.0.
This python shell is called the interpreter. In this shell you can do anything with python. Let's try a more advanced example. Open a python shell (just type `python` in the terminal) and try the following commands.

    >>> print "1 + 1 is", 1 + 1
    1 + 1 is 2
    
As you can see python also does simple math operations as you would expect. Let's try importing a module so we can use some advanced features.

    >>> from math impor sin
    >>> sin(1)
    0.8414709848078965
    
Here we are importing the `sin` function from the `math` module. A more verbose way of reading the import line could be: from the `math` module import the `sin` function. 

Now that you know how to use the shell try running the following line: `import this`. What do you get?

Imports and virtual environments
--------------------------------

Python has a particular way of doing imports. Let's take the `from math import sin` line from the example before. Where does the `math` module come from? The `math` module comes from the python standard library. When you try to import something python will try several places starting with the local folder you are on and then going through the `PYTHONPATH` enviroment variable (if you don't know what that is just think of it as a list of folders for python to search through). In this course we'll be installing some third party python packages and we'll be using a python package installation tool called `pip`. By default this tool installs the packages system wide. This means that anyone that opens a python shell would have the package available, which might not seen like a bad thing but there are some drawbacks. This would lead to problem down the line because you are only allowed one version of each package in your system and if 2 users needed 2 different version this wouldn't work.

This is where virtual environments come in. Basically we are going to be creating an environment per project we do. This way we'll be able to install everything we need whithout interfering with the system. Let's get started.

First we need to install the virtual environment package. Let's do that using `pkg`.

    $ pkg install py27-virtualenv

Now that virtual environment is installed let's initialise one for this course.

    $ virtualenv python-workshop
    New python executable in python-workshop/bin/python2.7
    Also creating executable in python-workshop/bin/python
    Installing setuptools, pip...done.

Now that our virtual environment is installed lets `activate` it to make sure we are using the new python "installation" (it's not really a whole new installation, it's just some symbolic links to the system wide python).

    $ which python
    /usr/local/bin/python
    $ cd python-workshop
    $ source bin/activate
    (python-workshop)$ which python
    /usr/home/vagrant/python-workshop/bin/python

Notice how after activating the virtualenv the command prompt changed and the python used also changed? When your virtual environment is activated you can install any package without messing up the system. To deactivate the virtual environment you can just type `deactivate` in the console.

Try installing the requests package for python. With the virtual environment activated just type:

    $ pip install requests
    Downloading/unpacking requests
    Downloading requests-2.4.3-py2.py3-none-any.whl (459kB): 459kB downloaded
    Installing collected packages: requests
    Successfully installed requests
    Cleaning up...

And that's it. The [requests](http://docs.python-requests.org/en/latest/) package is installed and ready to be used. 

Let's test it to make sure it works. Open a python shell and try:

    >>> import requests
    >>> response = requests.get("https://google.com/")
    >>> response.content

This piece of code will get the HTML code for `https://google.com/`. The response content will have a lot of javascript too. This particular library is very use full to make requests to API's throughout the internet. For example: if you do a get to `http://ip-api.com/json` it will tell you what your current IP is and where you are. Try it out.

Using a text editor to create python scripts
--------------------------------------------

Now let's try creating a python script and run it in our interpreter. Open your favourite text editor. For graphical text editors (not console based) you can try [Brackets](http://brackets.io/). Create a file named `hello.py` in your virtual environment directory with the following content:

    print "Hello world"

Save the file and run:

    $ python hello.py
    Hello World

This is how easy it is to write script files in python. Let's create a more complex one just to show off some o f python. Let's use the `requests` library we installed in the previous section. Create a new file called `secondhello.py` and write the following:

    import requests
    print "What IP do you want to investigate?"
    ip = rawinput()
    response = requests.get("http://ip-api.com/json/" + ip)
    print response.json()
        
Save the file. Try running the code. It will ask you for some IP, grab [your own](http://whatismyip.com/) and paste it to the script when it asks for it.

Standards and batteries included
--------------------------------

Python is a standards language. Every feature that is included in python has a [PEP (Python Enhancement Proposals)](http://legacy.python.org/dev/peps/) associated with it. These PEP's are what guide the language when developing new features. Remember the Zen of Python from before? It is defined in [PEP20](http://legacy.python.org/dev/peps/pep-0020/). There is one particular PEP which everyone should be familiar with which is [PEP8](http://legacy.python.org/dev/peps/pep-0008/). This PEP defines a standard for python code styling. With this everyone should have the same code style when writing python. This will make everyones code much easier to read and understand. It's a very good practice to know and follow this PEP when writing Python.

When Python is mentioned as having "batteries included" this means that Python's standard library has a lot of modules that do some advanced things without having to install anything extra. Some examples of those modules are:

* urllib - this module is used to make HTTP requests
* csv - module used to read/write csv files
* math - advanced mathematical functions
* zlib - file compression compatible with gzip
* sqlite3 - relational database connector for [sqlite](http://www.sqlite.org/)
* pdb - the python debugger
* unittest - as the name states its a unit testing framework

These are just some examples of what comes with python. You can check the full list at [https://docs.python.org/2/library/](https://docs.python.org/2/library/).

What you learned
================

This is what you learned in this module:

* python's phylosofy
* first contact with the python interpreter
* how python imports work
* working on a virtual envinronment
* creating a python script
* standards and PEP8
* various modules which python comes bundled with