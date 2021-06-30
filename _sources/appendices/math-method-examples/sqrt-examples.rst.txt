.. _sqrt-examples:

``Sqrt()`` Examples
====================================

Returns the square root of a given positive ``double``.

Returns ``NaN`` value if used with negative number.
``NaN`` is a field in the ``Double`` class.

``NaN`` stands for "Not a Number" and in this case, 
the `square root of a negative number <https://en.wikipedia.org/wiki/Square_root#Square_roots_of_negative_and_complex_numbers>`_ does not exist.  
It is imaginary, or not a number.

You can read more about ``NaN`` in the `Microsoft documentation <https://docs.microsoft.com/en-us/dotnet/api/system.double.nan?view=net-5.0>`_.
And the square root method `here <https://docs.microsoft.com/en-us/dotnet/api/system.math.sqrt?view=net-5.0>`_.  


**General Syntax**

.. sourcecode:: csharp

   Math.Sqrt(doubleNumber);


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(Math.Sqrt(9));
      Console.WriteLine(Math.Sqrt(-9));
    

   **Console Output**

   ::

      3
      NaN


