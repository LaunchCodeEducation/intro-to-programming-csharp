Breaking Down the ``for`` Statement
===================================

Having seen several examples, we will now explore the syntax of a ``for`` loop
in more depth.

Recall the first example of a ``for`` loop that we looked at.

.. sourcecode:: csharp
   :linenos:

   for (int i = 0; i < 51; i++) 
   {
      Console.WriteLine(i);
   }

We broke down the flow of execution of this loop, noting that the loop executes
once for each of the values of ``i`` from 0...50. The three components of the
loop---loop variable, loop condition, and update expression---dictate exactly
how this loop executes. So far, we have only seen ``for`` loops with this exact
form:

.. sourcecode:: csharp
   :linenos:

   for (int i = 0; i < upperBound; i++) 
   {
      // loop body
   }

However, the three components of a ``for`` loop statement can take different
forms to create more complex looping behavior.

``for`` Loop Anatomy
--------------------

The general form of a ``for`` loop is:

::

   for (initial expression; loop condition; update expression) 
   {
      loop body
   }

Let's look at each of the three components that affect how this loop iterates.

Initial Expression
^^^^^^^^^^^^^^^^^^

.. index::
   single: for loop; initial expression
   single: for loop; variable

The **initial expression** is executed once, before any iterations of the loop.
It can be any expression, even the **empty expression** (which contains no
code). However, it almost always declares and initializes a variable, known as
the **loop variable**.

The loop variable can be initialized to any value.

.. admonition:: Examples

   This loop prints 3...9.

   .. sourcecode:: csharp
      :linenos:

      for (int i = 3; i < 10; i++) 
      {
         Console.WriteLine(i);
      }

   This loop prints each of the letters ``C``, ``o``, ``d``, and ``e`` on a separate line.

   .. sourcecode:: csharp
      :linenos:

      let name = "LaunchCode";

      for (int i = 6; i < name.Length; i++) 
      {
         Console.WriteLine(name[i]);
      }

To avoid confusion and bugs, you should give your loop variable a unique name, one that you have not used elsewhere in your program. 
In cases where the loop variable is serving as a "counter" for iterations of a loop, it is conventional to use ``i`` for the variable name. 
In the case of **nested** ``for`` loops (loops inside of loops), the variables ``j``, ``k``, etc. are often used.

.. admonition:: Note

   The loop variable is typically used by the loop body, but this is not
   required. The following example is a valid ``for`` loop that prints
   ``"LaunchCode"`` 42 times.

   .. sourcecode:: csharp
      :linenos:

      for (int i = 0; i < 42; i++) 
      {
         Console.WriteLine("LaunchCode");
      }

Loop Condition
^^^^^^^^^^^^^^

.. index::
   single: for loop; condition

The **loop condition** is executed before each loop iteration. It is *always* a
boolean expression, evaluating to ``true`` or ``false``. If the condition is
true, the loop body executes. If the condition is false, loop execution stops
and the program continues with the next line of code below the loop.

.. admonition:: Example

   This loop does not iterate at all, because its condition is false to start with.

   .. sourcecode:: csharp
      :linenos:

      for (int i = 0; i < -1; i++) 
      {
         Console.WriteLine("LaunchCode");
      }

It is critical that the loop condition *eventually* becomes false. A loop for
which the condition is never false is known as an **infinite loop**, because it
never stops iterating. A program that contains an infinite loop will only stop
after running out of memory or being manually stopped (for example, using
control+c in a terminal).

.. admonition:: Example

   This is an infinite loop, because its condition will always be true.

   .. sourcecode:: csharp
      :linenos:

      for (int i = 0; i > -1; i++) 
      {
         Console.WriteLine("LaunchCode");
      }

You will accidentally write an infinite loop at some point; doing so is a rite
of passage for new programmers. When this happens, don't panic. Stop your
program and figure out why your loop condition never became false.

Update Expression
^^^^^^^^^^^^^^^^^

.. index::
   single: for loop; update expression

The final component in a for loop definition is the **update expression**,
which executes after *every* iteration of the loop. While this expression may
be anything, it most often updates the value of the loop variable.

In all of the examples we have seen so far, the update expression has been
``i++``, incrementing the loop variable by 1. However, it can update the loop
variable in other ways.

.. admonition:: Example

   This loop prints *even* integers from 0...50.

   .. sourcecode:: csharp
      :linenos:

      for (int i = 0; i < 51; i = i + 2) 
      {
         Console.WriteLine(i);
      }

A bad choice of update expression can also cause an *infinite loop*.

.. admonition:: Example

   This loop repeats indefinitely, since ``i`` becomes smaller with each
   iteration and thus is never greater than or equal to 51.

   .. sourcecode:: csharp
      :linenos:

      for (int i = 0; i < 51; i--) 
      {
         Console.WriteLine(i);
      }

.. admonition:: Try It!

   How does each of the three components affect the behavior of a ``for`` loop?
   Experiment by modifying each of them in this example: the variable
   initialization, the boolean condition, and the update expression.

   .. replit:: csharp
      :linenos:
      :slug: Loop-variable-CSharp

      for (int i = 0; i < 51; i++) 
      {
         Console.WriteLine(i);
      }

Check Your Understanding
------------------------

Consider the program:

.. sourcecode:: csharp
   :linenos:

   string phrase = "Schrodinger's cat'";

   for (int i = 0; i < phrase.Length - 1; i = i + 3) 
   {
      Console.WriteLine(phrase[i]);
   }

.. admonition:: Question

   How many times does the loop body execute?

   #. 5
   #. 6
   #. 17
   #. 18

.. ans. 6

.. admonition:: Question

   Which set of characters is printed by the loop? (We have placed characters for the choices below on the same line, but they would be on separate lines in the actual program output.)

   #. ``Schrodinger's cat``
   #. ``Schrodinger's ca``
   #. ``S, r, i, e, s, a``
   #. ``S, o, g, s, t, ' '``

.. ans. S, r, i, e, s, a
