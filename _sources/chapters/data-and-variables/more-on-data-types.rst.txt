======================
More On Data Types
======================

.. index:: ! data type, ! type 

Static vs. Dynamic Typing
-------------------------

.. index:: ! dynamically typed, ! statically typed

In a **dynamically typed** programming language (like JavaScript or Python), a
variable can refer to a value of *any* data type (string, number,
object, etc.) at *any* time. When the variable is used, the interpreter figures
out what type it is and behaves accordingly.

C# is a **statically typed** language. When a variable is
declared in a statically typed language, the data type for the value must be
specified. Once the declaration is made, the variable cannot refer
to a value of any other type.

For example, this is legal in JavaScript, a dynamically typed language:

.. admonition:: Example

   .. sourcecode:: JavaScript
      :linenos:

      let dynamicVariable = "dog";
      console.log(typeof(dynamicVariable));
      dynamicVariable = 42;
      console.log(typeof(dynamicVariable));

   **Output**

   .. sourcecode:: bash

      string
      number

After line 1 executes, ``dynamicVariable`` holds a ``string`` data type. After
line 3 runs, ``dynamicVariable`` is reassigned to a ``number`` type. ``dynamicVariable``
is allowed to hold values of different types, which can be reassigned as
needed when the program runs.  The keyword ``typeof`` is used in lines 2 and 4 
to verify the data type.

However, the corresponding code in C# will result in a build error:

.. admonition:: Example

   .. sourcecode:: c#
      :linenos:

      string staticVariable = "dog";
      staticVariable = 42;

   **Output**

   .. sourcecode:: bash

      Error CS0029: Cannot implicitly convert type 'int' to 'string' 

The compiler error occurs when we try to assign ``42`` to a variable of type
``string``.

Take-home lesson: *We must declare the type of every variable in
a statically typed language*. This is done by declaring the data type for the
variable or parameter BEFORE its name, as we did in the example above:
``string staticVariable = "dog"``.

.. admonition:: Note

   We only need to specify the type of a variable when declaring
   it. Further use of the variable does not require us to identify
   its type. Doing so will result in an error.


.. index:: ! type system

Dynamic and static typing are examples of different `type
systems <https://en.wikipedia.org/wiki/Type_system>`__. The **type system** of
a programming language is one of the most important high-level characteristics
that programmers use when discussing the differences between languages. Here
are a few examples of popular languages falling into these two categories:

#. **Dynamic**: Python, Ruby, JavaScript, PHP
#. **Static**: C#, C, C++, Java, TypeScript

Because we need to give plenty of attention to types when writing C# code,
let’s begin by exploring the most common data types in this language.

Built-In Types
--------------

In C#, all of the basic data types are objects --- we'll get into this idea shortly. 
Though the so-called built-in data types also have short names that differ from typical class name
conventions.

We provide here a list of some of the most common types, along with the official .NET class name. 
The .NET gives us a class library with object types, which we will learn about later. 
We’ll generally prefer to use the short names for each of these.

.. list-table:: Some Built-In Types in C#
   :header-rows: 1

   * - Short name
     - .NET Class
     - Examples
     - Notes 
   * - ``int``  
     - ``Int32``
     - -5, 1024 
     -
   * - ``double``
     - ``Double``
     - 3.14159, 2.0
     - Doubles are twice as precise and can use decimals. 
   * - ``char``
     - ``Char``
     - ‘a’, ‘!’ 
     - A single Unicode character. Must be enclosed in *single* quotes ``''`` to be a character.
   * - ``bool``
     - ``Boolean``
     - ``true``, ``false``
     -
   * - ``string``
     - ``String``
     - ``"Hello, World!"``, ``"Tuesday"``, ``"17"``
     - Reference value.  Non-Primitive Type.  Must be enclosed in *double* quotes ``"..."`` to be a string.  Immutable. 


Not all built-in data types in C# are listed here, only the most
commonly used types that beginners are likely to encounter. If you’re
curious, `read more about built-in types in
C# <https://msdn.microsoft.com/en-us/library/ya5y69ds.aspx>`__.

.. note:: 
   Having distinctions between integers and doubles can help with code design.
   For example, an inventory-tracking program stores items and the number of each number in stock. Since a store cannot have 3.5 shirts in stock, the programmer makes the quantity of each item integer values as opposed to doubles.



.. index:: ! primitive type

Primitive Types
^^^^^^^^^^^^^^^

The types in the table above are known as **primitive types**. A primitive data type is a basic 
building block of a programming language. Using primitive data types, we
can build more complex data structures.

Non-primitive Types
^^^^^^^^^^^^^^^^^^^

Primitive data types are *immutable* and can be combined to build larger data
structures. One example is forming the ``string`` "LaunchCode" from multiple
``char`` characters (``'L'``, ``'a'``, ``'u'``, etc.).

``string`` is another built-in type in C# and it is also a non-primitive data type. We'll delve into 
how strings work in C# in a future chapter.



.. index:: ! reference type ! value type

.. _reference-variable:

Reference and Value Types
-------------------------

We can group types in C# into two categories: **value types** and
**reference types**. Variables holding value types *directly* contain
their data, and include numeric types (``int``, ``double``, etc.),
``bool``, and a handful of others that we won’t encounter in this
course. The primitive, built-in types we list above are all value types.  
Whereas reference types stores the *address* where the value is being stored. 
Another way to think about this is that a reference type *points* to the 
memory location that stores the data.

.. index:: ! class


Boxing
^^^^^^

As we mention above, all types in C# are treated as objects. Even value types. 
This can be accomplished through processes called boxing and unboxing. 
Converting from a value type to a reference type is called **boxing**, and the reverse process 
(reference to value) is called **unboxing**. C# is known as a unified 
type system because it implicitly boxes values types to be treated as objects. 

.. sourcecode:: c#

   int i = 123;     // This is a value type.
   object o = i;    // Boxing the value type into a reference type.
   int j = (int)o;  // Unboxing the reference type back into a value type.

Check Your Understanding
-------------------------

.. admonition:: Question

   Which of the following is NOT a number data type in C#:

   #. ``number``
   #. ``int``
   #. ``float``
   #. ``double``

.. ans: a, ``number``

.. admonition:: Question

   Which of the following terms refers to C#'s behavior of treating all types as objects:

   #. static type system
   #. dynamic type system
   #. reference type system
   #. unified type system

.. ans: d, unified type system
