.. _debugging-logic-errors:

========================
Debugging Logic Errors
========================

We can debug runtime and syntax errors using the error messages produced.  
Logic errors, however, do not always produce error messages. This sometimes makes them tougher to debug.

While we can't provide a step-by-step approach that applies to every possible logic error, 
we *can* give you some solid strategies. Two such strategies---using debugger tools and writing tests---will 
be covered in future lessons. In this section, we start with a basic and effective way to debug logic errors.

Printing Values
---------------
This example will work with logic and runtime errors.  These are commonly seen in the C# environment.

When your code runs but doesn't produce the expected results, it is important to check the values of the 
variables being used.

Let's look at a program that has a logical bug.  

This program is designed to take ask the user for the temperature in Celsius and then convert it into Kelvin.  

Before we get into the code let's think about all the parts: Get a number from the user then use it in a math equation.

Okay, let's get building:

.. replit:: csharp
   :linenos:
   :slug: Degrees-C-to-K-Logic-Error-CSharp
   
   Console.WriteLine("Temp in degrees C:");    
   string degreesC = Console.ReadLine();             
   Console.WriteLine("Degrees K: " + degreesC + 273.15); 

  

This program asks the user for a temperature in degrees Celsius and attempts to convert it to degrees Kelvin. 
Degrees Kelvin differs from degrees Celsius by 273.15. So if we enter 100 (in Celsius) we should see a converted value of 373.15 (in Kelvin). 
However, running the program as-is and entering 100 gives the message:

::

   Temp in degrees C: 100
   Degrees K: 100273.15
   
This is clearly incorrect. But the program does not generate an error, so it is not immediately clear what the issue is. 
To figure it out, we'll use ``Console.WriteLine`` to see what the values of key variables are when the program runs. 

Looks like our variables were pushed together, or concatenated, instead of added.  Let's look at our data types and see if that can give us any insight.
We declared ``degreesC`` to be a string, but what about the number ``273.15``?  We can add a ``Console.WriteLine`` statement to check the data type.

.. sourcecode:: csharp
   :linenos:

   Console.WriteLine("Temp in degrees C:");    
   string degreesC = Console.ReadLine();             
   Console.WriteLine(273.15.GetType());
   Console.WriteLine("Degrees K: " + degreesC + 273.15); 


Running this with an input of 100 gives the output:

::

   Temp in degrees C:  100
   System.Double
   Degrees K: 100273.15

The value of ``273.15`` in **Line 3** is a double, but ``degreesC`` is initialized as a string.   We can join them with the ``+``, 
but final answer is still incorrect, so we need to keep digging for more information.

Looking at **Line 4** in which we try to add ``273.15`` to ``degreesC``.  All we are doing is concatenating the two togehter. 
In the last chapter we learned how to convert data types using the ``Double.Parse`` method.  Let's see what happens if we use that?

Currently the data type of ``degreesC`` is a string.  Let's create a new variable and use the ``Double.Parse`` method to convert the 
string into a double.  Let's also run a ``Console.WriteLine`` statement to check the data type after our ``Double.Parse``.


.. sourcecode:: csharp
   :linenos:

   Console.WriteLine("Temp in degrees C:");    
   string degreesC = Console.ReadLine();             
   double degreesCDouble = Double.Parse(degreesC);        
   Console.WriteLine(degreesCDouble.GetType() + "  --- testing degreesCDouble");
   Console.WriteLine(273.15.GetType() + " --- testing 273.15");
   Console.WriteLine("Degrees K: " + degreesC + 273.15);


Running this with an input of 100 gives the output:

::

   Temp in degrees C:  100
   System.Double --- testing degreesCDouble
   System.Double --- testing 273.15
   Degrees K: 100273.15

That's it! The variable ``degreesCDouble`` has the value ``100``, and is of data type double. However, ``degreesC`` is still a string.

.. admonition:: Note

   What are those extra strings in **Lines 4 and 5**?  It's a **tag**.  Adding tags to your ``Console.WriteLine`` statements can also help debug your code.
   It is basic string concatenation, but can provide valuable information.   We checked the data 
   types of multiple variables.  Tags remind you which variable is which or what you are expecting
   can help you stay organized as you debug and build.   


We can fix our program by using our new variable, ``degreesCDouble``.

.. sourcecode:: csharp
   :linenos:

   Console.WriteLine("Temp in degrees C:");    
   string degreesC = Console.ReadLine();             
   double degreesCDouble = Double.Parse(degreesC);          
   Console.WriteLine("Degrees K: " + degreesCDouble + 273.15);

Running this with an input of 100 gives the output:

::

   Temp in degrees C:  100
   Degrees K: 100273.15

Wait what?  This is another sneaky logic error.  In **Line 4**, we are performing concatenation with our new variable, rather than printing any results.  
If we want to print the results of the calculation, we should make a variable to *become* the results of our calculations

.. sourcecode:: csharp
   :linenos:

   Console.WriteLine("Temp in degrees C:");    
   string degreesC = Console.ReadLine();             
   double degreesCDouble = Double.Parse(degreesC);  
   double degreesK = degreesCDouble + 273.15;        
   Console.WriteLine("Degrees K: " + degreesK);

Running this with an input of 100 gives the output:

::

   Temp in degrees C: 100
   Degrees K: 373.15
  
It worked!  Finally, right?  We can take in user input? Check.  
We can use that input in a mathematical formula? 
We can now thanks to some conversions and additional variables. Great job!

Note that after debugging we removed all of our testing ``Console.WriteLine`` statements. Be sure to do the same when using this debugging technique.




