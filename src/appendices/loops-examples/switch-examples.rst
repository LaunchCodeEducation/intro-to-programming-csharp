.. _switch-examples:

``switch`` Examples
=====================

The ``switch`` statement can be used to select one of many code 
blocks to execute.  It is often used as an alternative to an ``if-else`` statement
when a single expression is being tested against three or more conditions.

Works with the keywords ``case`` and ``break``.  

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      switch (expression)
      {
         case x:
            //code block
            break;
         case y:
            //code block
            break;
         default:
            //code block
            break;
      }


The ``switch`` expression is evaluated once.  
The value of the expression is compared to values in each ``case``, 
until matched and that code block is executed followed by ``break`` and the loop ends.


``break`` is used to escape a switch block.  Each case contains a ``break``.  
Once a match is found, its ``break`` statement will be executed and the ``switch`` will be terminated.

``default`` is optional, but it can be used as a catch all if the other ``cases`` are looking for a specific match.  
Think of it like the ``else`` in ``if/else`` statements.  In the example above, we could have used ``case`` in **Line 9** instead of ``default`` .

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      int pet = 1;
      switch(pet)
      {
         case 1: 
            Console.WriteLine("I have a pet dog.");
            break;
         case 2:
            Console.WriteLine("I have a pet cat.");
            break;
         case 3: 
            Console.WriteLine("I have a pet fish.");
            break;
         default: 
            Console.WriteLine("I have a pet.");
            break;
      }
   
   **Output**

   ::

      I have a pet dog.


In the example above, if ``int pet = 5`` then then ``default`` would be exectuted.


If instead of ``default``, you had ``case 4`` and ``int pet = 5`` then the none of the cases would be executed.