Scope 
==========

.. index:: ! scope

**Scope** refers to visibility of a particular variable within your code.  
So far we have defined variables directly in the Main method within the ``MainClass`` in the replit IDE, 
but also inside loops and methods.  Perhaps you have exerienced an error when trying to print or call a variable that 
was created inside your loop from outside of the loop.  This is an example of a scope issue.  

When we create code blocks or classes, we are creating boxes to hold pieces of code contained within ``{ }`` .  
Unless we provide a way to open the box, we can't access the code within.
Conditionals, loops and methods have their own designated code block space between their ``{ }``, 
and can be stored inside a class or inside methods, loops, and conditionals.  
Anything created within that code block will stay there unless returned or granted access.  
Classes are larger boxes that can hold multiple loops and methods and, depending on the access modifiers, are able to access 
all of them within it as well as items from other classes.  

When you run into a scope error, the compiler error messages use the word **context** instead of scope.  
When you see this message, you might need to backstep through your work and look at your boxes.  
*Did you provide a way to open the lid?  Did you mean to work within the loop or method?  
Did you really want* that *access modifier?  Did you accidently open the lid when it should stay closed?*
Scope can vary from too narrow, as in trying to access a variable created within a loop.  All the way to too broad, 
as in able to access data through the entire program.  Being able to access across the entire program could cause 
issues with security or accidental data manipulation.

In C#, scope is broken down into three categories: class level, method level, and block level.

Class Level Scope 
----------------------

Class level scope refers to the variable within a class, also known as **class members**.  While we have only experience with the ``MainClass`` in the replit IDE
so far, you have seen this in action.  In the ``MainClass`` you are able to access any methods that are inside the class, but not contained inside any 
other methods or code blocks.  Once we begin to add *more* classes to our code, this can become an issue. 
When we get to classes, we will discuss how to handle class level scope in more detail. (Hint: think access modifiers).

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      class MainClass {

         static int SumItUp(int num1, int num2, int num3)
         {
            int sum = num1+ num2+ num3;
            return sum;
         }

         public static void Main (string[] args) {

            int total = SumItUp(1,2,3);
            Console.WriteLine(total);

            Console.WriteLine(sum)
         }
      }
   
   **Console Output**

   ::

      6

      error CS0103: The name `sum' does not exist in the current context

In this example we are trying to print the variable ``total``.  
We can access ``total`` because it has been defined within ``MainClass``, as you can see in **Line 1** in this example.

While ``sum`` is created in the ``MainClass``, we are not able to access it because it is contained within a method.  

As our classes expand, our ability to access variables between classes will depend upon depend upon their location within the class.  
If they are contained within methods, as ``sum`` was in the example above, we will not be able to acces them at all.  
If they are class members, it will depend on their access modifiers if we can reach them or not.  We will learn more about this soon.


Method Level Scope 
------------------------

With method level scope, any variables declared *within* a method are not avaliable outside the method.
They are avaliable to any nested code blocks within the method.  
These are commonly referred to as **local variables** as they are confined to one location, the method they were declared in.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      class MainClass 
      {

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


We defined ``total`` *inside* the method.  
When we call for the ``total`` with a ``Console.WriteLine`` statement, the compiler cannot find it.
It only exisits inside that method.  

Block Level Scope
-----------------------

This is very similar to method level scope,
except block level scope can happen within a method depending on where you declare it.  
Any signature that contains a code block can have scope issues here, such as loops or conditionals.


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      class MainClass 
      {

         static void PrintThis()
         {
            int i = 0;
            for(i = 0; i < 3; i++)
            {
               Console.WriteLine(i);
            }
         }

         public static void Main (string[] args) 
         {

            for(int j = 10; j < 20; j = j +3)
            {
               Console.WriteLine(j);
            }

            PrintThis();
            Console.WriteLine(j);
         }
      }
   
There are 3 examples of block scope in this example.

Starting with **Line 9**, we print the value of ``i`` from inside the ``PrintThis`` method.  
When this runs, you will see ``0,1,2`` print on new lines after calling the method in **Line 21**.
It works because **Line 9** is able to see the values of ``i`` via the ``for`` loop code block.

Moving down to **Line 16**, we see another ``for`` loop.  This loop will print each value of ``j`` from within its codeblock as is. 
There are no scope issues here.  Run the code and you will see ``10, 13, 16, 19`` print to the console on new lines.

**Line 22** is where we find a scope issue.  We want to know what ``j`` is *outside* the ``for`` loop.
However, ``j`` doesn't exist outside of the context of the ``for`` loop block, so the ``Console.WriteLine`` statement in **Line 22**
won't be able to find any values and will throw an error.  In fact, the compiler won't run ANY of your code until you fix **Line 22**.

Check Your Understanding
-------------------------

.. admonition:: Question

   Identify the level of scope for ``int byHalf``.

   .. sourcecode:: csharp
      :linenos:

      static int MathIsFun(int number)
      {
         if(number % 2 == 0)
         {
            int byHundred = number * 100;    
            Console.WriteLine(byHundred);
         }
         int byHalf = number/2;              
         return byHalf;
      }

      Console.WriteLine(byHalf);


   #. Class scope
   #. Method scope
   #. Block scope

.. ans: Method scope
