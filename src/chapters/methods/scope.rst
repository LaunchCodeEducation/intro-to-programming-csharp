Scope 
==========

**Scope** refers to visibility of a particular variable within your code.  
So far we have defined variables directly in the Main method within the MainClass in replit, 
but also inside loops and methods.  

In C#, scope is broken down into three categories: class level, method level, and block level.

Class Level Scope 101
----------------------

Class level scope you are already familiar with, but once we begin to add *more* classes to our code, this can become an issue. 
When we get to classes, we will discuss how to handle class level scope in more detail. (Hint: think access modifiers).

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      class MainClass {

         static int SumItUp(int num1, int num2, int num3)
         {
            return num1+ num2+ num3;
         }

         public static void Main (string[] args) {

            int total = SumItUp(1,2,3);
            Console.WriteLine(total);
         }
      }
   
   **Console Output**

   ::

      6

In this example we are trying to print the variable ``total``.  
We can access ``total`` because it has been defined within ``MainClass``.

Method Level Scope 101
------------------------

With method level scope, any variables declared **within** a method are not avaliable outside the method.
They are avaliable to any nested code blocks within the method.  
These are commonly referred to as **local variables** as they are confined to one location, the method they were declared in.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      class MainClass {

         static int SumItUp(int num1, int num2, int num3)
         {
            int total = 7 + 8 + 9;
            return total;
         }

         public static void Main (string[] args) {

            Console.WriteLine(total);
         }
      }
      
   **Console Output**

   :: 

      main.cs(11,31): error CS0103: The name `total' does not exist in the current context


We defined ``total`` **inside** the method.  
When we call for the ``total`` with a ``Console.WriteLine`` statement, the compiler cannot find it.
It's contained inside the method, locked away.  

Block Level Scope 101
-----------------------

This is very similar to method level scope,
except block level scope can happen within a method depending on where you declare it.


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      class MainClass {

         static void PrintThis()
         {
            int i = 0;
            for(i = 0; i < 3; i++)
            {
               Console.WriteLine(i);
            }
         }

         public static void Main (string[] args) {

            for(int j = 0; j < 3; j++)
            {
               Console.WriteLine(j);
            }

            PrintThis();
            Console.WriteLine(j);

         }
      }
   
There are 3 examples of block scope in this example.

Starting with **Line 8**, we print the value of ``i`` from inside the ``PrintThis``method.  
When this runs, you will see ``0,1,2`` print on new lines after calling the method in **Line 16**.
It works because **Line 8** is able to see the values of ``i`` via the ``for`` loop code block.

Moving down to **Line 14**, we see another ``for`` loop.  This loop is already in the Main method 
which means that **Line 14** will print each iteration on a new line without any problems.  
Again, the ``Console.WriteLine`` statement is contained within the code block for that loop.

**Line 20** is where we find a scope issue.  We want to know what ``j`` is **outside** the ``for`` loop.
However, ``j`` doesn't exist outside of the context of the ``for`` loop, so the ``Console.WriteLine`` statement in **Line 20**
won't be able to find any values and will throw an error.  In fact, the compiler won't run ANY of your code until you fix **Line 20**.

Check Your Understanding
-------------------------

- what type of scope is the desginated line invoking?
- 3 answers

