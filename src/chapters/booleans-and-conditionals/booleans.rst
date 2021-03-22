.. _booleans:

=========
Booleans
=========

.. index:: data type

One of the core features of any programming language is the ability to
conditionally execute a segment of code. This means that a program will run a
segment of code *only if* a given condition is met.

.. admonition:: Example

   Consider a banking application that can remind you when a bill is due. The
   application will notify you that a bill is due soon, but *only if* the bill
   has not already been paid.

The condition for the above example is: Send a notification of an upcoming bill
only if the statement "the bill is unpaid" is true. In order to state something
like this in C#, we need to understand how programming languages
represent true and false.

Boolean Values
--------------

.. index:: ! true, ! false, ! boolean

.. index::
   single: boolean; value

The C# data type for storing true and false values is ``boolean``,
named after the British mathematician George Boole.

.. admonition:: Fun Fact

   George Boole created `Boolean Algebra <https://en.wikipedia.org/wiki/Boolean_algebra>`_,
   which is the basis of all modern computer arithmetic.

There are only two **boolean values**---``true`` and ``false``. C# is
case-sensitive, so ``True`` and ``False`` are *not* valid boolean values.  

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(true);
      Console.WriteLine(true.GetType());
      Console.WriteLine(false.GetType());

   **Console Output**

   ::

      True
      System.Boolean
      System.Boolean

The values ``true`` and ``false`` are *not* strings. If you use quotes to
surround booleans (``"true"`` and ``"false"``), those values become strings.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(true.GetType());
      Console.WriteLine("true".GetType());

   **Console Output**

   ::

      System.Boolean
      System.String

Boolean Conversion
------------------

.. index:: ! Boolean(), type conversion

As with the numeric and string data types, the boolean type also has a
conversion function, ``Convert.ToBoolean()``. It works similarly to the ``Int32.Parse()`` and
``Double.Parse()`` methods, attempting to convert a non-boolean value to a boolean.  This is very limited as is, 
but this could be useful if working with user input, specifically the words "true" and "false".  

.. admonition:: Try It!

   Explore how ``Convert.ToBoolean()`` converts various non-boolean values.  Explore differnt data types.  
   
   .. replit:: bash
      :linenos:
      :slug: Boolean-Type-Conversion-CSharp
      
      Console.WriteLine(Convert.ToBoolean("true"));
      Console.WriteLine(Convert.ToBoolean("TRUE"));
      Console.WriteLine(Convert.ToBoolean(0));
      Console.WriteLine(Convert.ToBoolean(1));
      Console.WriteLine(Convert.ToBoolean(-1));
      Console.WriteLine(Convert.ToBoolean(""));
      Console.WriteLine(Convert.ToBoolean("LaunchCode"));
      



Boolean Expressions
-------------------

.. index::
   single: boolean; expression

.. index::
   single: operator; equality

.. index:: ! ==

A **boolean expression** is an expression that evaluates to either ``True`` or
``False``. The equality operator, ``==``, compares two values and returns true
or false depending on whether the values are equal.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(5 == 5);
      Console.WriteLine(5 == 6);

   **Console Output**

   ::

      True
      False

In the first statement, the two operands are equal, so the expression evaluates
to ``True``. In the second statement, 5 is not equal to 6, so we get ``False``.


Comparison Operators
^^^^^^^^^^^^^^^^^^^^

.. index::
   single: operator; comparison

The ``==`` operator is one of six common **comparison operators**.

.. index:: ==, ! !=, ! <, ! >, ! <=, ! >=

.. list-table:: Comparison Operators
   :widths: auto
   :header-rows: 1

   * - Operator
     - Description
     - Examples Returning ``True``
     - Examples Returning ``False``
   * - Equal (``==``)
     - Returns ``True`` if the two operands are equal, and ``False`` otherwise.
     - ``7 == 7``

       ``"dog" == "dog"``
     - ``7 == 5``

       ``"dog" == "cat"``
   * - Not equal(``!=``)
     - Returns ``True`` if the two operands are not equal, and ``False`` otherwise.
     - ``7 != 5``

       ``"dog" != "cat"``
     - ``7 != 7``

       ``"dog" != "dog"``
   * - Greater than (``>``)
     - Returns ``True`` if the left-hand operand is greater than the right-hand operand, and ``False`` otherwise.
     - ``7 > 5``

       ``'b' > 'a'``
     - ``5 > 7``

       ``'a' > 'b'``
   * - Less than (``<``)
     - Returns ``True`` if the left-hand operand is less than the right-hand operand, and ``False`` otherwise.
     - ``5 < 7``

       ``'a' < 'b'``
     - ``7 < 5``

       ``'b' < 'a'``
   * - Greater than or equal (``>=``)
     - Returns ``True`` if the left-hand operand is greater than or equal to the right-hand operand, and ``False`` otherwise.
     - ``7 >= 5``

       ``7 >= 7``

       ``'b' >= 'a'``

       ``'b' >= 'b'``
     - ``5 >= 7``

       ``'a' >= 'b'``
   * - Less than or equal (``<=``)
     - Returns ``True`` if the left-hand operand is less than or equal to the right-hand operand, and ``False`` otherwise.
     - ``5 <= 7``

       ``5 <= 5``

       ``'a' <= 'b'``

       ``'a' <= 'a'``
     - ``7 <= 5``

       ``'b' <= 'a'``


Although these operations are probably familiar, the C# symbols are
different from the mathematical symbols. A common error is to use a single
equal sign (``=``) instead of a double equal sign (``==``). Remember that ``=``
is an *assignment* operator and ``==`` is a *comparison* operator. Also note
that ``=<`` and ``=>`` are not recognized operators.

An equality test is *symmetric*, meaning that we can swap the places of the
operands and the result is the same.  For a variable ``a``, if ``a == 7`` is
``True`` then ``7 == a`` is also ``True``. However, an assignment statement is
not symmetric: ``a = 7`` is legal while ``7 = a`` is not.


Check Your Understanding
------------------------

.. admonition:: Question

   Under which conditions does ``Convert.ToBoolean()`` convert a string to ``True``?

   #. When the string is ``"true"``, ``"TRUE"`` or ``"True"``.
   #. Whenever the string contains any non-whitespace character.
   #. Whenever the string is non-empty.
   #. Never. It converts all strings to ``False``.

.. Answer = a

.. admonition:: Question

   Which of the following is a Boolean expression? Select all that apply.

   #. ``3 == 4``
   #. ``3 + 4``
   #. ``3 + 4 == 7``
   #. ``"false"``
