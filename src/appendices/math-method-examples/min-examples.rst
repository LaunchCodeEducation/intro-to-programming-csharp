.. _min-examples:

``Min()`` Examples
====================================

Compares two numeric values of the same type, and returns the SMALLER of the set.

**General Syntax**

.. sourcecode:: csharp

   Math.Min(number1, number2)


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      double test1 = 342.42; 
      double test2 = 9819;

      Console.WriteLine(Math.Min(test1, test2));

   **Console Output**

   ::

      342.42