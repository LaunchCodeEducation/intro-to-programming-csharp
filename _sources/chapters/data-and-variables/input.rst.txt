.. _readline-sync:

Input with ``ReadLine``
=============================

``Console.WriteLine`` works fine for printing static (unchanging) messages to the
screen. If we wanted to print a phrase greeting a specific user, then
``Console.WriteLine("Hello, Dave.");`` would be OK as long as Dave is the actual
user.

What if we want to greet someone else? We could change the string inside the
``()`` to be ``'Hello, Sarah'`` or ``'Hello, Elastigirl'`` or any other name we
need. However, this is inefficient. Also, what if we do not know the name of
the user beforehand? We need to make our code more general and able to respond
to different conditions.

It would be great if we could ask the user to enter a name, store that string
in a variable, and then print a personalized greeting using ``Console.WriteLine``.
Variables to the rescue!

Requesting Data
----------------

.. index:: ! input

.. index:: ! prompt

To personalize the greeting, we have to get **input** from the user. This
involves displaying a **prompt** on the screen (e.g. "Please enter a number:
"), and then waiting for the user to respond. Whatever information the user
enters gets stored for later use.

As we saw earlier, each programming language has its own way of accomplishing
the same task. For example, the Python syntax is ``input("Please enter your
name: ")``.

C# has a built-in module for collecting data from the user, called
``Console.ReadLine``. 

Syntax
-------

Gathering input from the user requires the following setup:

.. sourcecode:: csharp
   :linenos:

   Console.WriteLine("Enter your name");

   string name = Console.ReadLine();

   Console.WriteLine("Your name is " + name);

There is a lot going on here behind the scenes, but for now you should follow
this bit of wisdom:

   I turn the key, and it goes.

Most of us do not need to know all the details about how cars, phones, or
microwave ovens work. We just know enough to interact with them in our day to
day lives. Similarly, we do not need to understand how ``ReadLine`` works
at this time. We just need to know enough to collect information from a user.

As you move through the course, you WILL learn about all of the pieces that fit
together to make this process work. For now, here is a brief overview.

How to Prompt the User
^^^^^^^^^^^^^^^^^^^^^^^

In order to collect data from a user, you have to provide directions to ensure that the correct data is entered.
This means we have to prompt the user.

To display a prompt and wait for a response, we use the following syntax:

.. sourcecode:: csharp
   :linenos:

   Console.WriteLine("Question here...");

   string input = Console.ReadLine();



When C# evaluates the expression, it follows the instructions:

#. Display ``Question text`` on the screen.  
#. Wait for the user to respond. 
#. Store the data in the variable ``input``.

For our greeting program, we would code ``Console.WriteLine("What is your name?");``.  
This prints the question for the user.  We follow this question with ``string name = Console.ReadLine()``. 
In the console, you will notice the cursor blinking in the line below.  This is where the user enters a name and
presses the Return or Enter key. When this happens, any text entered is
collected by the ReadLine function and stored in ``name``.

.. admonition:: Try It

   Let's play around with the ``input`` statement. Open the repl.it link below
   and click the "Run" button.

   .. replit:: csharp
      :slug: CSharpInputExamples01
      :linenos:

      Console.WriteLine("Enter your name: ");
      string name = Console.ReadLine();


Note that after entering a name, the program does not actually DO anything with
the information. If we want to print the data as part of a message, we need to
put ``name`` inside a ``Console.WriteLine`` statement.

After line 3, add ``Console.WriteLine("Hello, " + name + "!");``, then run the
code several times, trying different responses to the input prompt.

By storing the user's name inside ``name``, we gain the ability to hold onto
the data and use it when and where we see fit.

Try adding another ``+ name`` term inside the ``Console.WriteLine`` statement and see
what happens. Next, add code to prompt the user for a second name. Store the
response in ``otherName``, then print both names using ``Console.WriteLine``.

.. admonition:: Try It

   Update your code to request a user's first and last name, then print an
   output that looks like:

   ::

      First name: Elite
      Last name: Coder
      Last, First: Coder, Elite

Critical Input Detail
----------------------

There is one very important quirk about the input function that we need to
remember. Given ``Console.WriteLine(7 + 2);``, the output would be ``9``.

Now explore the following code, which prompts the user for two numbers and then
prints their sum:

.. replit:: csharp
   :slug: CSharpInputExamples02
   :linenos:

   Console.WriteLine("Enter a number");
   string num1 = Console.ReadLine();


   Console.WriteLine("Enter a number");
   string num2 = Console.ReadLine();


   Console.WriteLine(num1 + num2);

Run the program, enter your choice of numbers, and examine the output. Do you
see what you expected?

If we enter ``7`` and ``2``, we expect an output of ``9``.  We do NOT expect
``72``, but that is the result printed. What gives?!?!?

The quirk with the ``ReadLine`` method is that it *treats all entries as
strings*, so numbers get concatenated rather than added.  Just like
"Hello, " + "World" outputs as ``Hello, World``, "7" + "2" outputs as ``72``.

   In C#, ReadLine entries must be strings!

If we want our program to perform math on the entered numbers, we must recast its type.

.. admonition:: Try It

   #. In line 3, Initialize a new int variable to hold your type conversion of num1.
   #. To convert num1 into your new int varialbe, use ``Int32.Parse()``.
   #. Run the program and examine the result.
   #. Repeat step 2 for ``num2`` starting in line 7.
   #. What happens if a user enters ``Hi`` instead of a number?
   #. If you want to work with doubles try it again using ``Double.Parse()``


Check Your Understanding
------------------------

.. admonition:: Question

   What is printed when the following program runs?

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine("Please enter your age: ");
      string input = Console.ReadLine();

      //The user enters 25.

      Console.WriteLine(input);

   #. ``System.String``
   #. ``System.Number``
   #. ``System.Int32``
   #. ``"25"``

.. admonition:: Question

   What is printed when the following program runs?

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine("Please enter your age: ");
      string input = Console.ReadLine();
      int ageNum = Int32.Parse(input);

      //The user enters 25

      Console.WriteLine(ageNum.GetType());

   #. ``System.String``
   #. ``System.Number``
   #. ``System.Int32``
   #. ``25``
