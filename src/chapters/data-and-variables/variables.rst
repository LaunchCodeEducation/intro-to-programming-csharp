=============
Variables   
=============

.. index:: ! variable

One of the most powerful features of a programming language is the ability to manipulate variables. 
A **variable** is a name that refers to a value. Recall that a value is a single, specific piece of data, such as a specific number or string. 
Variables allow us to store values for later use.

A useful visual analogy for how a variable works is that of a label that *points to* a piece of data. 

.. figure:: figures/variableCS.png
   :alt: A label, programmingLanguages, pointing to a the string value "C#"

   A variable can be visualized as a label pointing to a specific piece of data.

In this figure, the name ``programmingLanguage`` points to the string value ``"C#"``. This is more than an analogy, since it also is representative of how a variable and its value are stored in a computer's memory.

With this analogy in mind, let's look at how we can formally create variables in C#.

Declaring and Initializing Variables 
======================================

.. index:: 
   pair: variable; declaration

.. index:: ! declaration

To create a variable in C#, create a new name for the variable and precede it with the data type.  
In the previous section, we discussed data types.  

.. sourcecode:: csharp
    
    string programmingLanguage;

This creates a variable named ``programmingLanguage``. The act of creating a variable is referred to as **variable declaration**, or simply **declaration**.

.. index:: 
   pair: variable; assignment
   pair: variable; initialization

.. index:: ! assignment, ! initialization

Once a variable has been declared, it may be given a value using an **assignment statement**, which uses ``=`` to give a variable a value.

.. sourcecode:: csharp
   :linenos:

   string programmingLanguage;
   programmingLanguage = "C#";

The act of assigning a variable a value for the first time is called **initialization**.

The first line creates a variable that does not yet have a value. The variable is a label that does not point to any data.

.. figure:: figures/unassigned-variable.png
   :height: 250px
   :alt: The name "programmingLanguage" with no arrow connecting it to data.

   The result of ``string programmingLanguage;``

The second line assigns the variable a value, which connects the name to the given piece of data.

.. figure:: figures/variableCS.png
   :alt: A label, programmingLanguages, pointing to a the string value "C#"

   The result of ``programmingLanguage = "C#";``

It is possible to declare *and* initialize a variable with a single line of code. This is the most common way to create a variable.

.. sourcecode:: csharp

   string programmingLanguage = "C#";

.. admonition:: Warning

   It is allowed in some situations in C# to declare a variable without
   specifying a type by using the keyword ``var``, as in
   ``var x = "dog";``. In this case, C# still assigns a type to ``x``
   through inference. It looks and sees that we are assigning ``x`` the
   value ``"dog"``, which is a ``string``. Thus, ``x`` has type ``string``
   and attempting to assign ``x = 42`` will still result in a build error.

   We recommend avoiding use of ``var`` while you are learning C#. Even
   after you become more experienced with the language you will still only
   want to use it sparingly and in specific circumstances. Explicitly
   declaring the type of your variables makes for more readable code, in
   general.


To give a variable a value, use the **assignment operator**, ``=``. This operator should not be confused with the concept of *equality*, 
which expresses whether two things are the "same" (we will see later that equality uses the ``===`` operator).  
The assignment statement links a *name*, on the left-hand side of the operator, with a *value*, on the right-hand side. 
This is why you will get an error if you try to run:

.. sourcecode:: csharp

    "C#" = string programmingLanguage;

An assignment statement must have the name on the left-hand side, and the value on the right-hand side.

.. admonition:: Tip

   To avoid confusion when reading or writing code, say to yourself:

   ``programmingLanguage`` is assigned ``'C#'``

   or

   ``programmingLanguage`` gets the value ``'C#'``.

   Don't say: 
   
   ``programmingLanguage`` equals ``'C#'``.


Evaluating Variables
=====================

.. index:: variable; evaluation

After a variable has been created, it may be used later in a program anywhere a value may be used. 
For example, ``Console.WriteLine`` prints a value, we can also give ``Console.WriteLine`` a variable.

.. admonition:: Example

   These two examples have the exact same output.

   .. sourcecode:: csharp

      Console.WriteLine("Hello, World!");

   .. sourcecode:: csharp
      :linenos:

      string message = "Hello, World!";
      Console.WriteLine(message);

When we refer to a variable name, we are **evaluating** the variable. 
The effect is just as if the value of the variable is substituted for the variable name in the 
code when executed.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      string message = "What's up, Doc?";
      int n = 17;
      double pi = 3.14;
   

      Console.WriteLine(message);
      Console.WriteLine(n);
      Console.WriteLine(pi);

   **Console Output**

   ::

      What's up, Doc?
      17
      3.14

In each case, the printed result is the value of the variable. 


Reassigning Variables
======================

We use variables in a program to "remember" things, like the current score at the football game. As their name implies, 
variables can change over time, just like the scoreboard at a football game. You can assign a value to a variable, and later 
assign it a different value.

To see this, read and then run the following program in a code editor. 
You'll notice that we change the value of ``day`` three times; however, you'll also notice the data type ``string`` does not change.  

.. sourcecode:: csharp
   :linenos:

    string day = "Thursday";
    Console.WriteLine(day);

    day = "Friday";
    Console.WriteLine(day);

    day = "21";
    Console.WriteLine(day);



A great deal of programming involves asking the computer to remember things. 
For example, we might want to keep track of the number of missed calls on your phone. 
Each time another call is missed, we can arrange to update a variable so that it will always reflect the correct total of missed calls.

.. note:: We only use data type when *declaring* a variable, that is, when we create it. 
   We do NOT use the data type when reassigning the variable to a different value of the same type.  
      



Check Your Understanding
=========================

.. admonition:: Question

   What is printed when the following code executes?

   .. sourcecode:: csharp
      :linenos:

       string day = "Thursday";
       day = 32.5;
       day = 19;
       Console.WriteLine(day);

   1. Nothing is printed. A runtime error occurs.
   2. ``Thursday``
   3. ``32.5``
   4. ``19``
    

   
.. admonition:: Question   
   
   Which line is an example of variable initialization? (*Note: only one line is such an example.*)

   .. sourcecode:: csharp
      :linenos:
      
      int a;
      a = 42;
      a = a + 3;

   1. Line 1
   2. Line 2
   3. Line 3
   4. None of the above
