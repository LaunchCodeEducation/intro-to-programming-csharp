Values and Data Types
================================

Programs may be thought of as being made up of two things:

1. Data
2. Operations that manipulate data

This chapter focuses primarily on the first of these two fundamental components, data. 

.. index:: ! value

Data can be stored in a program in a variety of ways. The most basic unit of data is a value.

.. _def-value:

A **value** is a specific piece of data, such as a word or a number.  Some examples are ``5``, ``-7.4``, and ``"Hello, World!"``.

Each value belongs to a category called a **data type**. We will see many
different data types throughout the course, the first four of note are the
**int**, **double**, **string** and **char** types. 

Numeric values can be divided into 2 categories:
whole numbers and decimals.  In C# we use the data type **int** when working with whole numbers, and
the data type **double** when working with decimals.  Numeric values such as ``-14`` and ``23998`` are an 
**int** data type while values such as ``3.223``, ``9.99928820`` would be a **double** data type.  

Sequences of characters enclosed in quotes, such as ``"Hello, World!"``, are **strings**, so-called because they 
contain a string of letters. Strings must be enclosed in double quotes.  A **char** is a single letter surrounded by
single quotation marks, such as ``'Q'``.  Char is short for "character" and can contain upper or lowercase letters.


More On Strings
---------------

What about values like ``"17"`` and ``"3,2"``?  They look like numbers, 
but they are in quotation marks which makes them strings.  Strings in C# are 
enclosed in double quotes (``"``).

.. index:: ! integer, ! double, ! char

More On Numbers
---------------

When you type a large integer value, you might be tempted to use commas between groups of three digits, 
as in ``42,000``. This is not a legal integer in JavaScript, but it does mean something else, which is legal:

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(42000);
      Console.WriteLine(42,000);

   **Console Output**

   ::

      42000
      error

Well, that's not what we expected at all! Commas in numbers are for humans to have an easier time counting large numbers.  
Computers don't need them in this context.  In coding, commas are typically used to separate items in various contexts.  More on that later.  

Remember not to put commas or spaces in your integers, no matter how big they are. 
Also revisit what we said in the chapter :ref:`how-programs-work`: formal languages are strict, 
the notation is concise, and even the smallest change might mean something quite different from what you intend.
