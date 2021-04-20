.. _while-loop-examples:

``while`` Loop Examples
=========================

This loop is best for when you know the specific condition you need to meet, 
but the exact number of times to reach that condition are not a big concern. 

.. sourcecode:: csharp

   while (boolean expression) {
      body
   }

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      string prompt = "Please enter a negative number: ";
      Console.WriteLine(prompt);
      string input = Console.ReadLine();
      int num = Int32.Parse(input);

      while (num >= 0) 
      {
         Console.WriteLine(prompt);
         input = Console.ReadLine();
         num = Int32.Parse(input);
      }
      
      Console.WriteLine("Your number was: " + num);

In this example, we hope it will take the user a single try to enter a negative number, 
but the ``while`` loop is here to help us allow for numerous attempts.

``While`` loops can also be used when you have a specific number of iterations.  
You can easily convert a ``for`` into a ``while`` loop as we discussed in :ref:`chapter 9 <while-loops>` .
      
