==================================
Output With ``Console.WriteLine``
==================================

In the :ref:`Hello World <hello-world>` section, you experimented with
displaying text on the screen. Technically, you sent the words to the
**console**, which is a simple window where the user can type commands or view
output. We used a print function without explicitly talking about how it works.
Let’s fix that now.

We *call* the print function using the syntax ``Console.WriteLine()``. When the code
runs, we want it to tell the computer, *Please display what is inside the () on
the screen*. For us, the words are enough - we want to WRITE (the) LINE of text to the
CONSOLE. However, the computer only understands binary or hexadecimal
instructions. We need the compiler to change the keywords *Console* and *WriteLine*
into a format that the machine understands.

Examples
---------

Open the repl.it link in the example below, and note the difference between the
outputs:

.. replit:: csharp
   :slug: ConsoleWriteLineExamples01
   :linenos:

   Console.WriteLine("Hello, C#.");
   Console.WriteLine(2001);
   Console.WriteLine("What","do","commas","do?");
   Console.WriteLine("What" + "does" + "+" + "do?");
   Console.WriteLine("How " + "can" + " you" + "add   " + "spaces?");
   Console.WriteLine("LaunchCode was founded in" +  2013);

Observations line by line:

#. In the line 1, we print some text, which is surrounded by quotes.
#. In the line 2, we print a number. Note the absence of quote marks.
#. In line 3, we use four words, separated by commas, all within the same
   set of parentheses ``()``. When this statement prints, we only see the first word.
#. The code in line 4 prints all of the words using the ``+``, but where are the spaces?
#. Line 5 also prints all of the words including the spaces added to each word within the double quotation marks.
#. Line 6 prints text and a number without a space in between.

Two Special Characters
-----------------------

One final observation for all of the examples above is that each time we use
``Console.WriteLine``, a **newline** is inserted after the printed content. Think of
a newline as the same as hitting the Enter or Return key on your keyboard. The
cursor moves to the beginning of the next line.

For the computer, *newline* is an invisible character that is used to tell the
machine to move to the next line. It is possible to use this invisible
character with the special representation ``\n``.

.. admonition:: Try It

   Experiment with the newline character.

   .. replit:: csharp
      :slug: ConsoleWriteLineExamples02
      :linenos:

      Console.WriteLine("Some Programming Languages:");

      Console.WriteLine("C#\nPython\nJavaScript\nJava\nSwift");

In addition to the newline character, there is also a special tab character,
``\t``. Go back to the eight examples above and experiment with using ``\t``
and ``\n``.




