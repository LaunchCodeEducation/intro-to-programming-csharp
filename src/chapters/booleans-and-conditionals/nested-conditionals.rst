====================
Nested Conditionals
====================

We can write code with more complex branching behavior by combining
conditionals and, in particular, by nesting conditionals. 

Let's see how thisworks by tackling the following problem.

.. admonition:: Example

    Write code that prints different messages based on the value of a number variable. If the number is odd, print nothing. If it is even, print "EVEN". If it is also positive print "POSITIVE".

Our first attempt at a solution might look like this:

.. sourcecode:: csharp
   :linenos:

   int num = 7;

   if (num % 2 == 0) 
   {
      Console.WriteLine("EVEN");
   }

   if (num > 0) 
   {
      Console.WriteLine("POSITIVE");
   }

**Console Output**

::

   POSITIVE

We find that the output is ``POSITIVE``, even though 7 is odd and so nothing
should be printed. This code doesn't work as desired because we only want to
test for positivity when we already know that the number is even. We can
enable this behavior by putting the second conditional *inside* the first.

.. replit:: csharp
   :linenos:
   :slug: Positive-and-Even-CSharp

   int num = 7;

   if (num % 2 == 0) 
   {
       Console.WriteLine("EVEN");

       if (num > 0) 
       {
           Console.WriteLine("POSITIVE");
       }
   }


.. admonition:: Try It!

   Run the previous example with several different values for ``num`` (even,
   odd, positive, negative) to ensure it works as desired. Nice, huh?

Notice that when we put one conditional inside another, the body of the nested
conditional is indented by two tabs rather than one. This convention provides
an easy, visual way to determine which code is part of which conditional.

Nested ``if`` statements can also contain an ``else`` statement.  When working with nested statements, the ``else`` clause 
belongs to the last unpaired ``if``.  Remember from them previous chapter that you can only use an ``else`` when you have an ``if``.

.. sourcecode:: csharp
   :linenos:

   int num = 7;

   if(num < 9)
   {   
      if (num % 2 == 0) 
      {
         Console.WriteLine("EVEN");
      }

      else 
      {
         Console.WriteLine("ODD");
      }
   }

**Console Output**

::

   ODD

When working with ``else`` statements in nested conditionals, remember that the ``else`` is 
paired with the last ``if`` that doesn't have already have an ``else``.  In the example above, the ``else``
statement in line 10 belongs to the ``if`` in line 5.  

``else`` and ``else if`` rules apply the same way within nested conditionals as in unnested ones.  

Check Your Understanding
------------------------

.. admonition:: Question

   What is printed when the following code runs?

   .. sourcecode:: csharp
      :linenos:

      int num = 7;

      if (num % 2 == 0) 
      {
          if (num % 2 == 1) 
          {
            Console.WriteLine("odd");
          }
      }

   #. The code won't run due to invalid syntax
   #. ``odd``
   #. ``even``
   #. The code runs but doesn't print anything


.. admonition:: Question

   Considering the same conditional used in the previous question, which values of ``num`` would result in ``"odd"`` being printed?

   .. sourcecode:: csharp
      :linenos:

      if (num % 2 == 0) 
      {
          if (num % 2 == 1) 
          {
            Console.WriteLine("odd");
          }
      }

   #. Even values of ``num``.
   #. Odd values of ``num``.
   #. No values. It is impossible for the call to ``Console.WriteLine`` to ever run, given the two conditions.
   #. ``num`` is 0.
