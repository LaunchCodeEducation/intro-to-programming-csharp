====================
Strings as Objects
====================

Beyond bracket notation, there are many other tools we can use to work with strings. 
Talking about these tools requires some new terminology.

Object Terminology
------------------

.. index:: object, property, method

In C#, strings are objects, so to understand how we can use them in our programs, we must first understand some basics about objects.

An **object** is a collection of related data and operations. 
An operation that can be carried out on an object is known as a **method**. 
A piece of data associated with an object is known as a **property**.

.. admonition:: Example

   Suppose we created a ``Square`` object in C# to help calculate various properties of a square. 

   Since a square has four sides of the same length, it should have a property to represent this length. This property could be called ``Length``. For a given square, it will have a specific value, such as 4.

   Since a square has an area, it should have a method to calculate the area. This method could be called ``Area``, and it should calculate the area of a square using its ``Length`` property.

Dot Notation
^^^^^^^^^^^^^

You can think of methods and properties as functions and variables, respectively, that "belong to" an object. 
Properties and methods are accessed using **dot notation**, which dictates that we use the object name, followed by a ``.``, 
followed by the property or method name. When using a method, we must also use parentheses as we do when calling regular functions.
Notice we reference objects and methods with capital letters.

.. admonition:: Example

   Returning to the ``Square`` example, we can access its length by typing ``Square.Length``.

   We can calculate the area by calling ``Square.Area()``.

Referencing ``Length`` or ``Area`` by itself in code *does not* give you the value of ``Square.Length`` or carry out the 
calculation in ``Square.Area()``. It does not make sense to refer to a property or method without also referring to the associated object. 
Typing simply ``Length`` or ``Area()`` is ambiguous. There might be multiple squares, and it would be unclear which one you were asking about.


We will learn quite a bit more about objects in this course, including how to
use objects to create your own custom data types. This powerful C#
feature allows us to bundle up data and functionality in useful, modular ways.

Strings Are Objects
-------------------

The fact that strings are objects means that they have associated data and operations, or properties and methods as we will call them from now on.

.. index::
   single: string; length

Every string that we work with will have the same properties and methods. The most useful string property is named ``Length``, and it tells us how many characters are in a string.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      string firstName = "Grace";
      string lastName = "Hopper";

      Console.WriteLine(firstName + " has " + firstName.Length + " characters");
      Console.WriteLine(lastName + " has " + lastName.Length + " characters");

   **Console Output**

   ::

      Grace has 5 characters
      Hopper has 6 characters

Every string has a ``Length`` property, which is an integer.

The ``Length`` property is the only string property that we will use, but there are many useful string methods. 
We will explore these in depth in the section :ref:`string-methods`, but let's look at one now to give you an idea of what's ahead.

The ``ToLower()`` string method returns the value of its string in all lowercase letters. 
Since it is a method, we must precede it with a specific string in order to use it.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      string nonprofit = "LaunchCode";

      Console.WriteLine(nonprofit.ToLower());
      Console.WriteLine(nonprofit);

   **Console Output**

   ::

      launchcode
      LaunchCode

Notice that ``ToLower()`` does not alter the string itself, but instead *returns* the result of converting the string to all lowercase characters. 
In fact, it is not possible to alter the characters within a string, as we will now see.

Check Your Understanding
------------------------

.. admonition:: Question

   Given ``string word = 'Rutabaga'``, why does ``word.Length`` return the integer 8, but ``word[8]`` throws an exception?
