Unit Testing In Action With MSTest
====================================

Testing is a bit of an art; there are no hard and 
fast rules about how to write good tests.
That said, there are some general principles that you should follow.  
In this section, we will explore some of these. 

In particular, we will focus on identifying good **test cases** 
by working through a specific example.
We will start with a very simple example which will allow us to 
explore formatting, positive/negative tests, edge cases, 
then create a larger project using multiple tests.

**MSTest** is a framework that provides the methods and assertions 
for writing and executing unit tests in C#. 

What To Test
---------------

When writing tests for your code, what should you test?
You can't test *every* possible situation or input.  
But you also don't want to leave out important cases.  
A method or program that isn't well-tested might have bugs 
lurking beneath the surface. 

.. admonition:: Note

   Since we are also focused on *unit* testing, in this chapter we will 
   generally use the term "unit" to refer to the method or program under consideration

Regardless of the situation, there are three types of test cases you should 
consider: positive, negative and edge cases.

#. A **positive test** verifies expected behavior with valid database
#. A **negative test** verifies expected behavior with *invalid* data.
#. An **edge case** is a subset of positive tests, which checks the 
   extreme edges of valid values.

.. admonition:: example

   Suppose we were creating an app that focused on cars.  
   We could write tests for certain aspects, number of doors or wheels, 
   average milaage, size of gas tank, etc.

   Let's look at the engine temperature indicator light.  
   If your engine temperature is above 220 degrees or higher, 
   then a light turns on to notify the driver.
   We want to test that the light will turn on, so we can set the 
   following values for testing:
   
   #. Positive test values: ``221`` and ``280``
   #. Negative test values: ``-1`` and ``200``
   #. Edge case value: ``220``


Considering positive, negative, and edge tests will go a long way 
toward helping you create well-tested code.
Planning out your tests will save you time writing them.  
Just like with any code, testing has its own syntax.  

.. _csharp-attributes:

.. index:: ! TestClass, ! TestMethod

C# Attributes
-------------

.. index:: ! attributes

In C#, **attributes** are formalized bits of information about a program. 
They operate somewhere between actual code syntax and a comment on the code. 
Attributes do not directly affect the code they annotate, but they do supply 
information to the compiler.
An attribute is enclosed in square brackets, ``[]``, and placed above the item it decorates. 

To run unit tests using the native tools available in Visual Studio, 
the attributes **[TestClass]** and **[TestMethod]** are used to 
indicate that certain classes and methods should be treated as test cases. 
We describe how to use these in the examples that follow.

Testing Setup
-------------

.. index:: ! dependency

To test a simple .NET Core console project, we add an MSTest 
project into the same solution. An MSTest 
project is a console project with an added MSTest dependency.


Fork and clone `this repo <https://github.com/LaunchCodeEducation/csharp-web-dev-lsn5unittesting>`__. 
Inside the solution, we have two projects, ``Car`` and ``CarTests``. 
The ``Car`` project is a simple .NET Console app like the others you have encountered
in this course so far. ``CarTests`` is a new type of project, MSTest Project. 

On a Mac, to select this type of project looks like so:

.. figure:: ./figures/mac-create-mstest-project.png
   :alt: MAC: User selects MSTest project template in Visual Studio

   MAC: Creating MSTest project in Visual Studio

On a Windows:

.. figure:: ./figures/windows-create-mstest-project.png
   :alt: WINDOWS: User selects MSTest project template in Visual Studio

   WINDOWS: Creating MSTest project in Visual Studio

MSTest is a C# testing framework. When we create a Visual Studio MSTest Project, the 
necessary API and classes are added as **dependencies** of the ``CarTests`` project. 
A dependency is a separately developed program or piece of code that another 
program or piece of code uses to carry out its function. 
Our C# tests will *depend* on MSTest code. 

Along the same lines, since ``CarTests`` tests the methods 
inside of ``Car``, we must add the ``Car`` project as a dependency of ``CarTests``.

Right click on the ``Dependencies`` directory in ``CarTests`` and add a reference to 
the ``Car`` project.

.. figure:: ./figures/vs-add-dependency-reference.png
   :alt: User selects project to add as a dependency reference to test project

   Add main project as dependency for test project

``Car`` and ``CarTests``
^^^^^^^^^^^^^^^^^^^^^^^^

Open the ``Car`` class and look around. Here, we provide a class, ``Car``, with basic 
information about a make, model, gas level, and mileage. 
We also give it getters, setters, and a few other methods. 

In the same project, the ``Program`` class contains a main method that prints the
``make`` and ``model`` of a given ``Car`` object. Run the project to verify it works.
Now, open ``CarTests``. It's empty, save for a few TODOs. Let's tackle the
first TODO to make a new empty test. 
Starting with an empty test lets us validate that we can use MSTest in our current environment.

.. index:: ! test runner

``[TestClass]`` and ``[TestMethod]``
------------------------------------

Another benefit of coding in an IDE, Visual Studio contains its own **test runner**. 
A test runner is simply a tool to execute tests and deliver their results. 
In order to indicate that ``CarTests`` contains unit tests that we want the test runner to run, 
we must give it the ``[TestClass]`` attribute. As you might 
guess, ``[TestMethod]`` annotates a method to signal it as a test case. 
Both of these attributes come to us via the Visual Studio test runner.

In ``CarTests``, on top of ``public class CarTests``, add ``[TestClass]``. 
Then, create the following empty test underneath the first TODO. 
As usual, be sure write this code rather than copy/paste it:

.. sourcecode:: c#
   :linenos: 

   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace CarTests
   {
      [TestClass]
      public class CarTests
      {
         //TODO: add emptyTest so we can configure our runtime environment
         [TestMethod]
         public void EmptyTest() {
            Assert.AreEqual(10,10,.001);
         }
         // ... other TODOs omitted here
      }
   }

Our empty test is aptly named ``EmptyTest()`` as a description of its role. 
This test does not follow the AAA rule from our :ref:`testing-best-practices`, 
as it jumps straight to asserting. Nor is it relevant, for that matter. 
The goal of this empty unit test is not to demonstrate all of our best practices, 
but rather, to verify that our testing setup is in place.

The three arguments in our test are defined as "expected", "actual", and "delta". 
This empty test asserts an expected value of ``10`` to equal an actual value of ``10``, 
with an accepted ``.001`` variance. 

.. admonition:: Note

   The third argument, called ``delta``, is the amount of allowed difference between the 
   expected and actual values. If the difference between the two values is within 
   that range, then the test still passes. 

   This argument is optional for some comparisons and required for others. One 
   scenario in which it is required is when comparing doubles. 

   Why is it required? Well, that's kind of a long story. Some number types are 
   `floating-point numbers <https://en.wikipedia.org/wiki/Floating-point_arithmetic>`__. 
   Due to the nature of their storage, these types carry with them a certain 
   degree of 
   `inaccuracy <https://en.wikipedia.org/wiki/Floating-point_arithmetic#Accuracy_problems>`__. 
   In brief, the ``delta`` argument ensures we can still reasonably compare two doubles.

.. admonition:: Tip

   Visual Studio can offer info on the parameters of a previously defined function.
   Hover over the function call to see a tooltip:

   .. figure:: ./figures/function-parameters-tooltip.png
      :alt: User hovers mouse over a function to see its parameter names

      Hover over a function to see its parameters

Of course, ``10`` equals ``10``. But let's run it so 
we know our test runner works. 


This would be a good time to try a negative and edge case test as well. 
We recommend practicing these extra cases so you can see what the output 
would look like in your Visual Studio.

.. sourcecode:: c#
   :linenos: 

   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace CarTests
   {
      [TestClass]
      public class CarTests
      {
         //TODO: add emptyTest so we can configure our runtime environment
         [TestMethod]
         public void EmptyTest() {
            Assert.AreEqual(10,10,.001);     //positive test case
            Assert.AreEqual(10,11,.001);     //negative test case
            Assert.AreEqual(10,10.0009,.001) //edge case
         }
         // ... other TODOs omitted here
      }
   }

Now that we have our test created, we can walk through how to run them.
Like running console projects, there are many ways to run unit 
tests and view the results. 
In the next section, we will explore how to run tests and use the data they provide to us.




Check Your Understanding
--------------------------

.. admonition:: Question

   You are creating a class registration program for your local community center.  
   In order to qualify as a class, there must be a minimum of 5 students enrolled, but no more than 30. 
   Which of the following numbers would be useful for testing edge cases?

   #. ``38`` and ``14``
   #. ``30`` and ``5``
   #. ``-1`` and ``0``
   #. ``30`` and ``30``

..  ans: ``30`` and ``5``;