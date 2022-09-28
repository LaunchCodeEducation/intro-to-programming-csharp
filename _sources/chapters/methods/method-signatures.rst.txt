
Method Signatures and Calls 
==============================

.. index:: ! method signature, ! method call, ! method invocation


Method Signatures
-----------------------

When you decide to create your own method, there is a standard syntax that C# requires in order to 
run your method when you call it.  This syntax is the template for your method signature. 

.. sourcecode:: bash

   Access Modifier [static modifier] Return Type MethodName(Parameter List)
   {
      Method Body
   }

- **Access Modifier:**  This determines visibilty of methods between classes, and whether or not it can instanciate **new** objects.  Since our methods in this chapter are limited to the ``MainClass`` we will leave them off.
- **Static Modifier:**  *If* your method is static, you must include this between your access modifier and return type.  *Else* this is ommitted. 
- **Return Type:**  If the method is returning a value, this indicates what data type it will be.  Not all methods return values.  Methods that do not return a value have a return type of **void**.  
- **Method Name:**  The method's unique identifier.  This is what you use to call your method. 
- **Parameter List:** A parameter is a placeholder for specific data that the method will act upon.  Paraemeters are optional.  In these cases the ``()`` are still part of the method call, but remain empty.
- **Method Body:**  This is where you code your method.  Note it is contained between ``{}``.


Creating a Method
-------------------

Using our template, let's build a simple method.

.. admonition:: Example

   .. sourcecode:: csharp

      static int SquareTheNumber(int num)
      {
         return num * num;
      }


In this example, we are skipping the **access modifier**.  
The reason for this is that we are working within a single class.  
If we had multiple classes this would be more significant.  We will discuss this more when we get to class and class members.

We are using the ``static`` modifier.   This lets C# know that this method
belongs to the current class it is contained in and not to expect anything **new** to be created.  

Our **return type** is **int**.  This lets you know how to use the method.  
If you were expecting a **double** then you will need to modify your return type.  

``SquareTheNumber`` is the **method name**.  
Notice that it is all in `PascalCase <https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/capitalization-conventions>`_ where all words are capitalized and spaces removed.

``SquareTheNumber`` has a single **parameter**, ``int num``, which is a placeholder that tells you what **input** is expected along with the data type.  
In this example, ``SquareTheNumber`` is expecting one input of type **int**.  The input is labeled ``num`` to provide you more *context* on what to expect or how to use the method.  

When writing your own methods, provide as many clues as possible to help with readability.  
The **method body** shows you how the input will be manipulated within the method.  
Here it will be used to square itself.  This method will ``return`` a value which we can use elsewhere in our code.  Since this method is static, 
we can treat anything returned as a regular value.  This means you can store the method as a variable, pass the method into expressions or other methods, or print it. 

To sum up the method ``SquareTheNumber``:  use with an **int** value and the method will return the squared value.

Method Calls
^^^^^^^^^^^^^

A few notes about the Main method before we move on.  The Main method is where you **call** methods.  You build methods **outside** of the Main method.   

Let's walk through an example about placement for building your method and calling your method with the ``SquareTheNumber`` method.

.. admonition:: Example

   .. replit:: csharp
      :linenos:
      :slug: MethodBuildingAndCalling-CSharp
      
      using System;

      class MainClass {
      
         static int SquareTheNumber(int num)
         {
            return num * num;
         }

         public static void Main (string[] args) {
            
            int digit = 4;
            int squaredNum = SquareTheNumber(digit);
            int squaredAndSummed = squaredNum + SquareTheNumber(digit);

            Console.WriteLine(squaredNum);
            Console.WriteLine(squaredAndSummed);
            Console.WriteLine(SquareTheNumber(5));
         
         }
      }

   **Console Output**

   .. sourcecode:: bash

      16
      32
      25


You should be fairly familiar with the replit IDE by now.  

- **Line 1** is where the ``using`` statement goes.  
- **Line3** introduces the ``MainClass``.  The ``MainClass`` starts at **Line 3** and ends at **Line 21**  
- Starting at **Line 11** is the ``Main`` method statement.   The ``Main`` method is contained between **Lines 11-20** within the ``MainClass``.  

The purpose of the ``Main`` method is to exectue your program.  This is where you *call* or *invoke* the methods you create.
You cannot build your methods inside the ``Main`` method.  
They must be built outside the ``Main`` method but inside your ``MainClass``. 

In this example, we placed our ``SquareTheNumber`` method between **Lines 5-8**.  This makes it inside the ``MainClass`` but outside the ``Main`` method.


Invoking the Method
--------------------

We are using static methods with expected returns, these take input and return output, or values.  
So we must provide them with input if we want to see them work.  
Since this method is returning a numeric value, it needs to be stored somewhere.  
You can create a variable to do so, as we did in **Line 13** with the variable ``squaredNum``.  

.. sourcecode:: csharp
   :lineno-start: 12

   int digit = 4;
   int squaredNum = SquareTheNumber(digit);

   Console.WriteLine(squaredNum);

**Output**

.. sourcecode:: bash

   16

If you notice in **Line 13** we also invoked the method with the input variable ``digit`` from **Line 12**. 
When we print ``squaredNum`` we see the result ``16``, as expected since 4 * 4 is 16.  

Another way to take advantage of the returned value in this static method is to use the method call as part of an expression.  This is what
we did in **Line 14**.  

.. sourcecode:: csharp
   :lineno-start: 12

   int digit = 4;
   int squaredNum = SquareTheNumber(digit);
   int squaredAndSummed = squaredNum + SquareTheNumber(digit);

   Console.WriteLine(squaredAndSummed);

**Output**

.. sourcecode:: bash

   32


And the last example in **Line 18** is to use an *integer literal* or place the required data type value in the parentheses.  
In this example, we called ``SquareTheNumber`` and passed ``5`` directly in the parentheses.  When we printed the results, we got ``25``, as expected.


.. sourcecode:: csharp
   :lineno-start: 18

   Console.WriteLine(squaredNum(5));

**Output**

.. sourcecode:: bash

   25


These are three ways to invoke, or call, static methods that have a return type.  
Return types are not required.  Methods that return nothing are called **void** methods.
When working with void methods, the call is a slightly different.  We will look at them next.

**Method invocation** or **invoking the method** are synonmous terms for **calling the method**.


Check Your Understanding
------------------------
.. admonition:: Question

   What is the expected output returned by the ``Doubles`` method if the input, ``x``, was 7?

   .. sourcecode:: csharp
      :linenos:
         
      static int Doubles(int x)
      {
         return (2 * x);
      }


   #.  14
   #.  49
   #.  77
   #.  7

   .. ans: 14
