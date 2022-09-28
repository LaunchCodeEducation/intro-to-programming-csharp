Using Methods
================

Now that we see how to build a method, let's talk about using them.

``return`` vs. ``void`` Methods
---------------------------------

In the previous section, we looked at methods that return a value.  That value is then able to be used elsewhere in your program.  

Sometimes we might want to use our method to manipulate data for the console output only. 
This is when you may want to consider using a ``void`` return type.  

.. admonition:: Example

   .. replit:: csharp
      :linenos: 
      :slug: BirthdayNotes-CSharp

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
This might seem really simple, but if you had a list of names to run through, calling your method for each is a LOT less typing than 
a ``Console.WriteLine`` statement with your message for each one.  That would get old fast.  

If you notice, the method itself is creating the ``Console.WriteLine`` statement.  So when we call ``BirthdayNotes`` all we need to do is 
provide it with input.  We can directly place values of the corresponding data type directly in the parentheses of the method call, as we did in **Line 8**.
We can also pass variables into the parentheses, as we did in **Lines 10-12**.

This method used ``Console.WriteLine`` to print the message.  
We received no value from the method, making the return type **void**.  We are able to pass it values, but we are not expecting any in return.

When we pass values into the parameters, these values can be referred to as arguments.


Parameters and Arguments
-------------------------

Let's revisit the method signature template.

.. sourcecode:: bash

   Access Modifier [static modifier] Return Type MethodName(Parameter List)
   {
      Method Body
   }

Do you see ``"Parameter List"`` inside the parentheses following the ``MethodName``?
In the example above ``BirthdayNotes`` has three items inside the parentheses.  
These are the **parameters** the method is expecting.  Within a method, parameters are *placeholders* for the specific input required.
**Arguments** are the spcific input, or real values, you pass to the method upon invocation.   

In the ``BirthdayNotes`` example, the parameter list shows us that the method is expecting a string value and two int values in that order.  
For our human understanding we gave the parameters helpful names, but those names are NOT variables or values.  
They are holding space for your actual arguments.  The method will take your arguments and use them as designated by the parameters.

When we call the method, we can pass our arguments directly or via variables and check the output to see if we are happy with the results.

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
      

In the example we called BirthdayNotes twice.  
The first time, ``BirthdayNotes("Willow", 8, 3)`` and the second time ``BirthdayNotes("This is a string, too", -55, 987654321)``.  
The code ran both times because the data types of the arguments matched those of the parameters.  
The second call doesn't make any sense in the context of the method's overall job.  
However, since it was provided with arguments of the same data type as the parameters, the method ran as expected.  

Let's see this with a method that returns a value.

.. admonition:: Example

   .. replit:: csharp
      :linenos:
      :slug: StaticMethodExample01-CSharp
      
      using System;

      class MainClass {
      
         public static void Main (string[] args) {
               
            double purchase1 = 25.43;
            double total1 = purchase1 + SalesTax(purchase1);
            
            Console.WriteLine(total1);
         }

         static double SalesTax(double price)
         {
            double tax = price * 0.0423;
            return Math.Round(tax, 2);
         }

      }

   **Console Output**

   :: 
      
      26.51


In this example, we used a variable to hold our argument, then passed the argument to the method.  
Since this method returns an actual value, we can store it in a variable or use it as a value itself like we did in **Line 15**.

Also, inside this method we used the `Math Method <https://docs.microsoft.com/en-us/dotnet/api/system.math.round?view=net-5.0>`_ ``Round`` to round our output to 2 decimal places.  
Methods are able to use other methods.  

``Console.WriteLine`` was called to verify functionality.  
With return methods, you will need to print them in order to verify functionality.

Named and Optional Arguments
-------------------------------

Named Arguments
^^^^^^^^^^^^^^^^
As your code grows, you may find yourself questioning the order of parameters in a method you built somewhere in your program.
Despite not remembering the order, you remember exactly what each parameter is called.  You could pause and serach for your 
method to verify the order or you could use **named arguments**.  
Naming your arguments means that you provide the parameter name ``:`` then the argument.  
The order doesn't matter, as the compiler is clever enough to use the names to properly use the arguments in your method.

.. admonition:: Example

   .. replit:: csharp
      :linenos:
      :slug: NamedArguments-CSharp

      class MainClass {
      
         static void ResumeList(string jobTitle, string jobName, int numYears, string name)
         {
            Console.WriteLine(name + " worked at " + jobName + " as a(n) " + jobTitle + " for " + numYears + " years.");
         }
      

         public static void Main (string[] args) {
            
            ResumeList("Receptionist", "Tate & Bywater", 2, "Carolyn");

            //using Named Arguments
            ResumeList(name: "Beth", numYears: 3, jobName: "Hope Center", jobTitle: "RVT");
         }
      }

   **Console Output**

   :: 
      
      Carolyn worked at Tate & Bywater as a(n) Receptionist for 2 years.
      Beth worked at Hope Center as a(n) RVT for 3 years.



Optional Arguments
^^^^^^^^^^^^^^^^^^^^

An argument becomes optional when the parameter is coded to take a **default value**. 
This means that if you invoke the method and don't pass it a value, the parameter will use the default value instead.
This can be useful in testing methods.

To use an optional argument, you need to program your parameter to be optional.  Name your parameter, follow it with an ``=`` 
then the value, properly formated for its data type.  Optional parameters should be defined at the end of your parameter list.

.. admonition:: Example

   .. replit:: csharp
         :linenos:
         :slug: OptionalArguments-CSharp

         static void HelloYou(string name = "You")
         {
            Console.WriteLine("Hello, " + name);
         }
            
         public static void Main (string[] args) {

            HelloYou("Evelyn");
            HelloYou();
         
         }

   **Console Output**

   :: 
      
      Hello, Evelyn
      Hello, You



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

.. ans: T

.. admonition:: Question

   What is printed when the following program runs?

   .. sourcecode:: csharp
      :linenos:

      static void Greetings()
      {
         Console.WriteLine("Hello!");
      }
      
      public static void Main (string[] args) {
            
         Greetings();
         
         }


      

   

   #. Throws an error this is a void method, nothing should happen. Ever.
   #. ``Hello!``
   #. ``Greetings();``
   #. Throws an error because the user did not provide any values inside the parentheses at the time of calling.

.. ans: b.

.. admonition:: Question

   **True or False** A method can use other methods to create desired output.

   #. True
   #. False

.. ans: T

.. admonition:: Question

   In your own words, what are parameters and arguments?  Where and when do you use each?



   