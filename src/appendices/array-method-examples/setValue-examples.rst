.. _setValue-examples:

``SetValue`` Examples
=======================

The general syntax for this method is:

.. sourcecode:: csharp

   arrayName.SetValue(updateItem, index)

This method returns the value of the specified index.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      int[] myNums = new int[] { 10, 3, 4, 8, 12, 12};
      
      Console.WriteLine(myNums[4]);

      myNums.SetValue(6, 4);

      Console.WriteLine(myNums[4]);
      

   **Output**

   ::

      12
      6
      
