Introduction
=============

Up until now, you have been able to write programs that function within the Main method using a variety of 
data types and collection types along with specific collection methods.  These methods are built into the C# language.
You call them and they do their task.  

As we move deeper in the C# language, you will begin to use methods more and more.  This chapter is designed to introduce you to 
**method signatures**, **method calls**, and the ability to create your own unique methods.  A method signature is the structure of the method, 
including accessability, data type, parameters, and return type if applicable.  A method call, or invocation, is how you call your method based on its
signature.  

A little caveat before we continue.  Since we have not encountered C# classes at this point, we will be working with **static** methods.
Static methods are able to ``return`` a **value** or print directly into the console, but they do not create anything **new**.
Methods that create new instances of objects are called **instance methods**, we will learn about them soon.  

What is a Method?
---------------------

.. index:: ! method

A **method** is a reusable, callable, and customizable piece of code. Methods are created to perform a single task or action.

You have been using methods throughout your learning so far, without receiving a full explanation of how methods work. 

You have already become familiar with several functions:

- ``Console.WriteLine``
- The type conversion methods: ``Int32.Parse``,  ``ToString`` or even ``GetType``
- Collection methods, such as ``IndexOf``,  ``Join``, ``Add``

Each of the methods we have used works in the same way. By typing the methods's name, followed by parentheses, 
we can *call* the method, resulting in an action being carried out. 
Sometimes, as with ``Console.WriteLine``, we can provide input data between the parentheses, which the method will use to carry out its action.

.. admonition:: Example

   The function ``Console.WriteLine`` prints the provided value or values (the input data).

   .. sourcecode:: csharp

      Console.WriteLine("Hello, World!");

   **Console Output**

   ::

      Hello, World!

This is an example of a method receiving *input*. Methods may also provide
*output*. For example, the type conversion methods give back the result of
converting a value.

.. admonition:: Example

   Type conversion methods *return* a value, that can be used by the calling code. Often, we store the return value of a method in a variable.

   .. sourcecode:: csharp
      :linenos:
      
      int num = Int32.Parse("42");
      Console.WriteLine(num + 12);

   **Console Output**

   ::

      54


.. index:: encapsulation

Methods are extremely powerful. They allow us to repeat actions without repeating each individual step of code that the actions are built from. 
By grouping actions together, methods allow us to be removed from the details of what they are actually doing.

When we want to print a message to the console using ``Console.WriteLine``, we don't have to know what the console is, or how a string can be displayed on it. 
The behavior is wrapped up within the method itself. This is an example of a broader programming concept known as **encapsulation**. 
Encapsulation is the process of packaging up code in a reusable way, without the programmer needing to be concerned with how it works.

.. index::
   single: function; machine

.. _function-machine:

One analogy for describing the concept of a method is that of a factory that takes input, carries out an action, and gives back a result. 
Each line of code is like one step on an assembly line.  Data enters, is manipulated by the code in the method producing a unique result.

.. figure:: figures/function-machine.png
   :alt: A "method factory," consisting of a box which takes inputs, and from which output emerges.

   The method factory

If we want to use a method, we must provide it with some input. It carries
out an action on that input and returns a result. The action occurs within the
method, or "inside the factory". If we know the purpose of a method, we
simply provide it with input and receive the output. The rest is up to the
factory itself.

Methods also allow us to keep our code DRY, a concept that you learned about :ref:`when we introduced loops <dry-code>`. If we want to do the same basic task 17 times across a program, we can reduce code repetition by writing one method and calling it 17 times.

Check Your Understanding
------------------------

.. admonition:: Question

   In your own words, explain what a method is.
