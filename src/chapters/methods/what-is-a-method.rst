Introduction
=============

Up until now, you have been able to write programs that function within the main method using a variety of 
data types and collection types along with specific collection methods.  These methods are built into the C# language.
You call them and they do their task.  You chain them and they do that task in combination with other methods.  Think of all the time
that a method like ``ToUpper`` or ``IndexOf`` saved you from having to code yourself.  Not only that, but you can call 
either of those methods over and over and not have to worry about *if* they will work.  Those methods are designed to work with 
any code as long as it is the correct data type.  The other nice thing about methods is that they will only run when you call them.
When you run your code you don't have to worry about a renegade ``ToLower`` converting all your string outputs to lowercase *unless* 
you consciously call that method.  

Some benefits of methods: 

#. Methods are **reusable**, keeping your code nice and DRY.
#. Methods only run when **called**.
#. Methods are completely **customizable**.

As we move deeper in the C# language, you will begin to use methods more and more.  This chapter is designed to introduce you to 
method signatures, method calls, and overall usage of methods within your code.  A **method signature** is the structure of the method, 
including accessability, data type, parameters, and return type if applicable.  A **method call** is how you call your method based on its
signature.  

A little caveat before we continue.  Our current experience with C# is a little limited at this point, so our methods will be limited in 
functionality and usage.  The purpose of this chapter is to provide you with exposure to the basics of a method so that when we begin to 
learn about classes and creating objects, you will be familair with the idea methods so that you can focus more on the nuances of classes
which include methods.  As we progress into classes, you will see how powerful methods can be.  Please take this chapter as a chance to 
become familar with the concepts of methods so that you can build amazing code later.



What is a Method?
---------------------

.. index:: ! method

A **method** is a reusable, callable piece of code. Methods are created to perform a single task or action.

You have been using methods throughout your learning so far, without receiving a full explanation of how methods work. 

You have already become familiar with several functions:

- ``Console.WriteLine``
- The type conversion methods: ``Int32.Parse``,  ``ToString`` or even ``GetType``
- String and array methods, such as ``IndexOf`` or ``Join``

Each of the methods we have used works in the same way. By typing the methods's name, followed by parentheses, we can *call* the method, resulting in an action being carried out. 
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
