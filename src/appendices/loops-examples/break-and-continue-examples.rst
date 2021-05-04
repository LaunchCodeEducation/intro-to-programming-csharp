.. _break-and-continue-examples:

``break`` and ``continue`` Examples
====================================

``break`` is used to exit a loop.

``continue`` will skip the current iteration and move on to the next iteration.  Continuing the loop onward.

.. admonition:: Example

   ``break`` example

   .. sourcecode:: csharp
      :linenos:

      for(int i = 1; i <=10; i++)
      {
         if (i == 3)
         {
            break;
         }
         Console.WriteLine(i);
      }
   
   **Output**

   ::

      1
      2


In this example, once ``i`` becomes ``3`` the loop ends.   

If we wanted the loop to continue after skipping 3, then we'd need a continue statement.


.. admonition:: Example

   ``continue`` example

   .. sourcecode:: csharp
      :linenos:

      for(int i = 1; i <=10; i++)
      {
         if (i == 3)
         {
            continue;
         }
         Console.WriteLine(i);
      }
   
   **Output**

   ::

      1
      2
      4
      5

We iterated all the way to `5` as indicated in our ``for`` loop, but we skipped over ``3``.   The ``continue`` allowed us to return to the loop and continue printing ``4`` and ``5``.