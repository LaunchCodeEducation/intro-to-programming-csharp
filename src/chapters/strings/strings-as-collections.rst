=======================
Strings as Collections
=======================

Throughout the first chapters of this book we have used strings to represent words or phrases we wanted to print out. 
Our definition of a string was simple: a string is a sequence of characters inside double quotes. 

In this chapter we explore strings in much more detail. 
Strings come with a special group of operations that can be carried out on them, known as methods. 
Strings are also what is called a collection data type. Let's look at what this means.

Collection Data Types
---------------------

.. _string-chars:

.. index:: ! collection

.. index::
   single: data type; collection

Data types that are comprised of smaller pieces are called **collection data types**, or simply **collection types**. 
Depending on what we are doing, we may want to treat a value of a collection data type as a single entity (the whole collection), or we may want to access its parts.

.. index:: ! character

A **character** is a data type that contains exactly one element, such as ``'a'``, ``'?'``, or even ``' '`` (a single space character).  
In C#, characters are referred to as ``char`` data types and use single quotation marks.

We can think of strings as being built out of characters. In this way, strings can be broken down into smaller pieces.

.. figure:: figures/strings-as-collections-csharp.png
   :alt: The string "C Sharp" broken down into individual letters.

   A string is made up of characters, which are of length 1.

Strings are made up of smaller pieces, characters. 


Ordered Collections
-------------------

.. index::
   single: collection; ordered

We defined strings as *sequential* collections of characters. 
This means that the individual characters that make up the string are assumed to be in a particular order from left to right. 
The string ``"LaunchCode"`` is different from the string ``"CodeLaunch"``, even though they contain the exact same characters.

Collection types that allow their elements to be ordered are known as **ordered collections**, for reasons that will become clear to you very soon.
