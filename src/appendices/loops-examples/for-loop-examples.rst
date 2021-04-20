.. _for-loop-examples:

``for`` Loop Examples
=======================

This loop is best used when you know exactly how many times you want to loop to run.  

.. sourcecode:: csharp

      for (initial expression; loop condition; update expression) 
   {
      loop body
   }

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      int[] nums = new int[] { 1, 2, 3, 4, 5, 6, 7, 8, 9 };

      for(int i = 0; i < nums.Length; i += 2)
      {
         Console.WriteLine(nums[i]);
      }

   **Output**

   ::

      1
      3
      5
      7
      9

      
.. index::
   single: nested loop;

.. admonition:: Example

   Using a nested loop to create a pattern of stars and spaces using the ``Console.Write`` method.

   .. sourcecode:: csharp
      :linenos:
      
      int star;
      int space;
        
      for(star = 0; star <= 6; star++) 
      {
         for(space = 1 ; space <= 7-star; space++) 
         {
            Console.Write("*");
         }
           
         Console.Write("\n"); 
      }

   **Output**

   ::

      *******
      ******
      *****
      ****
      ***
      **
      *

Above is an example of a nested ``for`` loop, but you can nest ANY loop.
