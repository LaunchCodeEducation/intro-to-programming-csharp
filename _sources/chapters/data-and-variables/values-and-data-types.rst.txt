=======================
Values and Data Types
=======================

Programs may be thought of as being made up of two things:

1. Data
2. Operations that manipulate data

This chapter focuses primarily on the first of these two fundamental components, data. 

.. index:: ! value

Data can be stored in a program in a variety of ways. The most basic unit of data is a value.

.. _def-value:

.. _typeof:

A **value** is a specific piece of data, such as a word or a number. 
Some examples are ``5``, ``5.2``, ``'r``, and ``"Hello, World!"``.

.. index:: ! data type, ! number, ! string, ! type 

Each value belongs to a category called a **data type**. We will see many
different data types throughout the course, the first three of which are the
**int**, **double**, and **string** types. Whole numeric values such as ``4`` and ``33`` are
**ints**.  **Doubles** deal with decimal points, some examples include ``2.34`` and ``3.14159265``. Sequences of characters enclosed in double quotes, such as
``"Hello, World!"``, are **strings**, so-called because they contain a string of
letters. Strings must be enclosed in double quotes. 

.. index:: ! integer, ! float

.. index:: ! typeof

If you are not sure what data type a value falls into, follow the value with ``GetType``.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(("Hello, World!").GetType());
      Console.WriteLine(17.GetType());
      Console.WriteLine(3.14.GetType());

   **Console Output**

   ::

      System.String
      System.Int32
      System.Double

Not surprisingly, C# reports that the data type of ``"Hello, World!"`` is ``string``.  
The data type of ``17`` is assumed ``int`` because it is a whole number, and ``3.14`` 
is ``double`` because of the decimal point. 

.. index:: expression, returns

.. note:: Notice that ``Console.WriteLine(("Hello, World!").GetType());`` prints out ``System.String`` to the console.  The ``GetType`` method is not printed to the console because the statement ``"Hello, World!" GetType`` is an **expression**. Briefly, expressions are code segments that are reduced to a value. We will learn more about expressions soon.

   We say that an expression **returns** a value. That is, ``"Hello, World!" GetType`` returns the value ``System.String``.

.. index:: operator

.. note::

   ``GetType`` is a C# entity known as an **method**. It carries out some kind of action, which is already built into it.
   
   We will more about methods in upcoming sections.

There are data types other than string and number, including object and method, which we will learn about in future chapters.

More On Strings
---------------

What about values like ``"17"`` and ``"3.2"``? They look like numbers, but they are in double 
quotation marks making them strings.

Double-quoted strings can contain single quotes inside them, as in ``"Bruce's beard"``.


More On Numbers
---------------

When you type a large integer value, you might be tempted to use commas between groups of 
three digits, as in ``42,000``. This is not a legal integer in C#. 

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(42000);
      Console.WriteLine(42,000);

   **Console Output**

   ::

      42000
      error CS1502: ...`System.Console.WriteLine(string, object)' has some invalid arguments

Well, that's not what we expected at all! 
Because of the comma, C# chose to treat ``42,000`` as a pair separate entries.  
This causes an error in the Console.WriteLine() which was built to only work with a single entry.  
Adding additional entries separated by commas will overload it, causing an error.


Remember not to put commas or spaces in your integers, no matter how big they are. 
Also revisit what we said in the chapter :ref:`how-programs-work`: formal languages are strict, 
the notation is concise, and even the smallest change might mean something quite different from what you intend.


Type Systems
------------

.. index:: ! type system

Every programming language has a **type system**, which is the set of rules that determine how the languages deals with data of different types. In particular, how values are divided up into different data types is one characteristic of a type system.


When discussing the differences between programming languages, the details of type systems are one of the main factors that programmers consider. There are other aspects of type systems beyond just how values are categorized. We will explore these in future lessons.

Check Your Understanding
------------------------

.. admonition:: Question

   Which of these is *not* a data type in C#?

   #. integer
   #. string
   #. letter
   #. object
