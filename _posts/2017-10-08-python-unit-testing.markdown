---
layout: post
title:  "Python unit testing"
date:   2017-10-08 14:08:25 +0100
categories: python unittesting
---
There are a few unit testing frameworks for python and differing opinions on the best way to structure a project.  As the aim is a reference for getting started with limited knowledge of python or unit testing in general I just chose one and got on with it.  The built in unittest module was chosen as this was the first example of unit testing in python that I came across and it was fairly straight forward to get started with.

* [Folder structure](#folder-structure)
* [Tests](#tests)
* [Test runner](#test-runner)
* [Appendix](#appendix)

## Folder structure

All tests are stored in there own directory names tests which needs to be defined as a package by adding an empty file called ```__init__.py``` to it.

Via powershell:
```Powershell
mkdir tests
new-item -type file tests\__init__.py
```

Via bash:
```
mkdir tests
touch tests/__init__.py
```


## Tests

Modules in the tests directory define one or more test cases, the methods of test cases are the tests.  For a method of a TestCase class to be considered a test it needs to start with ```test_```

e.g.
```Python
from maths.arithmetic import sum
import unittest


class SumCalculatesCorrectlyTestSuite(unittest.TestCase):
    '''
    Test that operations performs the calculation correctly
    '''

    def test_positive_values(self):
        self.assertEqual(2, sum(1, 1))

    def test_negative_values(self):
        self.assertEqual(-2, sum(-1, -1))

    def test_postive_and_negative(self):
        self.assertEqual(-3, sum(3, -6))

    def test_identity(self):
        self.assertEqual(4, sum(4, 0))

    def test_reciprocal(self):
        self.assertEqual(0, sum(4, -4))

    def test_commutative(self):
        self.assertEqual(sum(-5, 4), sum(4, -5))

```

TestCases also support methods such as setUp and tearDown which are run before and after each test method is executed.


## Test runner

To run the test you can execute the following command from the root of the project.  This will discover all unit tests within the project and execute them, reporting the status to the console.

```
python -m unittest
```

**Note** this must be run from the root of the project due to the ways that packages are discovered in python.  If you try to run the command from within the test folder the test will fail due to the imports in the unit test not being able to find the modules. This can be overcome but is not covered here.


## Appendix

* [Python - unittest](https://docs.python.org/3/library/unittest.html)
* [Python docs - unit testing](http://docs.python-guide.org/en/latest/writing/tests/)
* [Reference project](https://github.com/paulmoorenhs/python-unit-testing-example)
