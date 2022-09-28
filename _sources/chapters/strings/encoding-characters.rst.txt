Encoding Characters
===================

.. index:: ! bit, character encoding

If you had a microscope powerful enough to view the data stored on a computer's
hard drive, or in its memory, you would see lots of 0s and 1s. Each such 0 and
1 is known as a **bit**. A bit is a unit of measurement, like a meter or a
pound. Collections of computer data are measured in bits; every letter, image,
and pixel you interact with on a computer is represented by bits.

We work with more complex data when we program, including numbers and strings.
This section examines how such data is represented within a computer.

Representing Numbers
--------------------

.. index:: ! byte

.. index::
   pair: number; binary
   pair: number; decimal

A **byte** is a set of 8 bits. Bytes look like 00101101 or 11110011, and they
represent a **binary number**, or a base-2 number. A binary number is a number
representation that uses only 0s and 1s. The numbers that you are used to,
which are built out of the integers 0...9, are **decimal numbers**, or base-10
numbers.

Since each bit can have one of two values, each byte can have one of
2\ :sup:`8` = 256 different values.

It may not be obvious, but every decimal integer can be represented as a binary
integer, and vice versa. There are 256 different values a byte may take, each
of which can be used to represent a decimal integer, from 0 to 255.

.. admonition:: Note

   We will not go into binary to decimal number conversion. If you are
   interested in learning more, there are `many <https://www.khanacademy.org/math/algebra-home/alg-intro-to-algebra/algebra-alternate-number-bases/v/decimal-to-binary>`_ `tutorials <https://www.youtube.com/watch?v=wPvI19DmWQw>`_ `online <https://www.rapidtables.com/convert/number/decimal-to-binary.html>`_ that can show you the way.

In this way, the bits in a computer can be viewed as integers. If you want to
represent values greater than 255, just use more bits!

Representing Strings
--------------------

Strings are collections of characters, so if we can represent each character
as a number, then we'll have a way to go from a string to a collection of bits,
and back again.

Character Encodings
^^^^^^^^^^^^^^^^^^^

.. index::
   pair: character; encoding

Unlike the natural translation between binary and decimal numbers, there is no
natural translation between integers and characters. For example, you might
create a pairing of 0 to ``a``, 1 to ``b``, and so on. But what integer should
be paired with ``$`` or a tab? Since there is no natural way to translate
between characters and integers, computer scientists have had to make such
translations up. Such translations are called **character encodings**.

.. index:: Unicode

There are many different encodings, some of which continue to evolve as our use
of data evolves. For instance, the most recent versions of the Unicode
character encoding include emoji characters, such as 🌮.

The ASCII Encoding
^^^^^^^^^^^^^^^^^^

.. index:: ASCII

Most of the characters that you are used to using---including letters, numbers,
whitespace, punctuation, and symbols---are part of the **ASCII** (pronounced
*ask-ee*) character encoding. This standard has changed very little since the
1960s, and it is the foundation of all other commonly-used encodings.

.. admonition:: Note

   ASCII stands for American Standard Code for Information Interchange, but
   most programmers never remember that, so you shouldn't try to either.

ASCII provides a standard translation of the most commonly-used characters to
one of the integers 0...127, which means each character can be stored in a
computer using a single byte.

.. index::
   single: ASCII; table

Using the Dec, or decimal column, ASCII maps ``a`` to 97, ``b`` to 98, and so on for lowercase letters, with ``z`` mapping to 122. 
Uppercase letters map to the values 65 through 90. 
The other integers between 0 and 127 represent symbols, punctuation, and other assorted odd characters. 
This scheme is called the **ASCII table**, and rather than replicate it here, we refer you to an `excellent one online <https://www.ascii-code.com/>`_.

In summary, strings are stored in a computer using the following process:

#. Break a string into its individual characters.
#. Use a character encoding, such as ASCII, to convert each of the characters
   to an integer.
#. Convert each integer to a series of bits using decimal-to-binary integer
   conversion.

.. admonition:: Fun Fact

   C# uses the UTF-16 encoding, which includes ASCII as a subset. We will rarely need anything outside of its ASCII subset, so we will usually talk about "ASCII codes" in C#.

Character Encodings in C#
---------------------------------

In C#, the character data type, or **char**, is able to handle the integer input of a unicode reference with some implicit type casting and vice versa.

.. admonition:: Example
   
   .. sourcecode:: csharp
      :linenos:

      char letter1 = (char)97;
      int letter2 = 'a';

      Console.WriteLine(letter1);
      Console.WriteLine(letter2);
      Console.WriteLine(letter1 == letter2)

   **Output**

   :: 

      a
      97
      True

In **Line 1** we initialized the variable letter1 to be of type **char**.  We then initialized it to be 97, which is an **int**.
For C# to understand that we want the character that number is encoded as, we have to **explicitly cast** it to be a **char**.  
Explicit casting occurs when we manually convert a larger data type to a smaller one.  
This is done manually by placing the data type desired in parentheses *in front* of the value.
In this example we used the ``(char)`` in front of the integer to 
tell the compiler that we want the actual **char** that is represented by the ``97``.  The compiler will read it as such and print ``a``.  

Int is able to accept a **char**, and will return the ASCII value.  The compiler reads **Line 2** and sees that you want an **int** value for this **char**.
It returns ``97``.  

In order to use this with string data types, we need to break our string into a character array.  We will discuss arrays and this method in the next chapter.
For now, we can use single **chars** and **ints** for encoding purposes.  

.. admonition::  Example

   .. sourcecode:: csharp
      :linenos:

      int c1 = 'C';
      int c2 = ' ';
      int c3 = 'S';
      int c4 = 'h';
      int c5 = 'a';
      int c6 = 'r';
      int c7 = 'p';

      Console.WriteLine(c1);
      Console.WriteLine(c2);
      Console.WriteLine(c3);
      Console.WriteLine(c4);
      Console.WriteLine(c5);
      Console.WriteLine(c6);
      Console.WriteLine(c7);

   **Console Output**

   ::  
      
      67
      32
      83
      104
      97
      114
      112


To convert an ASCII code to an actual character, initialize a **char** variable and explicitly cast the value to **char**.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      char num1 = (char)67;
      char num2 = (char)32;
      char num3 = (char)83;
      char num4 = (char)104;
      char num5 = (char)97;
      char num6 = (char)114;
      char num7 = (char)112;
      
      Console.WriteLine(num1);
      Console.WriteLine(num2);
      Console.WriteLine(num3);
      Console.WriteLine(num4);
      Console.WriteLine(num5);
      Console.WriteLine(num6);
      Console.WriteLine(num7);

   **Console Output**

   ::

      C 
       
      S
      h
      a
      r
      p
