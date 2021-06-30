===================
More On Variables
===================

The previous section covered creating, evaluating, and reassigning variables.
This section will cover some additional, more nuanced topics related to
variables.

Creating Constants With ``const``
---------------------------------

One of the key features of variables that we have discussed so far is their
ability to change value. We can create a variable with one value, and then
reassign it to another value.

.. sourcecode:: csharp
   :linenos:

   string programmingLanguage = "C#";
   programmingLanguage = "JavaScript";

In some situations, we want to create variables that cannot change value. Many
programming languages, including C#, provide mechanisms for programmers
to make variables that are constant.

For example, suppose that we are writing a to-do list web application, named
"Get It Done!" The title of the application might appear in multiple places,
such as the title bar and the main page header.

.. figure:: figures/get-it-done.png
   :alt: A to-do list web application with application name in the title bar and main header.
   :height: 300px

   An example to-do list web application

We might store the name of our application in a variable so that it can be
referenced anywhere we want to display the application name.

.. sourcecode:: csharp

   string appName = "Get It Done!";

This allows us to simply refer to the ``appName`` variable any time we want to
use it throughout our application. If we change the name of the application, we
only have to change one line of code, where the ``appName`` variable is
initialized.

One problem with this approach is that an unwitting programmer might change the
value of ``appName`` later in the code, leading to inconsistent references to
the application name. In other words, the title bar and main page header could
reference different names.

.. index:: ! const, ! constant

.. index::
   pair: variable; constant

Using ``const`` along with the data type to create a variable ensures that the value
of the declared variable cannot be changed.

.. sourcecode:: csharp

   const string appName = "Get It Done!";

Such an unchangeable variable is known as a **constant**, since its value is
just that.

How does C# prevent a programmer from changing the value of a constant?
Let's find out. Try running the following code in an editor. What happens?

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      const string appName = "Get It Done";
      appName = "Best TODO application Ever!";

   **Console Output**

   ::

      error CS0128: A local variable named `appName' is already defined in this scope

As we've seen with other examples---such as trying to declare a variable twice,
using incorrect syntax, or failing to enclose strings in quotes---C#
prevents undesired code from executing by throwing an error.




Naming Variables
----------------

Valid Variable Names
^^^^^^^^^^^^^^^^^^^^

As you may have discovered already, not just any sequence of characters is a
valid variable name. For example, if we try to declare a variable with a name
containing a space, C# complains.

.. admonition:: Example

   .. sourcecode:: csharp

      string application name;

   **Console Output**

   ::

      error CS1525: Unexpected symbol `name', expecting `,', `;', or `=

In this case, the complier didn't know what to do with the space, so the error
message is saying that the variable name is not valid, or is "unexpected".  

C# provides a narrow `set of rules <https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/naming-guidelines>`_  
for naming variables. Here are a few easy-to-remember guidelines:

.. index:: keywords

****

#. Use only the characters 0-9, a-z, A-Z, and underscore. In other words, do
   not use special characters or whitespace (space, tab, and so on).
#. Do not start a variable name with a number.
#. Avoid starting a variable name with an underscore. Doing so is a convention
   used by some C# developers to mean something very specific about the
   variable, and should be avoided.
#. Do not use **keywords**, which are words reserved by C# for use by
   the language itself. We'll discuss these in detail in a moment.

Following these guidelines will prevent you from creating illegal variable
names. While this is important, we should also strive to create good variable
names.

Good Variable Names
^^^^^^^^^^^^^^^^^^^

Writing good code is about more than writing code that simply works and
accomplishes the task at-hand. It is also about writing code that can be read,
updated, and maintained as easily as possible. How to write code that achieves
these goals is a theme we will return to again and again.

One of the primary ways that code can be written poorly is by using bad
variable names. For example, consider the following program. While we haven't
introduced each of the components used here, you should be able to come to a
general understanding of the new components.

.. sourcecode:: csharp
   :linenos:

   double x = 5.75;
   const double y = 3.14;
   double z = y * Math.Pow(x, 2);
   Console.WriteLine(z);

Understanding what this program is trying to do is not obvious, to say the
least. The main problem is that the variable names ``x``, ``y``, and ``z`` are
not descriptive. They don't tell us anything about what they represent, or how
they will be used.



.. pull-quote:: Variable names should be descriptive, providing context about the data they contain and how they will be used.

Let's look at an improved version of this program.

.. sourcecode:: csharp
   :linenos:

   double radiusOfCircle = 5.75;
   const double pi = 3.14;
   double areaOfCircle = pi * Math.Pow(radiusOfCircle, 2);
   Console.WriteLine(areaOfCircle);

With improved variable names, it now becomes clear that the program is calculating the area of a circle of radius 5.75.

.. tip:: When considering program readability, think about whether or not your code will make sense to another programmer. It is not enough for code to be readable by only the programmer that originally wrote it.

Camel Case Variable Names
^^^^^^^^^^^^^^^^^^^^^^^^^

.. index:: ! lower camel case, ! camel case

.. index::
   pair: variable; naming conventions

There is one more aspect of naming variables that you should be aware of, and that is conventions used by professional programmers. 
Conventions are not formal rules, but are informal practices adopted by a group.

.. admonition:: Example

   In the United States, it is common for two people to greet each other with a handshake. In other countries and cultures, such as some in east Asia, the conventional greeting is to bow.

   Failing to follow a social convention is not a violation of the law, but is considered impolite nonetheless. It is a signal that you are not part of the group, or do not respect its norms.

There are a variety of types of conventions used by different groups of programmers. 
One common type of convention is that programmers that specialize in a specific language will adopt certain variable naming practices.

In C#, most programmers use the **camel case** style, which stipulates that variable names consist of names or phrases that:

- are joined together to omit spaces,
- start with a lowercase letter, and
- capitalize each internal word.

In the example from the previous section, the descriptor "area of circle" became the variable name ``areaOfCircle``. 
This convention is called camel case because the capitalization of internal words is reminiscent of a camel's humps. 
Another common name for this convention is **lower camel case**, since names start with a lowercase letter.

.. note:: Different programming languages often have different variable-naming conventions. For example, in Python the convention is to use all lowercase letters and separate words with underscores, as in ``area_of_circle``.

We will use the `lower camel case convention <https://en.wikipedia.org/wiki/Camel_case>`_ throughout this course, and strongly encourage you to do so as well.

Keywords
--------

.. index:: ! keywords, ! reserved words

Our last note on naming variables has to do with a collection of words that are reserved for use by the C# language itself. 
Such words are called **keywords**, or **reserved words**.

Any word that is formally part of the C# language syntax is a keyword. 
So far, we have seen only a few keywords: ``const``, ``var``, and any of the data type words.

.. warning:: While ``Console`` and ``Console.WriteLine`` may seem like keywords, they are actually slightly different things. They are entities (an system and a method, respectively) that are available by default in most C# environments.

Attempting to use a keyword for anything other than it's intended use will result in an error. 
To see this, let's try to name a variable ``const``.

.. admonition:: Example

   .. sourcecode:: csharp

      int const;

   **Console Output**

   ::

      error CS1525: Unexpected symbol `const'

.. tip:: Most code editors will highlight keywords in a different color than variables or other parts of your code. This serves as a visual cue that a given word is a keyword, and can help prevent mistakes.

We will not provide the full list of keywords at this time, but rather point them out as we learn about each of them. 
If you are curious, the `full list is available at Microsoft Documentation <https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/>`_.

Check Your Understanding
------------------------

.. admonition:: Question

   Which is the best keyword to use when you want ot keep the value of a variable fixed?

   #. ``var``
   #. ``let``
   #. ``const``

.. answer: c. const
