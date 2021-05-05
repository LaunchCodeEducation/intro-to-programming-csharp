.. _abs-examples:

``Abs()`` Examples
====================================

Returns the absolute value of a number.  Absolute values are always positive.

This method is avaiable to all numeric values.

**General syntax:**

::

   Math.Abs(number)


.. admonition:: Example

   .. sourcecode:: csharp

      double[] absPractice = {54.234, -9.32, -19, 45};

      foreach(double d in absPractice)
      {
         Console.WriteLine(Math.Abs(d));
      }

   **Console Output**

   ::

      54.234
      9.32
      19
      45
