---
layout: page
title: How to Write Python Code in a Standardized Manner
author: Yifei Zhu
comments: true
tags:
 - Author Guidelines
 - Python
---
## Introduction
Strictly speaking, there is no strict standard for coding languages as long as the correct code syntax is followed.
However, for the sake of code readability, it is advisable for code to adhere to relevant coding conventions and standards.
For example, Python codes should follow the **PEP8- Style Guide for Python Code** ([English](https://peps.python.org/pep-0008/)/[Chinese](https://link.zhihu.com/?target=https%3A//zh-google-styleguide.readthedocs.io/en/latest/google-python-styleguide/python_language_rules/%23id1))

In this wiki project, for the convenience of everyone for reference, calling, collaboration, and unified management, we encourage everyone to upload Python code in a standardized manner.
Here, we will demonstrate, with specific examples, **how to write Python code in a standardized way in the context of collaborative work in our group's project.**
Our focus will be on key points that require emphasis and commonly encountered issues, without delving into all the specific details.


## Case study：
```Python
"""
Author: Yifei Zhu
Date: 2024-01-27
"""
class MyCalculator:
    """
    A simple calculator class for performing basic arithmetic operations on two input number.
    Note:
        - Currently, we only implemented addition and subtraction in this class.
        - When calling this class, the sys module must be imported.
    """

    def __init__(self, first_nu, second_nu):
        """Initializes the Calculator.
        Convert the a and b to float format.
        Exit the program while an exception is raised.

        Parameters
        ----------
        first_nu:   a float or an int.
                    The first number to perform basic arithmetic operations.
        second_nu:  a float or an int.
                    The first number to perform basic arithmetic operations.
        Notes
        ----------
        You can input numbers in int or float format.
        """
        try:
            self.first_nu = float(first_nu) # Convert the input number to float format.
            self.second_nu = float(second_nu)
        except Exception as e:
            print(f"An exception occurred: {e}")
            sys.exit(1)

    def add_a_to_b(self) -> float:
        """Adds two numbers.
        The first number add the second number.

        Returns
        -------
        res:    a float or an int.
                The result of adding two numbers.
        """
        return self.first_nu + self.second_nu

    def subtract_b_from_a(self) -> float:
        """Subtracts two numbers.
        Subtract the second number from the first number.

        Returns
        -------
        res:    a float or an int.
                The result of subtracting the second number from the first number.
        """
        return self.first_nu - self.second_nu

```
Notes:

- At the beginning of the file, it is necessary to specify the author, date, and other information.
- Whenever you define a class or function, you should include a section that describes the function, its purpose, the meanings and formats of its parameters and return values, as well as any considerations for others when calling it.
- Classes are named using CamelCase.
- Global variables and constants are named in uppercase.
- Names all functions and regular variables in lowercase and connects words with an underline.
- Variables or functions starting with a single underscore (_) are considered protected (they won't be included when using from module `import *`).
- Instance variables or methods starting with a double underscore (__) are considered private within the class (for example, `__name__`).

