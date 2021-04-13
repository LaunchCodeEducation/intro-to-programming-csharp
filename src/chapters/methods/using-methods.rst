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

      static void BirthdayMessage(string name)
      {
         Console.WriteLine("Happy Birthday, " + name + "!");
      }
      public static void Main (string[] args) {
            
            string friend1 = "Lil";
            BirthdayMessage(friend1);
            BirthdayNotes("Willow");
         }
      }

   **Console Output**

   :: 
      
      Happy Birthday, Lil!
      Happy Birthday, Willow!

In this example, we are asking the method to print a friend's name  and birthday message inside a preprogrammed message.  
This might see really simple, but if you had a list of names to run through, calling your method for each is a LOT less typing than 
a ``Console.WriteLine`` statement with you message for each one.  That would get old fast.  

If you notice, the method itself is creating the ``Console.WriteLine`` statement.  So when we call ``BirthdayMessage`` all we need to do is 
provide it with input.  The input could be in the form of a variable, as in **Line 8**, or directly as in **Line 9**.  



Parameters and Arguments
-------------------------

Let's revisit the method signature template.

.. sourcecode:: bash

   Access Specifier Return Type MethodName(Parameter List)
   {
      Method Body
   }


************************************************

Inside the parentheses is ``Parameter List``.  In the example above ``BirthdayNotes`` has three items inside the parentheses.  
These are the parameters the method is expecting.  Parameters are placeholders for the method while you build it.  

In the BirthdayNotes example above, the parameter list shows us that the method is expecting a string value and two int values.  
For our human understanding we gave the parameters specific names, but those names are NOT variables or values.  
They are holding space for any values or variables you want to use the method on.  They tell the method to expect a string variable or value
and do the following with it.  In the ``BirthdayNotes`` example, take the string variable and insert it into a ``Console.WriteLine`` statement.

Those specific variables or values that you use when you call your method are called **arguments**.  Let's see how arguments work in a method.

.. admonition:: Example

   .. replit:: bash
      :linenos:
      :slug: MethodBuildingAndCalling-CSharp
      
      using System;

      class MainClass {
      
      static void BirthdayNotes(string name, int month, int date)
      {
         Console.WriteLine($"{name}'s birthday is {month}/{date}.  Happy Birthday!");
      }
      

         public static void Main (string[] args) {
            
            BirthdayNotes("Willow", 8, 3);
            BirthdayNotes("This is a string, too", 3455, -987);
         
         }
      }

   **Console Output**

   :: 
      
      Willow's birthday is 8/3. Happy Birthday!
      This is a string, too's birthday is 3455/-987.  Happy Birthday! 
      

In the example we called BirthdayNotes twice.  The first time, ``BirthdayNotes("Willow", 8, 3);`` and the second time ``BirthdayNotes("This is a string, too", 3455, -987);``.  
The code ran both times because the data types of the arguments matched those of the parameters.  The second call doesn't make any sense in the context
of the method's overal function.  However, since it was provided with arguments of the same data type as the parameters, the method doesn't care.  

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


Special Usages
----------------

This is not the only way to use methods.  **Anon** and **Recursion**

keep these simple


Check Your Understanding

T/F:  You can not use other methods inside your method //F
T/F:  Parameters are placeholders for specific arguments //T
T/F:  
