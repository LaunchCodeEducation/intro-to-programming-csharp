.. _type-conversion:

=================
Type Conversion
=================

.. index:: ! Number(), ! String(), returns

.. index::
   pair: type; conversion

Sometimes it is necessary to convert values from one type to another. 
A common example is when a program receives input from a user or a file. 
In this situation, numeric data may be passed to the program as strings and your code is looking for a double data type, not string.

C# provides a few simple methods that will allow us to convert values to different data types. The methods ``Int32.Parse`` and ``Double.Parse`` will (attempt to) convert their arguments into types ``int`` and ``double``, respectively. 
We call these **type conversion** functions.

The ``Int32.Parse`` method can take a string and convert it into an integer whilte ``Double.Parse`` converts strings into a double. Let's see this in action:

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(Int32.Parse("2345"));
      Console.WriteLine((Int32.Parse("2345")).GetType());
      Console.WriteLine(Double.Parse("17"));
      Console.WriteLine((Double.Parse("17.8")).GetType());

   **Console Output**

   :: 

      2345
      System.Int32
      17
      System.Double



What happens if we attempt to convert a string to a number, and the string doesn't directly represent a number?

.. admonition:: Example

   .. sourcecode:: csharp

      Console.WriteLine(Int32.Parse("23bottles"));

   **Console Output**

   ::

     Unhandled Exception: System.FormatException: Input string was not in a correct format.

This example shows that a string has to be a syntactically legal number for conversion to go as expected. 
Examples of such strings are ``"34"`` or ``"-2.5"``. If the value cannot be cleanly converted to a number then an error will be returned.

Converting other data types into strings is more complex than a simple parse.  We will return back to this concept once we learn more about strings.



Check Your Understanding
------------------------

.. admonition:: Question

   Which of the following will result in ``Double.System`` when passed to ``GetType``? 

   #. ``'3'``
   #. ``'three'``
   #. ``3.3333``
   #. ``33``
