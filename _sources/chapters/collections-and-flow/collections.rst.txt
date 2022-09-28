.. index:: ! data structure

Collections
===========

Data Structures
---------------

A **data structure** lets us hold on to lots of data in a single place. It 
is a programming construct to aggregate many values into one value. Many 
types of data structures exist in various languages. A few examples are 
lists, dictionaries, arrays, tuples, etc. 

.. index:: ! collections, ! C# Collections Namespace

C# Collections Namespace
------------------------

C# provides powerful and flexible structures to store data, known as
**collections**. The **C# collections namespace** refers to the various interfaces
the language provides for implementing collection types. 

Here, we'll discuss a collection called ``List`` and compare it to the 
``Array`` class. We'll then introduce a third collection type called ``Dictionary``. 
These three collection types will be sufficient for our basic C# needs. 
For more, refer to the official C# documentation on `collections <https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections>`__.

In order to be able to access these collection types, we need to include the correct ``using`` statements.  
   

.. index:: ! using, ! namespace, class, ! assembly

.. _using-statement:

``using``
---------

The ``using`` statement in C# allows us to access classes, methods, and
data stored in different files other than the one we are currently in.

In C#, you can use any class that is available without having to import
the class - subject to two very important conditions:

1. The C# compiler must know that the class exists.
2. You must use the full name of the class.

Classes that are available to you may be those in the project you are currently working on, such as the ``MainClass`` in 
the replit.com IDE or those that come along with the .NET class library, as well as anything you might get 
from added dependencies.

.. admonition:: Example

   .. replit:: csharp
      :linenos:
      :slug: usingExamples-CSharp

      using System;
      
      namespace TempConv
      {

         class MainClass
         {
            public static void Main(string[] args) 
            {
               double fahrenheit;
               double celsius;
               string input;

               Console.WriteLine("Temperature in F:");
               input = Console.ReadLine();
               fahrenheit = double.Parse(input);

               celsius = (fahrenheit - 32) * 5 / 9;
               Console.WriteLine("The Temperature in C is: " + celsius);
               Console.ReadLine();
            }
         }
      }

The class naming system in C# is very hierarchical. The *full* name of the ``Console``
class used first on line 14 is really ``System.Console``. You can think of this name as having
two parts. The first part, ``System``, is called the **namespace**, and
the last part is the **class**. We’ll talk more about the class naming
system a bit later.   You have also seen ``System`` when you are checking the data type of varialbes.

One thing to know about the ``using`` statement is that it is not responsible for loading classes into memory.
That task falls on the **assembly**, which is the unit of compiled code created by the C# compiler.

The ``using`` statement tells the compiler that we are going to use a
shortened version of the class’s name. In this example, we are going to
use the class ``System.Console``, but we can refer to it as just
``Console``. We could use the ``System.Console`` class without any
problem and without any import statement provided that we always
referred to it by its full name.

Don’t just trust us, try it yourself! Remove the ``using`` statement and
change ``Console`` to ``System.Console`` in the rest of the code. The
program should still compile and run.


``using`` System.Collections.Generic
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

So far, the ``using System`` has allowed us to work with primitive data types, such as **ints** and **chars**, but also 
reference types like **strings**.  When we start using collection types, we are going to need a namespace update that will
provide the compiler with needed resources to work with these types.  

While working with the replit IDE, you will need to add this manually when you want to use a collection type.  

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      using System;
      using System.Collections.Generic;    //add this line

Gradebook, Three Ways
---------------------

We’ll explore collections in C# by looking at different versions of
the same program. The program functions as a gradebook, allowing a
user (a professor or teacher) to enter the class roster for a course,
along with each student’s grade. It then prints the class roster along
with the average grade. In each variation of this program, the grading
system could be anything numeric, such as a 0.0-4.0 point scale, or a
0-100 percentage scale.

A test run of the program might yield the following:

::

   Enter your students (or ENTER to finish):
   Chris
   Jesse
   Sally

   Grade for Chris: 3.0
   Grade for Jesse: 4.0
   Grade for Sally: 3.5

   Class roster:
   Chris (3.0)
   Jesse (4.0)
   Sally (3.5)

   Average grade: 3.5

We’ll look at the gradebook using a ``List`` first. 

