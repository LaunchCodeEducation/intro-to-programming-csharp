===========================
Diagnosing Error Messages
===========================

Syntax and runtime errors *always* produce error messages. Reading and
understanding error messages is a crucial first step in fixing these types of
bugs.

**Error messages are your friends.**  Really.  This idea can seem foreign to new
programmers, because an error message is a signal that your program is broken.
When we are working with a broken program, we might feel frustrated, like we do
not fully understand the concepts at hand.

However, the reality is that *all* programmers, no matter how experienced,
regularly make simple mistakes. If you run your program and it produces an
error message, your first reaction should be, "Great! My program has an error,
but I have a helpful message to help me fix it."

Let's consider a small program with a couple of syntax errors.




.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      string name = "Julie";
      Console.WriteLine("Hello,  +  name);


While you can spot one or more errors just by looking at the code, let's
examine the error messages produced.

.. _syntax-error:

A Syntax Error
--------------

Running the program at this stage results in the message:

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      string name = "Julie";
      Console.WriteLine("Hello,  + name);

   **Console Output**

   ::

     main.cs(2,36): error CS1010: Newline in constant
     main.cs(3,2): error CS1525: Unexpected symbol `}', expecting `)' or `,'
     main.cs(3,3): error CS1002: ; expected
     Compilation failed: 3 error(s), 0 warnings
     compiler exit status 1





While there is a lot of text in this message, the **first** error tells us where to start.  
The rest of the errors are typically a result of the first error.  

The first portion identifies where in our code the error exists: ``main.cs(2,36): error CS1010: Newline in constant``.


This error number is telling us that error is located in the **main** namespace, line 2, character 36.  
Which in this case is the ``;`` or the final character of this line.  Sometimes using the coordinates are enough to help you find the error.
In this case, we see that we have a ``;`` okay, so what does that mean?  Perhaps, you can see the problem at this point.  Great!  
If not, it's okay.  This takes practice, and with each error you make, you will be better with your syntax.  
 
Sometimes you might need more information about *why* something is an error.  That is where the error numbers come in handy.  
You are not expected to memorize error numbers.  If you need more information than the snippet that is provided, copy and 
paste the number into your favorite search engine.  That will bring up the Microsoft Documentation, but you might also find other 
sites that discuss the error.  Browse and find an explanation that helps you best understand the error and, hopefully, manage or correct it.

Let's look at our first error message again.

::

   error CS1010: Newline in constant

This line identifies that actual issue that C# found.  If you are scratching your head at the message, "CS1010" or "Newline in constant",
don't worry. Programming languages often report errors in ways that are not always easy to decipher at first glance. 
However, a quick copy and paste can help us find out more.  

Let's start with the `Microsoft Documentation <https://docs.microsoft.com/en-us/dotnet/csharp/misc/cs1010>`__. on this error number.  


::

   Console.WriteLine("Hello,  + name);
               

.. index:: ! token

C# is telling us that in the ``Console.WriteLine`` a string was intiatied, but never closed.  
The compiler is looking for that closing ``"``.  Without that closing ``"``, it is unable to properly ready any of the other code. 

Fixing this error gives us a program with correct syntax:

.. sourcecode:: csharp
   :linenos:

   string name = "Julie";
   console.log("Hello, " + name);

.. note:: Error messages may differ depending on where you run your code. The same program run in a `repl.it <https://repl.it/>`_ and other IDEs on your computer will generate slightly different error messages. However, these differences are minor and generally unimportant. The main cause of the error will be reported in the same way.

A quick note on syntax errors.  Sometimes the coordinates of an error are referring to the line *above*.
This is very common when you leave off an ``;``.  Here is a quick example:

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      string name = "Julie"
      Console.WriteLine("Hello, " + name);

   **Console Output**

   ::

     main.cs(2,4): error CS1525: Unexpected symbol `Console'

If you scour line 2 for errors, you are going to drive yourself crazy.  Your line 2 is correct.  
*Why* does the complier think ``'Console'`` is a symbol?  If you look at line 1, you'll see there is no ``;`` to end the statement, 
so C# thinks that line 2 is part of your inital expression in line 1.


Syntax Errors and Code Highlighting
-----------------------------------

.. index::
   single: syntax; highlighting

Most code editors provide a feature known as **syntax highlighting**. Such
editors highlight different types of tokens in different ways. For example,
strings may be red, while data types may be blue. This useful feature gives you
a quick, visual way to identify syntax errors.

For example, here is a screenshot of our flawed code taken within an `editor at repl.it <https://repl.it/@launchcode/syntaxHighlightingCSharp>`_.

.. figure:: figures/syntax-highlights-csharp.png
   :alt: A screenshot with two lines of code. Sytax error on line 1 extends the expression into the next line, but C# knows that "Console" is a built-in method, so something is wrong.  
      Notice, however, there is no highlighting to inform you of you missin ``;``.
      Syntax error on line 2 causes highlighting to differ from what is expected.  The ``+``, variable name, and
      symbols ``);`` are red instead of black, because the preceding string "Hello, " doesn't have a closing double-quote.

   Screenshot of a program with one syntax error

Notice that the string ``Hello`` is colored red, while *most* of the symbols
(``=``, ``;``, ``.``, and ``(``) are colored black. At the end of line 2,
however, the final ``)`` and ``;`` are both red rather than black. Since we
haven't closed the string, the editor assumes that these two symbols are *part
of* the string. Since we expect ``);`` to be black in this editor, the
difference in color is a clue that something is wrong with our syntax.


A Runtime Error
---------------

Having fixed the syntax errors, let's talk about runtime errors.  These types of errors are found when you run the program.  


So using our same code, what if we declared our varialbe, but never initialized it?

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      string name;
      Console.WriteLine("Hello, " + name);

   **Console Output**

   ::

     main.cs(2,35): error CS0165: Use of unassigned local variable `name'

When you look at this code in the replit code editor, all the syntax highlighting is sound.  Once we hit run, we ger a new error code.  
This error message is very useful.  It tells us that in line 2, we are trying to call a variable that is empty.  Nothing has been assigned to it, we
never initialized it.  

Just glancing at these two lines, you might not have noticed the error right away.  So you hit run and you got an error.  
Congrats!  You have a clue to help you fix the reason it is not working.  This is good news!  No really, errors are your friends.


These types of errors can be very helpful because they return with information about the issue.  Not all errors are this easy to sort out.  
What happens when our syntax is sound, we are running through all the lines smoothly, but not getting the expected output?  Might be a logic error.
Let's dive into those in the next section.

