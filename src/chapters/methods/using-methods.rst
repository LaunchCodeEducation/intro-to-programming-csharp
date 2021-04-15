Using Methods
================

Now that we see how to build a method, let's talk about using them.

``return`` vs. Void Methods
------------------------------

In the previous section, we looked at methods that return a value.  That value then able to be used elsewhere in your program.  

Sometimes we might want to use our method to manipulate data for the console output only. 
This is when you may want to consider using a ``void`` return type.  

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      static void BirthdayNotes(string name, int month, int day)
      {
         Console.WriteLine(name +"'s birthday is on " + month + "/" + day);
      }
      
      public static void Main (string[] args) {
            
            BirthdayNotes("Willow", 12, 12);

            string friend1 = "Lil";
            int friend1Month = 8;
            int friend1Day = 21; 
            
            BirthdayNotes(friend1, friend1Month, friend1Day);   
         }  
      }

   **Console Output**

   :: 
      
      Willow's birthday is on 12/12
      Lil's birthday is on 8/21
      

In this example, we are asking the method to print a friend's name and birth date inside a preprogrammed message.  
This might see really simple, but if you had a list of names to run through, calling your method for each is a LOT less typing than 
a ``Console.WriteLine`` statement with you message for each one.  That would get old fast.  

If you notice, the method itself is creating the ``Console.WriteLine`` statement.  So when we call ``BirthdayNotes`` all we need to do is 
provide it with input.  We can directly place values of the corresponding data type directly in the parentheses of the method call, as we did in **Line 8**.
We can also pass variables into the parentheses, as we did in **Lines 10-12**.

When we pass values into the parameters, these values can be referred to as arguments.


Parameters and Arguments
-------------------------

Let's revisit the method signature template.

.. sourcecode:: bash

   Access Specifier Return Type MethodName(Parameter List)
   {
      Method Body
   }

Inside the parentheses is ``Parameter List``.  In the example above ``BirthdayNotes`` has three items inside the parentheses.  
These are the parameters the method is expecting.  Parameters are *placeholders* for the method while you build it and are optional.  

In the ``BirthdayNotes`` example above, the parameter list shows us that the method is expecting a string value and two int values.  
For our human understanding we gave the parameters specific names, but those names are NOT variables or values.  
They are holding space for any values or variables you want to use the method on.  They are references for what data types are required and what to do with that data type.  
In the ``BirthdayNotes`` example, take the string value and two int values and insert it into a ``Console.WriteLine`` statement at specific locations for the message to make sense.

You build the method referring to the parameters.  In ``BirthdayNotes`` you see the same parameter names in the ``Console.WriteLine`` 
statement with string concatenation to create a message.  That is your value template.  When you call the method with **specific** values, 
the parameter placehoders will be replaced with your specific values, which in this example will print the message.  

The same is true in methods that return values.  

Those specific variables or values that you use when you call your method are **arguments**.  Let's see how arguments work in a method.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      static void BirthdayNotes(string name, int month, int day)
      {
         Console.WriteLine(name +"'s birthday is on " + month + "/" + day);
      }
      
      public static void Main (string[] args) {
            
            BirthdayNotes("Willow", 12, 12);
            BirthdayNotes("This is also a string", -55, 987654321);   
         }  
      }

   **Console Output**

   :: 
      
      Willow's birthday is on 12/12
      This is also a string's birthday is on -55/987654321
      

In the example we called BirthdayNotes twice.  The first time, ``BirthdayNotes("Willow", 8, 3)`` and the second time ``BirthdayNotes("This is a string, too", 3-5, 987654321)``.  
The code ran both times because the data types of the arguments matched those of the parameters.  The second call doesn't make any sense in the context
of the method's overall function.  However, since it was provided with arguments of the same data type as the parameters, the method ran as expected.  

Let's see this with a method that returns a value.

.. admonition:: Example

   .. replit:: csharp
      :linenos:
      :slug: StaticMethodExample01-CSharp
      
      using System;

      class MainClass {
      
      static double SalesTax(double price)
      {
         double tax = price * 0.0423;
         return Math.Round(tax, 2);
      }
      

         public static void Main (string[] args) {
            
         double purchase1 = 25.43;
         double total1 = purchase1 + SalesTax(purchase1);
         
         Console.WriteLine(total1);
         
         }
      }

   **Console Output**

   :: 
      
      26.51


In this example, we used a variable to hold our argument, then passed the argument to the method.  
We also used the method in a math expression in **Line 15**.  This is possible because this method returns a values.  
That value is like every other value you have worked with so far.  This method takes a double, but any double will do.  
The ``Math.Round`` method has been added to return a value with only two decimal places.  

When working with static methods, if you want to see your output, you will need to print the value.  You can call it directly in a 
``Console.WriteLine`` statement or create a variable to hold the call then print your variable.


Check Your Understanding
---------------------------

.. admonition:: Question

   **True or False** the following method will *not* return a value.

   .. sourcecode:: csharp
      :linenos:

      static void YourName(string name)
      {
         Console.WriteLine(name);
      }

   #. True
   #. False

.. admonition:: Question

   What is printed when the following program runs?

   .. sourcecode:: csharp
      :linenos:

      static void YourName(string name)
      {
         Console.WriteLine(name);
      }


      //The user enters ``YourName("Desi");`` in the Main method.

   

   #. Throws an error this is a void method, nothing should happen.
   #. ``Desi``
   #. ``MyName();``
   #. Throws and error because the user did not use a variable called ``name``.

.. admonition:: Question

   **True or False** A method can use other methods to create desired output.

   #. True
   #. False

.. admonition:: Question

   In your own words, what are parameters and arguments?  Where and when do you use each?



   