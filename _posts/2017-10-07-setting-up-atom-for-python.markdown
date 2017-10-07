---
layout: post
title:  "Setting up atom for python"
date:   2017-10-07 14:08:25 +0100
categories: setup atom
---
Basic setup of the atom text editor for python development.

* [Syntax highlighting](#syntax-highlighting)
* [Code execution](#code-execution)
* [Auto complete](#auto-complete)
* [Linter](#linter)
* [Code Formatter](#code-formatter)
* [File icons](#file-icons)
* [Code preview](#code-preview)



## Syntax highlighting

I think this comes built in as when I opened a python script the syntax was automatically highlighted.  I had been using atom for a while before I started with python so there is a chance that I had previously installed a syntax highlighting package but I do not remember doing so.


## Code execution

* Package name : script
* Run script : ctrl-shift-b

To test open a new file, set the language to python and enter the following script and then press ctrl-shift-b.
```python
print('hello world')
```
At output window should be displayed with 'Hello world' and the time it took to execute the script.


## Auto complete

1. Disable the built in auto complete packages:

  * autocomplete-plus
  * autocomplete-snippets

2. Install the python specific autocomplete package:

  * package name : autocomplete-python


## Linter

* Package name : linter-flake8
* **Note** you need to install the flake8 python package.
```python
pip install flake8
```

## Code formatter

* Package name : python-autopep8
* **Note** you need to install the autopep8 package.
```python
pip install autopep8
```
* **Note** the package has 'Foram on Save' setting that is off by default, this can be turrned on via the package settings.
* [Pep8](https://www.python.org/dev/peps/pep-0008/) is the python style guide.


## File icons

* Package name : file-icons
* Icons for different file types


## Code preview

* Package name : minimap
* Provides miniture outline of the code that allow you to navigate to points in the code.  It is helpfull for large files.
