Values and Data Types
================================


In the previous section, we saw how values can be represented by variables.  
In order to create variables in C#, we need to know and declare what **type** of data the value contains.   
Each value is a category called a **data type**. We will see many different data types throughout the course, but
the first four of note are the **int**, **double**, **string** and **char** types. 

Let’s start with **int** and **double**.  
Numbers can be classified into 2 different groups: whole numbers and decimals.  
When working with whole numbers, **int** is a great choice.  If you need decimals, 
**double** should be what you pick for now.  Why not use **double** for everything then?  
Think about the purpose of the number you will be working with.  If you are creating an 
inventory system for a clothing store, you are going to work with whole numbers as you 
cannot sell 3.25 shirts to a customer.  In this instance, an **int** would be your best choice.  
If you are making a finance app, you would want decimals so pick a **double**.

What if you want to work with words or characters?  Sequences of characters enclosed in **double 
quotes** such as “Hello, World!” or “yarn” are **strings**.  
They are called this because they contain a string of characters. (Get it?)  
And what if you only want one of these characters?  Then use the char data type.  
**Char** data types hold single characters in **single quotes**, such as ‘Q’, ‘v’, ‘ ‘ or ‘^’.  

Data typing helps the human building the code and the computer handle the values in the code.  
Knowing that you will be working with an **int** will help you anticipate the results of calculations, as in you will expect whole numbers.
It will also help the computer know how to use the value in your code, as in what will work and what will not.     


.. index:: ! GetType

If you are not sure what data type a value falls into, follow the value with ``.GetType()``.  

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine("Hello, World!".GetType());
      Console.WriteLine(17.GetType());
      Console.WriteLine(3.14.GetType());

   **Console Output**

   ::

      System.String
      System.Int32
      System.Double

Not surprisingly, C# reports that the data type of ``"Hello, World!"`` is ``System.String``.  
The data type of ``17`` is a ``System.Int32`` and ``3.14`` is ``System.Double``. 
What is the System?  System is one of the many built-in libraries that C# uses to compile code.
It is how C# knows how to treat an **int** differntly from a **double**, **string**, etc.  

.. index:: expression, returns

.. note:: Notice that ``Console.WriteLine("Hello, World!".GetType());`` prints out ``System.String`` to the console. 
   The ``.GetType()`` method is not printed to the console because the statement ``"Hello, World!.GetType()"`` is an **expression**. 
   Briefly, expressions are code segments that are reduced to a value. We will learn more about expressions soon.
   We say that an expression **returns** a value. That is, ``"Hello, World!".GetType()`` returns the value ``System.String``.



.. index:: operator

.. note::

   ``.GetType()`` is a C# entity known as an **method** that gets the type of the *current* instance.  
   A method is a type of code used to perform certain actions, can also be known as a function.  
   
   We will more about methods in upcoming sections.

There are data types other than string, char, int, and double, including object and function, which we will learn about in future chapters.

More On Strings
---------------

What about values like ``"17"`` and ``"3.2"``? They look like numbers, but they are in quotation marks like strings.

Run the following code to find out.

.. admonition:: Try It!

   .. replit:: csharp
      :linenos:
      :slug: Data-Types

      Console.WriteLine("17".GetType());
      Console.WriteLine("3.2".GetType());


.. admonition:: Question

   What is the data type of the values ``"17"`` and ``"3.2"``?


Double-quoted strings can contain single quotes inside them, as in ``"Bruce's beard"``.

C# cares whether you use single or double quotes to surround your strings. 
Once it has parsed the text of your program or command, the way it stores the value is identical in all cases, and the surrounding quotes are not part of the value.

.. warning:: 

   If a string contains an double quotes such as ``"Dave says, "Hi.""`` then surrounding it with double quotes gives unexpected results. 

   What happens if you run the following piece of code? 

   ::
   
      Console.WriteLine("Dave says, "Hi."");

If your strings already contain quotation marks, follow the English grammar rule of alternating double quotes with single quotes.

.. admonition:: Try It!
   
   .. sourcecode:: csharp
   
      Console.WriteLine("Dave says, 'Hi.'");

 

More On Numbers
---------------

When you type a large integer value, you might be tempted to use commas between groups of three digits, as in ``42,000``. 
This is not a legal integer in JavaScript, but it does mean something else, which is legal:

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(42000);
      Console.WriteLine(42,000);

   **Console Output**

   ::

      42000
      42 

Well, that's not what we expected at all! Because of the comma, ``Console.WriteLine`` 
chose to treat ``42,000`` as a *pair* of parameters which it is not overloaded for. 
The ``Console.WriteLine`` method only takes one parameter.  Parameters are separated by commas.  
When you begin to list items in the ``Console.WriteLine`` and use commas to separate you are now overloading the method, which will cause an error.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(42, 17, 56, 34, 11, 4.35, 32);
      Console.WriteLine(3.4, "hello", 45);

   **Console Output**

   ::

      error
      error

Remember not to put commas or spaces in your integers, no matter how big they are. Also revisit what we said in the chapter :ref:`how-programs-work`: formal languages are strict, the notation is concise, and even the smallest change might mean something quite different from what you intend.

Type Systems
------------

.. index:: ! type system

Every programming language has a **type system**, which is the set of rules that determine how the languages deals with data of different types. 
In particular, how values are divided up into different data types is one characteristic of a type system.

In many programming languages, integers and doubles are considered to be different data types. For example, in C# ``42`` is of the ``int`` 
data type, while ``42.0`` is of the ``double`` data type.  While JavaScript does not distinguish between doubles and integers. 

When discussing the differences between programming languages, the details of type systems are one of the main factors that programmers consider. There are other aspects of type systems beyond just how values are categorized. We will explore these in future lessons.

Check Your Understanding
------------------------

.. admonition:: Question

   Which of these is *not* a data type in C#?

   #. int
   #. string
   #. letter
   #. double

