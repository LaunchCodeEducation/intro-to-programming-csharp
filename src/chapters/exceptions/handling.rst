.. index:: ! checked exception, ! unchecked exception

Handling Exceptions
===================

When you include exceptions in your C# programs, you must decide what should take place once one is thrown. Some 
languages, like Java, require exceptions to be handled at the time of compiling. These are **checked exceptions**. When an exception is 
not handled in compiling, it is passed to runtime and called an **unchecked exception**. All exceptions in C# 
are unchecked. Therefore it is up to you, the programmer, to decide what to do to handle one when the need arises 
in runtime.

Here's some advice to consider when contemplating when to handle an exception. This comes from Karl Seguin's 
`Foundations of Programming <https://www.openmymind.net/FoundationsOfProgramming.pdf>`__.

#. Only handle exceptions that you can actually do something about.
#. You can't do anything about the vast majority of exceptions.

For example, if your code cannot connect to a database, there is probably nothing your program can 
do about it. However, as we allude to on the previous page, if you receive invalid input from a user, you can still throw an 
exception and re-prompt them to refine their input with an error message to help them get it right the next time.

.. index:: ! try, ! catch, ! finally

Try/Catch/Finally
-----------------

To handle exceptions in C#, we use the **try/catch/finally** construction. This functions very similarly 
to exception handling tooling in other languages. If you expect that a method might return an exception, the method call should 
be wrapped in a ``try`` statement. This could be because you threw the exception in the method yourself. Or you are in one of 
the common exception scenarios we outlined on the previous page.

If the code runs without throwing an exception, then the program continues as usual. However, if the ``try`` block results in an 
exception, then a later ``catch`` statement will be called. ``catch`` gives the program instructions on what to do in the 
event of an exception. The ``catch`` block prevents the program from stopping when it reaches the exception. 

.. _temp-argument-exception:

Here's how we can update our Temperature constructor with a ``try/catch`` to handle the exception:

.. sourcecode:: c#
   :lineno-start: 8

   public Temperature(double fahrenheit)
   {
      try
      {
         if (fahrenheit < absoluteZero)
         {
            throw new ArgumentOutOfRangeException("Value is below absolute zero");
         }
         else
         {
            Console.WriteLine(fahrenheit);
         }
      }
      catch(ArgumentOutOfRangeException e)
      {
         fahrenheit = absoluteZero;
         Console.WriteLine(e);
      }
   }

First the constructor method comapres the ``fahrenheit`` input to ``absoluteZeroFahrenheit``.
If the ``fahrenheit`` is greater than absolute zero, the code runs without any exception.
We tried the value and it passed so we can keep the code running. 

If the action inside the ``try`` block results in an exception, i.e. the ``userTemp`` value is below absolute zero, 
the catch block is triggered.  
In this example, the catch block will reassign the inital value of fahrenheit to that of absolute zero.  
This particular catch block is activated because we set it to the ``ArgumentOutOfRangeException``.

We assigned the ``ArgumentOutOfRangeException`` a variable of ``e`` in **Line 21**.  
In **Line 23**, the value of ``fahrenheit`` is being reassigned to ``absoluteZero``.  
In **Line 24**, we are print the updated value via ``e``.  
This provides feedback to the user about the error by displaying the exception or it's message in the view of your
running app. It also an option to rethrow an exception after it has been caught. You won't need to rethrow 
exceptions in this course, but just know that it can be done. 

Now, running the same sample input from the previous page does not output an exception:

.. admonition:: Example

   *Input:*

   .. sourcecode:: c#
      :linenos:

      //Test 1: userTemp = 73
      Temperature insideTemp = new Temperature(userTemp);

      //Test 2: userTemp = -8200
      Temperature outsideTemp = new Temperature(UserTemp);

   *Output:*

   :: 

      You entered 73 degrees F.
      -459.67

Although the exception has still been thrown, the ``try/catch`` construction diverts the program from
terminating when it's met.

Some ``try/catch`` blocks can also contain a ``finally`` statement that will run whether or not an 
exception was thrown. In this example, perhaps we want to communicate that if a Fahrenheit value is 
passed into the constructor that is less than absolute zero, then the ``fahrenheit`` input will be 
set to absolute zero.

.. sourcecode:: c#
   :lineno-start: 6

   class Program
   {
      public Temperature(double fahrenheit)
      {
         try
         {
            if (fahrenheit < absoluteZero)
            {
               throw new ArgumentOutOfRangeException("Value is below absolute zero");
            }
            else
            {
               Console.WriteLine("You entered " + fahrenheit + " degrees F.");
            }
         }
         catch(ArgumentOutOfRangeException e)
         {
            fahrenheit = absoluteZero;
            Console.WriteLine(e)
         }
         finally
         {
            Console.WriteLine("Fahrenheit cannot be less than -459.67.");
         }
      }
   }

This ``finally`` statement is a tad redundant, since presumably a user will know this before trying 
to set the value. A more likely scenario to use a ``finally`` block might be in connecting to a database
or other external service. For example, if a connection is opened within a try block and an exception is 
still caught, we'll want to close the connection no matter what happens next. 

.. index:: ! exception swallowing

What to Catch
^^^^^^^^^^^^^

When working with a ``try/catch`` statement, in statically-type languages like C#, you can declare the type of exception you wish to catch.  
Due to the `four basic principles <https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/intro-to-csharp/object-oriented-programming>`_ of object oriented programming (will explore this in the next lesson), we have to be aware that catching the base ``System.Exception`` type will result in *all* exceptions being caught. 
This is not advised. Be specific about the types of exceptions you want to catch, as we have in the example above.
We will look at a few common exceptions in the next section.

If you have reason to believe that a given method may return an exception but you are unsure which type exactly, ``try/catch`` 
can --- and should --- include more than one ``catch`` block. Rather than catching one abstract exception type, you want to 
attempt to catch the exception with specificity so that the resulting decisions are meaningful. It is also important to note 
that order matters when it comes to catching. If the thrown exception matches the first ``catch`` block, then that block executes 
and any remaining ``catch`` blocks are ignored. If that exception thrown doesn't match the first ``catch`` argument, then it goes on 
to the next statement to check for a type match.

Catching the base class ``Exception`` -- that is, all exceptions -- is sometimes referred to as **exception swallowing**. 
In these cases, exceptions are simply absorbed and not re-thrown or logged. If your program has a bug, or reaches an 
undesirable state, you want to know about it! Don't swallow exceptions.


How to Avoid Exceptions
-----------------------

For some types of exceptions, there's little you can do. If a database goes down, it's down. However, many situations that 
result in exceptions are avoidable.

Validate User Input
^^^^^^^^^^^^^^^^^^^

Validate user input to ensure that it is of the type your code expects, and satisfies any other implicit constraints 
(such as numeric input falling within a certain range).

If you're working within a framework such as ASP.NET, use the built-in validation capabilities to make this easier. We'll cover 
these in detail when we discuss model validation.

Perhaps the most important thing to keep in mind here is that you should never assume that input given to your program is safe 
and valid. This is the case even when you're providing browser-based validation. Clever (or malicious) users can bypass most 
forms of client-side validation.

.. index:: ! null

Check For ``null`` References
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In C#, ``null`` is a keyword that represents a **null reference**.  
A null reference is a reference to nothing, but not like an empty string or a value of zero.
For example, a string variable can be set to ``null``, but is not the same as an empty string.

.. admonition:: Example

   .. sourcecode:: csharp

      string n = null;
      string e = ""; 
      Console.WriteLine(n == e);

   **Output**

   ::

      False

Think of it as a placeholder for values or where values should be once a method runs, or a field is initialized, etc.
Often you will see ``null`` values when working with databases.  


You will see working examples of ``null`` when we learn more about Visual Studio and debugging (watch the autos and locals windows).
You may read more on ``null`` and null references `here <https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/null>`_.

If your code depends on an input parameter not being ``null`` to work properly, and it's possible to gracefully handle the 
situation -- for example, by re-prompting the user -- then you should do so.

As with exceptions above, if there is no way to reasonably recover from a ``null`` pointer, then you shouldn't swallow it. 
Furthermore, it's generally a bad idea to catch a ``null`` pointer exception (``NullReferenceException`` in C#). 
`Read more <https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/exceptions/creating-and-throwing-exceptions>`_ on why this is the case.


Check Your Understanding
------------------------

.. admonition:: Question

   Select an anomalous event when you may choose to not ``catch`` a thrown exception.

   #. None. All exceptions should be handled with ``catch``.
   #. A database responsible for providing all of the image data on your site cannot be reached.
   #. A user inputs string data into a form designed to handle integers.
   #. It's the bottom of the ninth and you just want the game to be over.

.. ans: b, A database responsible for providing all of the image data on your site cannot be reached.

.. admonition:: Question

   True/False: Exception swallowing is a good choice to ensure no exceptions break your code.

   #. True
   #. False

.. ans: False, Exceptions carry important information and catching all of them blinds us to potentially
   unhealthy behavior
