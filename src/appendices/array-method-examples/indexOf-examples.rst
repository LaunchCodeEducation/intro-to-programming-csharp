.. _array-indexOf-examples:

``IndexOf`` Examples
=====================

The general syntax for this method is:

.. sourcecode:: csharp

   Array.IndexOf(arrayName, item)

This method returns the index of the FIRST occurence of an item in the array.
If the item is not in the array, -1 is returned.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      int[] charles = new int[] {1, 7, 5, 9, 5};
      string[] otherArray = {"hello", "world!"};

      Console.WriteLine(Array.IndexOf(charles, 5));
      Console.WriteLine(Array.IndexOf(otherArray, "hi"));

   **Output**

   ::

      2
      -1
