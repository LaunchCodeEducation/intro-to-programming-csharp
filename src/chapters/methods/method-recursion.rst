Recursive Methods
=================================

.. index:: ! recursion 

If methods can use methods, can a method use itself?  

The answer is yes.  This process is called **recursion** and is 
when a method compares itself in its current state to a **base case** to determine if it should run again or terminate.  

The base case is a specific condition that once reached returns a final or **base value**.  
Every time the method is called, it compares the current input to the base case.  
If the base case is not met, the method will run once more.   
If the base case is met, the base value will be returned and the method will stop calling itself.  

Just like with loops, you have to check your logic with a recursive method, else you will have an endless recursion.


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      using System;

         class MainClass {
         
            static double FactorialRecursive(double number)
            {
               if(number == 0)
               {
                  return 1;   
               }
               return number * FactorialRecursive(number-1);
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


Here is an example of a recursive method.  In **Lines 5-12** we create the function.  
The base case is the ``if`` statement in **Line 7** which says that when the argument reaches ``0``, the method will return ``1`` and stop.
But if the arguement is not ``0``, we leave the ``if`` statment and go to **Line 11** which uses the method to call itself once more, with modified parameters.
The method will continue to call itself until the base case is met.

We could do the same thing with a loop as well.

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

Both methods complete the same task, but is one better than the other?  
If you ask developers in the real world, you will get a wide range of answers.  
Some use recursion all the time, while others only used it in school.  
Where you work, who you work with, and your own development style will provide you with a better answer for this.

Check Your Understanding
--------------------------
.. admonition:: Question

   In your own words, what is recursion?  