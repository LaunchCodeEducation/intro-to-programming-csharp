=====================
Categories of Errors
=====================

It is useful to distinguish between categories of errors in order to quickly
identify and fix them. Each category manifests itself in a different way, and
some strategies may be more useful for certain types of errors.

Stages of C# Execution
------------------------------

In order to understand programming errors it is useful to understand the two
stages of code execution.

Complilation
^^^^^^^^^^^^^

.. index:: ! code compilation

Before code can be run, it must first be compiled, or validated and prepared for
execution. This is known as the **compilation stage**, and you can think of it like
the pre-flight check for a plane or space craft. 

A lot of detailed, low-level tasks are carried out during this process, but it
is enough for us to understand that compiling verifies the syntax and structure
of the code.

.. _error-categories:

Execution
^^^^^^^^^

Once our code has been compiled, its syntax has been verified and the program is
ready to run. The **execution stage** is when the actions written into our
program---printing to the console, prompting the user for input, making
calculations, etc.---are actually carried out. You can think of this stage as
the plane taking flight. 

Compile-Time Errors, Warnings, and Exceptions
----------------------------------------------

.. index:: syntax

C# can only execute a program if the program is syntactically correct.
**Syntax** refers to the structure of a language (spoken, programming, or
otherwise) and the rules about that structure. For example, in English, a
sentence must begin with a capital letter and end with appropriate punctuation.

When we run our code, two things can happen.  Either it works as expected, or it doesn't.  It's that simple.  One of the nice features of C# is
the compiler.  The compiler works by reading each line and performing all coded tasks.  If it finds a line that doesn't work, it will stop
the code and provide you with feedback.  
This feedback usually falls within one of three categories:  errors, warnings, or exceptions.



.. index::
   single: error; syntax

Compiler Errors
^^^^^^^^^^^^^^^^^

A **compiler error** is usually a violation of the formal rules for a given language.  
This can also be referred to as a **syntax error**.

.. admonition:: Examples

   this sentence contains a syntax error. 

   So does this one

For most readers of English, a few syntax errors are not a significant problem.
Our brains are often flexible enough to determine the intended meaning of a
sentence even if it contains one or more syntax errors.

Programming languages are not so forgiving. If there is a single syntax error anywhere in your program, 
C# will display an error message and quit *immediately*. Since syntax is validated during the compilation stage, 
syntax errors are the first we see when running a program.

During the first few weeks of your programming career, you will probably spend a lot of time tracking down syntax errors. 
However, as you gain experience, you will make fewer errors, and you will find your errors faster.

.. admonition:: Try It!

   Find the syntax errors in the program.

   .. replit:: csharp
      :linenos:
      :slug: Syntax-Errors-CSharp

      string day = Wednesday;
      Console.WriteLine(day;


.. admonition:: Question

   What syntax errors did you find? What was the specific error message provided by C# in each case?

Compiler Warnings
^^^^^^^^^^^^^^^^^^

When the compiler runs across code that is sound, but has a small flaw in either the logic or execution, it will give you a **warning**.  
Warnings, most of the time, catch small items that won't break your code at this point, but might be unused or unnecessary.  These are 
helping you prevent errors as you build.  

.. admonition:: Try It!

   Run the code.  Make changes to handle the warning.

   .. replit:: csharp
      :linenos:
      :slug: Compiler-Warning-CSharp

      string firstName = "Alyce";
      string lastName;
      Console.WriteLine(firstName);

.. index: ! exceptions

Exceptions
^^^^^^^^^^^^

**Exceptions** occur while running the program.  
They are usually the results of unanticipated errors that you didn't plan on as you built your code.
Currently, you may have seen error messages about an ``Unhandled Exception``.  
This means that something unexpected happened and crashes your code.  
This could be an unanticipated user input, trying to divide by zero, to name a few.  
C# has ways to handle exceptions, but we will discuss those more in later chapters.



Logic Errors
------------

.. index::
   single: error; logic

The last type of error is the **logic error**. If there is a logic error in your program, it will run successfully and *not* 
generate any error messages. However, the program will not work as intended.

The characteristic of logic errors is that the program you wrote is not the program you wanted. 
For example, say you want a program to calculate your daily earnings based on your weekly salary. You might try the following:

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      double weeklyPay = 600;

      double dailyEarnings = weeklyPay / 7;
      Console.WriteLine(dailyEarnings);

   **Console Output**

   ::

      85.71428571428571

The result surprises you because you thought you were making at least $100 per day (you work Monday through Friday). 
According to this program, though, you are making about $85 per day. The error is a logic one because you divided your weekly pay by 7. 
It would have been more accurate to divide your weekly pay by 5, since that is how many days a week you come to work. 

Identifying logic errors can be tricky because unlike syntax and runtime problems, there are no error messages to help us identify the issue. 
We must examine the output of the program and work backward to figure out what it is doing wrong.

Check Your Understanding
------------------------

.. admonition:: Question

   Label each of the following as either a complier error, compiler warning, unhandled expectation or logic error.

   #. Trying to use a variable that has not been defined.
   #. Leaving off a close parenthesis, ``)``, when calling ``Console.WriteLine``.
   #. Forgetting to divide by 100 when printing a percentage amount.
   #. Asking the user for their favorite number and they enter ``""`` (an empty string).


   