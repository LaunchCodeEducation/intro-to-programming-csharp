
========================
Errors and User Input
========================

In our last example, we asked the user to provide us with a temperature value in Celsius.
As programmers, we all hope that our message ``"Temp in degrees C:"`` would be clear enough
to have the user enter a numeric value.  However, things happen.

Have you tried your code with a non-numeric ``"Temp in degrees C:"`` value?  

Let's look at what happens if a user were to enter non-numeric data.  This is where we left
our program at the end of the last section.

.. sourcecode:: csharp
   :linenos:

   Console.WriteLine("Temp in degrees C:");    
   string degreesC = Console.ReadLine();             
   double degreesCDouble = Double.Parse(degreesC);  
   double degreesK = degreesCDouble + 273.15;        
   Console.WriteLine("Degrees K: " + degreesK);

Running this with an input of the string ``"one hundred"`` gives the output:

::

   Unhandled Exception:
      System.FormatException: Input string was not in a correct format.


In **Line 3**, we are converting our user input into a double data type.  
A double data type can only be numbers, whole or decimals.  
Anything else is unexpected and will cause your code to stop working.  
That type of message does not provide any feedback to your user for a second attempt. 

Is there anything you can do about this?  Yes.

``TryParse``
-------------

The ``TryParse`` method can be used here to handle this type of exception. 

``TryParse`` uses booleans and conditionals to verify that the correct input data type has been entered, and then allows 
you to create options based on the data.  This can be a helpful way to prompt the user for the desired data type.


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine("Temp in degrees C:");
      string degreesC = Console.ReadLine();
      double degreesCDouble;

      if (Double.TryParse(degreesC, out degreesCDouble)) 
      {
         double degreesK = degreesCDouble + 273.15;  
         Console.WriteLine("Degrees K: " + degreesK);
      }  
      else 
      {
         Console.WriteLine("Please enter a numeric value.");
      }


Running this with an input of the word ``"one hundred"`` gives the output:

::

   Please enter a numeric value.

If the in input was ``"100"`` then the output would be:

::

   Degress K: 373.15

``TryParse`` and ``out``
^^^^^^^^^^^^^^^^^^^^^^^^^

``TryParse`` method uses the keyword ``out``.  
In this instance, ``out`` reassigns our string value for a *valid* numeric value, which will be stored in the ``degreesCDouble`` variable in **Line 3**.

Let's see how ``TryParse`` and ``out`` work.

- **Line 1**, we print the prompt asking the user to provide a temperature reading.
- **Line 2**, ``degreesC`` is initialized once the user puts in their value.
- **Line 3**, ``degreesCDouble`` is declared, but not initialized.
- **Line 5**, we take ``degreesC`` and attempt to parse it into a double.  

If this is **true**, then a lot of things happen.

- First, since the input is a valid double, ``TryParse`` will assign the parsed value to ``degreesCDouble`` via the ``out`` keyword, thereby initializing it.
- Second, the ``degreesCDouble`` variable is initialized.
- Third, ``degreesCDouble`` is used in **Line 7** to initialize ``degreesK``.
- Finally, **Line 8** prints our results.


If **Line 5** is **false**, then ``TryParse`` is *not* able to assign any values.  
When this happens the ``else`` clause is triggered, and **Line 12** prints.  

This may seem like a lot of "extra" code, but one benefit of ``TryParse`` is that you can provide specific feedback for your user. 
Another benefit of ``TryParse`` is that it doesn't immediately shut down your program if the user input is non-numeric.  

``TryParse`` in this example is used with a **double**, but can be used for all of the primitive data types, including **ints**.  
Here's a short `practice repl.it <https://repl.it/@launchcode/TryParse-Int-CSharp#main.cs>`__ using ``TryParse`` and **ints**.  