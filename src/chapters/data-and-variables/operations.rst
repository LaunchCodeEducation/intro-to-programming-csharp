==========
Operations
==========

Operators and Operands
----------------------

Now that we can store data in variables, let's explore how we can generate new data from existing data.

.. index:: ! operator, ! operand

An **operator** is one or more characters that represents a computation like addition, multiplication, or division. The values an operator works on are called **operands**.

The following are all legal C# expressions whose meaning is more or less clear:

- ``20 + 32``
- ``hour - 1``
- ``hour * 60 + minute``
- ``minute / 60``
- ``Math.Pow(5,2)``
- ``(5 + 9) * (15 - 7)``

For example, in the calculation ``20 + 32``, the operator is ``+`` and the operands are ``20`` and ``32``.

The symbols ``+`` and ``-``, and the use of parentheses for grouping, mean in C# what they mean in mathematics. The asterisk (``*``) is the symbol for multiplication, and ``Math.Pow()`` is the method for exponentiation. Addition, subtraction, multiplication, and exponentiation all do what you expect.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine(2 + 3);
      Console.WriteLine(2 - 3);
      Console.WriteLine(2 * 3);
      Console.WriteLine(Math.Pow(2,3));
      Console.WriteLine(Math.Pow(3,2));

   **Console Output**

   ::

      5
      -1
      6
      8
      9

We use the same terminology as before, stating that ``2 + 3`` **returns** the value ``5``.

When a variable name appears in the place of an operand, it is replaced with the value that it refers to before the operation is performed. For example, suppose that we wanted to convert 645 minutes into hours. Division is denoted by the operator ``/``.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      double minutes = 645;
      double hours = minutes / 60;
      Console.WriteLine(hours);

   **Console Output**

   ::

      10.75

In summary, operators and operands can be combined to create expressions that are evaluated upon execution. Let's discuss some specific types of operators

Arithmetic Operators
--------------------

.. index:: ! arithmetic operators

.. index:: ! +, ! -, ! *, ! /, ! Math.Pow(), ! ++, ! --

Some of most commonly-used operators are the **arithmetic operators**, which carry out basic mathematical operations. These behave exactly as you are used to, though the modulus operator (``%``) may be new to you.

.. list-table:: Arithmetic operators
   :widths: auto
   :header-rows: 1

   * - Operator
     - Description
     - Example
   * - Addition (``+``)
     - Adds the two operands
     - ``2 + 3`` returns ``5``
   * - Subtraction (``-``)
     - Subtracts the two operands
     - ``2 - 3`` returns ``-1``
   * - Multiplication (``*``)
     - Multiplies the two operands
     - ``2 * 3`` returns ``6``
   * - Division (``/``)
     - Divides the first operand by the second
     - ``6 / 2`` returns ``3``
   * - Modulus (``%``)
     - Aka the remainder operator. Returns the integer remainder of dividing the two operands.
     - ``7 % 5`` returns ``2``
   * - Exponentiation (``Math.Pow()``)
     - Calculates the base (first operand) to the exponent (second operand) power, that is, base\ :sup:`exponent`.  Math.Pow(base, exponent).
     - ``Math.Pow(3, 2)`` returns ``9``

       ``Math.Pow(5, -1)`` returns ``0.2``
   * - Increment (``++``)
     - Adds one to its operand. If used before the operand (``++x``), returns the value of its operand after adding one; if used after the operand (``x++``), returns the value of its operand before adding one.
     - If ``x`` is ``2``, then ``++x`` sets ``x`` to ``3`` and returns ``3``, whereas ``x++`` returns ``2`` and, only then, sets ``x`` to ``3``
   * - Decrement (``--``)
     - Subtracts one from its operand. The return value is analogous to that for the increment operator.
     - If ``x`` is ``2``, then ``--x`` sets ``x`` to ``1`` and returns ``1``, whereas ``x--`` returns ``2`` and, only then, sets ``x`` to ``1``

.. index:: ! modulus, ! %

More on the Modulus
^^^^^^^^^^^^^^^^^^^^

While the **modulus operator** (``%``) is common in programming, it is not used much
outside of programming. Let's explore how it works with a few examples.

The ``%`` operator returns the *remainder* obtained by carrying out integer division of the first operand by the second operand. Therefore, ``5 % 3`` is ``2`` because 3 goes into 5 one whole time, with a remainder of 2 left over.

.. admonition:: Examples

   - 12 % 4 is 0, because 4 divides 12 evenly (that is, there is no remainder)
   - 13 % 7 is 6
   - 6 % 2 is 0
   - 7 % 2 is 1

The last two examples illustrate a general rule: An integer x is even exactly
when ``x % 2`` is ``0`` and is odd exactly when ``x % 2`` is ``1``.

.. admonition:: Note

   The value returned by ``a % b`` will be in the range from ``0`` to ``b``
   (not including ``b``).

.. admonition:: Tip

   If remainders and the modulus operator seem tricky to you, we recommend
   getting additional practice at `Khan Academy <https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/what-is-modular-arithmetic>`_.


More on Exponentiation
^^^^^^^^^^^^^^^^^^^^^^^
In C#, the ``Math.Pow()`` method is needed to do these types of calculations.  Keep in mind that this method uses **double** data types only.  
This method already uses parentheses, so adding more can become confusing.  It can be easier to create variables for the numbers you wish to manipulate 
and use them to complete your mathematical expressions.


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      /* 
      using the variables in the Math.Pow() method and 
      perfroming the exponentiation in the Console.WriteLine
      */

      double num1 = 4;
      double num2 = 3;
      Console.WriteLine(Math.Pow(num1, num2));

      /*  
      creating a variable for the exponentiation 
      which will be called in the Console.WriteLine
      */

      double numPower = Math.Pow(num1, num2);
      Console.WriteLine(numPower);

   **Console Output**

   ::

      64
      64

When working with a longer expression, variables can help with order of operations.  You can even use your variables in the expression.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      double num1 = 4;
      double num2 = 3;
      double numPower = Math.Pow(num1, num2);
      Console.WriteLine((numPower + 5) / 2);
      Console.WriteLine((numPower * 3) + (12 / num1))

   **Console Output**

   ::

      34.5
      195


Order of Operations
-------------------

.. index:: ! order of operations

When more than one operator appears in an expression, the order of evaluation depends on the **rules of precedence**. C# follows the same precedence rules for its arithmetic operators that mathematics does.

#. Parentheses have the highest precedence and can be used to force an
   expression to evaluate in the order you want. Since expressions in
   parentheses are evaluated first, ``2 * (3 - 1)`` is 4, and ``(1 + 1) * (5 - 2)`` is 6. You can also use parentheses to make an expression easier to read, as in ``(minute * 100) / 60``, even though it doesn't change the result.
#. Exponentiation has the next highest precedence.    
   While you can directly use numbers in this method, like so ``Math.Pow(2,  1) + 1``, longer expressions with multiple parentheses can make things confusing.  
   With longer expressions, creating variables to hold your exponentiation will make things easier to read and calculate correctly.
#. Multiplication, division, and modulus operators have the same precedence,
   which is higher than addition and subtraction, which also have the same
   precedence. So ``2 * 3 - 1`` yields 5 rather than 4, and ``5 - 2 * 2`` is 1,
   not 6.
#. Operators with the *same* precedence are evaluated from left-to-right. So in
   the expression ``6 - 3 + 2``, the subtraction happens first, yielding 3. We
   then add 2 to get the result 5. If the operations had been evaluated from
   right to left, the result would have been ``6 - (3 + 2)``, which is 1.

.. index:: PEMDAS

.. admonition:: Tip

   The acronym PEMDAS can be used to remember order of operations:

   **P** = parentheses

   **E** = exponentiation

   **M** = multiplication

   **D** = division

   **A** = addition

   **S** = subtraction


Operators, such as ``+`` and ``*``, are type-dependent.
That is, we can only use them on allowed types, and their effects are
different depending on which types we use them on. The ``+`` operator is
a good example of this. We can use ``+`` to add numeric types together,
such as ``2 + 2`` which results in ``4``. But we can also use it to
concatenate strings: ``"2" + "2"``, for example, which results in
``"22"``. What the operators do depends on the type they are operating
on, and we may not mix types in arbitrary ways (``"2" + 2`` results in a
compiler error).

.. admonition:: Note

   Numeric types such as ``int`` and ``double`` may be freely mixed when
   using numeric operators. Generally, the result of such mixing is that
   the output has the type of the more precise input. For example, the
   following snippet would print out ``System.Double``.

   .. sourcecode:: c#

      int a = 2;
      double b = 3;
      Console.WriteLine((a + b).GetType());


Check Your Understanding
------------------------

.. admonition:: Question

   What is the value of the following expression?

   .. sourcecode:: csharp

      Console.WriteLine(16 - 2 * 5 / 3 + 1);

   #. 14
   #. 24
   #. 3
   #. 13.666666666666666

.. admonition:: Question

   What is the output of the code below?

   .. sourcecode:: csharp

      Console.WriteLine(1 + 5 % 3);


.. admonition:: Question

   What is the value of the following expression?

   *Note:* Using the **^** "carrot" symbol is common short hand for showing exponentiation, but not used in C#.

   .. sourcecode:: csharp

      2 ^ 2 ^ 3 * 3

   #. 768
   #. 128
   #. 12
   #. 256
