Methods and ??
=================================

Before we leave the subject of methods, let's walk through a slightly more complicated method example that can be solved using methods two ways.

Let's say that you are working with arrays and you need to know the sum of each value within the array.  
In order to do this, you will need to iterate through each index of the array and acculumate a running total of the values.
Easy.

.. sourcecode:: csharp

   int total = 0;
   for(int i = 0; i < arr.Length; i++)
   {
      total = i++;
   }
   

Great, there is our loop.  However, you have 20 arrays to sum.  
You could write a loop for each array *or* you could put one loop into a method and call the method 20 times.


.. admonition:: Example

   .. replit:: csharp
      :linenos:
      :slug: StaticMethodExample01-CSharp
      
      using System;

      class MainClass {
      
      static int SumOfArray(int[] arr)
      {
         for(int i = 0; i < arr.Length; i++)
         {
            total = i++;
         }
         return total;
      }
      
      public static void Main (string[] args) {
            
         int[] numOfBooks = new int[] {45, 22, 55, 6, 77, 11};
         int[] numOfCats = new int[] {1,2,2}; 
         int[] numOfCalories = new int[] {345, 734, 232, 25};
         
         Console.WriteLine(SumOfArray(numOfBooks));
         Console.WriteLine(SumOfArray(numOfCats));
         Console.WriteLine(SumOfArray(numOfCalories));
         
         }
      }

   **Console Output**

   :: 
      
      216
      5
      1336

Using the method ``SumOfArray`` we were able to perform the simple action of adding all values in an array and printing out the total.
We used an ``int[] arr``, or integer array as a parameter.  As long as the arguments we passed to ``SumOfArray`` were of type ``int[]``
the method worked without any problems, dispite differences in length.

This one method saved you from writing the same loop over and over and over and over.

Methods can also hold conditionals as well.  They serve to help you simplify your code.  So if you are going to reuse a piece of code, 
be it a loop, conditional, or other method, consider using a method to help you keep your sanity and make your code more streamlined.

Special Usages
----------------

The methods we have discussed so far follow the standard method signature, and are able to work with other methods.  
However, there are two special usages we should mention before we move on.  
**Recursive methods** are methods that call themselves interally.  
**Anonymous methods**, often called **Anonymous functions** are methods that have no name, only a method body.

Recursion
^^^^^^^^^^

If methods can use methods, can a method use itself?  The answer is yes.  This process is called **recursion** and is 
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
Recursion can be faster, but that doesn't mean it is the most correct.  
If you ask developers in the real world, you will get a wide range of answers.  
Some use recursion all the time, while others only used it in school.  
Where you work, who you work with, and your own development style will provide you with a better answer for this.

Anonymous Methods
^^^^^^^^^^^^^^^^^^

As the name implies, these are unnamed functions.  
These functions are defined with the keyword ``delegate``, 
and can be assigned to variables of ``delegate`` type.  
The ``delegate`` types can pass methods as arguments 
to other methods, one example of this is seen with event handlers ications.

While this is a new data type, it works like all the other data types 
we've learned about so far.  It must match data types for it to work, 
regardless if working with a static or instance method.

Anonymous methods are instance methods.  
Creating instances is not something that we have talked about yet. 
So why do you need to learn these?  Well, you will run into them a LOT, 
especially as your code grows in complexity, such as web applications.

So while we're discussion methods, let's look at one.  Instances and instantiation will be covered
in more depth once we discuss classes and objects.  For the purpose of a quick walkthrough, we will gloss over 
terminology you will see soon.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      using System;

         class MainClass {
         
         delegate void MathOperations(double number1, double number2);
            
         public static void Main (string[] args) {

            MathOperations sum = delegate (double number1, double number2)
            {
                Console.WriteLine(number1 + " + " + number2 + " = " + (number1 + number2));
            };

            ArithmeticOperation divide = delegate (double number1, double number2)
            {
                Console.WriteLine(number1 + " / " + number2 + " = " + (number1/number2));
            };
			   
            sum(10, 5);
            divide(75, 3);

         }
      }

   **Console Output**

   ::

      10 + 5 = 15
      75 / 3 = 25

So what just happened here?  

In **Line 5** we declared the delegate method ``MathOperations`` and said it will take two parameters.

In **Line 9** we created an instance of that method and named it sum.  
(Think of is like making a variable, but with a method that we can call later).
Within ``sum`` we created a ``Console.WriteLine`` statement that will print with the arguments we pass to ``sum``.

For the purpose of demonstrating the reusability of methods, we created a new instance called ``divide`` in **Line14**.
It also has a ``Console.WriteLine`` statement that will print when called.

**Lines 19 and 20** we call the methods.  In this case, we refer to the names we gave each instance, and provided arguments.

Run your code and you will see the expression printed in the console.

In a small piece of code, it is hard to see why this would matter, but as your code grows 




MAYBE>>>>>>>   NOT SURE YET.....