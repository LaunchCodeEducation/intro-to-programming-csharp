.. _do-while-examples:

``do while`` Examples
=======================

``do while`` loops are similar to the ``while`` loop.  
However, this loop will execute a least once *before* 
checking on the status of the condition.  This loop will 
run again as long as the condition is true.


.. sourcecode:: csharp

   do
   {
      //code block to be executed
   }
   while (condition);



.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      int i = 0; 
      do
      {
         Console.WriteLine(i);
         i++;
      } 
      while(i < 5);

   **Output**

   ::

      0  
      1
      2
      3
      4


- In **Line 4** the ``do`` codeblock starts the loop by printing ``i``. 
- **Line 5** then updates ``i`` with ``i++``.
- In **Line 7** the newly updated ``i`` is compared to the ``while`` statement.

As long as the ``while`` statement is true, the ``do`` block will be executed again.

In this example, ``i`` is incremented up to ``4``.  We print ``4`` and then update ``i`` to 5 thanks to **Line 5**, but
now ``i`` is no longer less than 5, it's actually equal to 5, so the ``while`` statement is now ``false`` and the loop ends.
