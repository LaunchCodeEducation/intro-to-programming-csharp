.. _math-class:

The ``Math`` Class
===================

C# has a few built in classes that can be called directly by the user.  
Arrays, collections, strings are only a few.
One of these classes is the ``Math`` class, 
which contains more than just the standard mathematical operations(``+``, ``-``, ``*``, ``/``).

In the previous sections we learned how to construct, modify, and use classes to create objects.  
However built-in C# classes are not allowed to be modified.  
The fields and methods available are what you get.  

The ``Math`` class is ``static``; containing ``static`` methods and ``const`` fields.  

``Math`` Class is ``static``
----------------------------------

The ``Math`` methods are all static.  
We do not have to instantiate the ``Math`` class in order to use it. 
It is part of the ``using System`` that is commonly found in your C# IDEs, like the ``Console`` class.

When we want to use members of the ``Math`` class, we need to directly call the class then the member name.

.. sourcecode:: csharp

   Math.Round(3.293823, 2);


However, if we want to do something with the output of this ``Math.Round`` method, we will need to store it in a variable.
Being ``static``, it cannot create its own instance.

The ``Math`` class has built-in methods that you can call.  We will review a few in this chapter, but for a complete list 
you can read the `documentation <https://docs.microsoft.com/en-us/dotnet/api/system.math?view=net-5.0>`_ on the ``Math`` Class.


.. index:: ! Math methods

``Math`` Methods Are ``static``
----------------------------------

The ``Math`` Class contains several mathematical and trigonometric methods.  

.. list-table:: Math Methods in C#
   :header-rows: 1

   * - C# Syntax
     - Description
     - Example
   * - :ref:`Abs() <abs-examples>`
     - Returns the absolute value, or positive value, of a number.  Can be used with any numeric type.
     - ``Math.Abs(number)``
   * - :ref:`Ceiling() <ceiling-examples>`
     - Rounds the ``double`` or ``decimal`` value UP to the closest whole number.  
     - ``Math.Ceiling(number)`` 
   * - :ref:`Floor() <floor-examples>`
     - Rounds the ``double`` or ``decimal`` value DOWN to the closest whole number.  
     - ``Math.Floor(number)``
   * - :ref:`Max() <max-examples>`
     - Returns larger of 2 numeric types.
     - ``Math.Max(number1, number2)``   
   * - :ref:`Min() <min-examples>`
     - Returns smaller of 2 numeric types.
     - ``Math.Min(number1, number2)``  
   * - :ref:`Pow() <pow-examples>`
     - Returns specified number raised to specified power.  Takes ``double`` types.
     - ``Math.Pow(number, power)`` 
   * - :ref:`Round() <round-examples>`
     - Returns number rounded to nearest integral value OR specified number of decimal places
     - ``Math.Round(number)`` OR ``Math.Round(number, decimalPlaces)``  
   * - :ref:`Sqrt() <sqrt-examples>`
     - Returns the square root of specified number.  Takes ``double`` types.
     - ``Math.Sqrt(double)``    
   * - :ref:`Truncate() <truncate-examples>`
     - Removes any decimals and returns interger part of number.  Takes ``double`` or ``decimal`` types.
     - ``Math.Truncate(double)`` 



.. index:: ! const, ! constants ! PI ! pi ! Pi

.. _math-pi:

``Math`` Fields Are Constants
------------------------------

Having a built in ``Math`` class can be very helpful when it comes to common math elements, such as ``PI``.  

One of the benefits of constant values is that you don't have to memorize them, or define them in a variable.
C# stores the value of pi up to 16 decimal places for us.  
We just need to use dot notaion and we can access this class field.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(Math.PI);
      Console.WriteLine(Math.PI*4);
      Console.WriteLine(Math.PI + Math.PI);
   
   **Console Output**

   ::

      3.14159265358979
      12.5663706143592
      6.28318530717959

However, this value is a constant, or ``const``.  You are NOT able to alter it.  
``const`` values are fixed and unable to be updated or overwritten.  

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(Math.PI);

      double Math.PI = 1234.56;

      Console.WriteLine(Math.PI);

   **Console Output**

   ::

      3.1415926535897931
      error CS1525: Unexpected symbol `.', expecting `,', `;', or `='

The error message shows that the compiler was not expecting you to try and update ``Math.PI``.  
Again, users are not allowed to update the ``Math.PI`` field.

.. list-table:: Math Fields in C#
   :header-rows: 1

   * - C# Syntax
     - Description
     - Example
   * - ``Math.PI`` 
     - Ratio of circumference of a circle to its diameter.  
     - 3.1415926535897931



Check Your Understanding
---------------------------

.. admonition:: Question

   Which of the following returns ``-3`` when applied to ``-3.87``?

   #. Math.Floor(-3.87);
   #. Math.Abs(-3.87);
   #. Math.Round(-3.87);
   #. Math.Truncate(-3.87);

.. ans: Math.Truncate


