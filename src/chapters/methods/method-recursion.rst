Recursive Methods
=================================

.. index:: ! recursion 

If methods can use methods, can a method use itself?  

The answer is yes.  This process is called **recursion**. 
Recursion is when a method compares itself in its current state to a **base case** to determine if it should run again or terminate.  

The base case is a specific condition that once reached returns a final or **base value**.  
Every time the method is called, it compares the current input to the base case.  
If the base case is not met, the method will run once more.   
If the base case is met, the base value will be returned and the method will stop calling itself.  

Just like with loops, you have to check your logic with a recursive method, else you will have an endless recursion.

``FactorialRecursive`` A Recursive Example
------------------------------------------------


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      using System;

         class MainClass {
         
         static double FactorialRecursive(double number)
         {
            if(number == 0)  //base case
            {
               return 1;   
            }
            return number * FactorialRecursive(number-1);  //calling function again.  Notice updated parameters
         }
         
         public static void Main (string[] args) {

            double testNumber = 7;

            double factorialTest = FactorialRecursive(testNumber);

            Console.WriteLine(factorialTest + " is the factorial outcome of " + testNumber);
         }
      }

   **Console Output**

   ::

      5040 is the factorial outcome of 7


Here is an example of a recursive method.  
**Lines 5-8** contain the method ``FactorialRecursive``. 
**Line 7** is the base case.  Whether or not the method will terminate or invoke itself again is determined by the base case.  

.. sourcecode:: csharp
   :lineno-start: 7

   if(number == 0)  //base case
   {
      return 1;   
   }
   
If the number is ``0`` then the methods will return ``1`` and not call itself.  When this line is true, the recursion will stop.  
If the number is NOT ``0`` then **Line 11** will execute.
   
   
.. sourcecode:: csharp
   :lineno-start: 11
       
   return number * FactorialRecursive(number-1);  

   
**Line 11** returns the ``number`` times the method once again.  
However, notice that the parameters have been updated with this repeated call.  If we never updated the parameters, this would never terminate. 
We would have created an infinite recursion.  

Luckily, we updated the parameter in a way that the base case will eventually be met and the method call will stop.  
In a way this is similar to how loops work.

In fact, we could do the same thing with a loop as well.

``FactorialLoop`` A Loop Example
---------------------------------

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      using System;

         class MainClass {
         
         static double FactorialLoop(double number)
         {               
            double factorial = 1;

            for(double i = number; i >= 1; i--)
            {
               factorial = factorial * i;
            }

            return factorial;
         }
            
         public static void Main (string[] args) {

            double testNumber = 7;

            double factorialTest = FactorialLoop(testNumber);

            Console.WriteLine(factorialTest + " is the factorial outcome of " + testNumber);
         }
      }

   **Console Output**

   ::

      5040 is the factorial outcome of 7


This method, ``FactorialLoop`` does the same thing as the ``FactorialRecursive`` method only using a loop rather than recursion.    
The loop sets the index ``i`` at the value of parameter, if ``i`` is greater or equal to 1, then decrease ``i`` by 1 value.
Each iteration updates the variable ``factorial`` in **Line 15** and returns the final version once the loop has reached 0.


Recursion or Loops?
--------------------

Both methods complete the same task, but is one better than the other?  
If you ask developers in the real world, you will get a wide range of answers.  
Some use recursion all the time, while others only used it in school.  
Where you work, who you work with, and your own development style will provide you with a better answer for this.

Check Your Understanding
--------------------------
.. admonition:: Question

   In your own words, what is recursion?  