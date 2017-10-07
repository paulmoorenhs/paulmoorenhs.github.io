---
layout: post
title:  "Python packages"
date:   2017-10-07 14:08:25 +0100
categories: setup atom
---
* [Packages](#packages)
* [Pip](#pip)


## Packages

A package is simply a directory with a ```__int__.py``` file inside it.

```
$ mkdir mypackage
$ cd mypackage
$ touch __init__.py
$ echo "# A Package" > __init__.py
$ cd ..
```

This creates a package that can be imported using the import.

```Python
>>> import mypackage
>>> mypackage.__file__
'mypackage/__init__.py'
```

To add and import a module:


* Create hello.py in mypackage:

  ```Python
  def hello():
      print("hello world")
  ```

* To import the function:

  ```Python
  >>> from mypackage.hello import hello
  >>> hello()
  ```


### Package discovery

```sys.path``` contains the list of locations that python looks for packages.

```Python
>>> import sys
>>> for path in sys.path:
>>>   print(path)
```
The first value in ```sys.path``` is an empty string which represents the current path.

The convention way of manually installing packages is to put them in the .../site-packages/ directory.  Alternatively you can add a directory to ```sys.path``` this can be done in several ways:

* [A path configuration file](#path-configuration-file)
* [Environment variables](#environment-variables)
* [Append to sys.path](#append-to-syspath)


#### Path configuration file

The most convenient way is to add a path configuration file to a directory that’s already in Python’s path. Path configuration files have an extension of .pth, and each line must contain a single path that will be appended to sys.path. (Because the new paths are appended to sys.path, modules in the added directories will not override standard modules. This means you can’t use this mechanism for installing fixed versions of standard modules.)


#### Environment variables

* ```PYTHONHOME```
* ```PYTHONPATH```

```PYTHONHOME``` sets an alternate value for the prefix of the Python installation. For example, if PYTHONHOME is set to /www/python/lib/python2.6/, the search path will be set to ['', '/www/python/lib/python2.6/', ...]

```PYTHONPATH``` sets a list of paths that will be added to the beginning of sys.path. For example, if PYTHONPATH is set to /www/python:/opt/py, the search path will begin with ['', '/www/python', '/opt/py', ...].


#### Append to sys.path

As ```sys.path``` is just a regular Python list any Python application can modify it by adding or removing entries.


### Standard package location

A Python installation has a ```lib\site-packages``` directory which is the default location for user installed packages.  A .pth file in this directory is maintained which contains paths to the directories where the extra packages are installed.


## Pip

Is a package management tool that allows you to list, install, upgrade, and uninstall packages. It uses the [Python Package Index](https://pypi.python.org/pypi) which is a package repository for open-source third-party Python packages. [Change pip Repository](https://mirror-riddle.gitbooks.io/notebook/content/pip/change-pip-repository.html) explains how to change the pip config files to point to a different repository.  [Setting up an private Pip repository](http://blog.xelnor.net/private-pypi/) explains how to create a  repository.

By default pip will install packages into the ```site-packages``` directory. To install a package:

```
$ pip install Markdown
```
In python:
```Python
>>> import markdown
>>> print markdown.markdown( '**Excellent**' )
```

The problem with this is that the packages are shared across all projects, if you upgrade a package for one project you upgrade it for all projects.


### requirements.txt

By conventions the packages that a project depends on are stored in a file in the project root directory called ```requirements.txt```.  This file can be supplied to pip as the required packages specification.

```
pip install -r requirements.txt
```

## Appendix
* [The hitchhikers guide to packaging](http://the-hitchhikers-guide-to-packaging.readthedocs.io/en/latest/introduction.html)
* [Tim Reilly's, Python, Pip, virtualenv installed on windows](http://timmyreilly.azurewebsites.net/python-pip-virtualenv-installation-on-windows/)
