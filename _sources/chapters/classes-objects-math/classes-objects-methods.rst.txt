Classes, Objects, and Methods! Oh My!
=========================================

Classes are templates that define **objects**.  The class becomes the type of that object, but is not an object itself.
It's like a cookie cutter.  It shapes the cookie, but is not the cookie itself.  

An object is its own entity of whatever type class created it.  
When objects are created, it is often referred to as an **instance of class**. 
We create, modify, manipulate, and store objects in our programs.  
Classes are a way to create many new objects using a single template.  

You have been working with classes and objects since day 1.  
``WriteLine()`` is a method of the ``Console`` class.  
You have initalized string objects, and instantiated new array and ``List`` objects.  

Classes also contain any rules and methods for the object it creates.  
This is why  ``List`` methods don't work on **string** objects.  
C# has many built-in classes, but as a programmer you will want to create your own.  
In order to be able to do that, we need to explore the basics of classes and objects.


What Is A Class?
-------------------

A class is a template, or set of blueprints, used to create objects.  
The template dictates what an object of this class requires, as well as how that object behaves.

To declare a new class, you will need the keyword ``class``.  

.. admonition:: Note

   When working with replit.com, you will need to create a new class in a new file.  
   In order for your class to be recognized by ``MainClass`` in replit, you will need to provide your class its own unique ``namespace``.
   
   We will be moving to a different IDE soon, so any replit.com code examples will be provided to you.  

When working in a project with multiple classes, it is common to have a ``namespace``.  
A ``namespace`` connects all classes within a project.  
In this context, a ``namespace`` can be more for organizational purposes, providing direction to each class within the main project.  
If the ``namespace`` is not part of the ``Main method`` you will have to access it through a ``using`` statement.
Just like we did with Collections.  
This tells the compiler to look through any classes within the same ``namespace`` for definitions and requirements.

.. admonition:: Example

   Here is an example of two classes:  a new ``Cat`` class, and the ``MainClass``.

   The ``Cat`` class has been created under the ``namespace Pets`` (as seen in **Line 3**).
   The keyword ``class`` is used to declare that ``Cat`` is a class.

   .. replit:: csharp
      :linenos:
      :slug: ClassBasics101-CSharp

      using System;

      namespace Pets
      {
         //in the Cat class
         public class Cat
         {
            //class attribute
            public string name = "Alyce";

            //class member
            public void PetChin() 
            {
               Console.WriteLine("Purr");
            }

            public Cat()
            {

            }
         }
      }

   .. sourcecode:: csharp
      :linenos:

      using System;
     
      //provide access to class definitions contained within this namespace.
      using Pets;

      class MainClass 
      {
         public static void Main (string[] args) 
         {
            Cat myCat = new Cat();       

            myCat.PetChin(); 
            Console.WriteLine(myCat.name);
         }
      }          

   **Console Output**

   :: 

      Purr
      Alyce


Instantiating Objects
^^^^^^^^^^^^^^^^^^^^^

When working with classes to create objects, you will see a familiar pattern.  
To delcare a *new* object of a class you will use the keyword ``new`` as you have done with ``Lists``, arrays, and dictionaries.  
The data type for these objects is the class, which you reference directly.

.. sourcecode:: csharp

 //data type                  constructor with possilbe parameters
   ClassName objectName = new ClassName(possible parameters); 


In our ``Cat`` class example, we instantiate ``myCat`` which is a new ``Cat`` object.

.. sourcecode:: csharp
   :lineno-start: 10

   Cat myCat = new Cat();         


Class Constructors
^^^^^^^^^^^^^^^^^^^^^^^

In order to instantiate a new object, we need to know what values are needed, if any.  
To do this, we use a class **constructor**. 
A constructor is a special method that instantiates new objects.
Just like a method, we pass it arguments that are used to set the attributes, which will also determine behvaiors.

Constructors can also be parameterless.  We call this the **default constructor**.  
A default constructor is left empty, allowing the object to be created with any attributes initalized manually via dot notation.

The examples in this section will be using parameterless, or empty, constructors to walkthrough basic concepts of classes.  
We will explore these class members and constuctors deeper in the upcoming chapters.

In our ``Cat`` example, the default constructor is on **Line 16**.

.. sourcecode:: csharp
   :lineno-start: 16

   public Cat()
   {

   }

This default constructor means that we do not have to provide any arguments in order to create a new ``Cat`` object.  

.. sourcecode:: csharp
   :lineno-start: 10
   
   //within the Main method
   Cat myCat = new Cat();


Class Members
^^^^^^^^^^^^^^^

Class definitions deterimine any **attributes** the object requires, as well as any **behaviors** of the object.
Attributes are class variables, also called **fields**.  They can be hard coded, or filled in at the time of instantiation.

Methods are the behaviors or actions your class is able to perform on objects created by that class.  
They belong to the class they are defined in.  This means that you are not able to call methods from one class on another.

We can refer to the combination of class attributes and methods as **class members**.

Class members will be initialized when as an object is instantiated.  
This allows you to be able to create multiple unique objects from a single class.  

In our ``Cat`` class we have defined a string ``name`` attribute and a ``PetChin`` method.  
These are available to any object instantiated by the ``Cat`` class.

.. sourcecode:: csharp
      :lineno-start: 8

      //within the Cat class
      public string name = "Alyce";

      public void PetChin() 
      {
         Console.WriteLine("Purr");
      }


Dot notation is required to access the class members.  
**Line 11** we use dot notation to print the ``name`` attribute of the ``myCat`` object.
In **Line 12** we call the ``PetChin`` method on the ``myCat`` object.

.. sourcecode:: csharp
   :lineno-start: 9
   
   //within the Main method
   Cat myCat = new Cat();
   Console.WriteLine(myCat.name);
   myCat.PetChin();

**Console Output**

.. sourcecode:: csharp

   Alyce
   Purr


Since we used the default constructor to create the ``myCat`` object, 
the attribute ``name`` will be "Alyce" or exactly what we coded it to be.  

If we wanted to update the name, you would do so like any other variable.

.. sourcecode:: csharp
   :lineno-start: 10
   
   //within the Main method
   Cat myCat = new Cat();
   
   myCat.name = "Porkchop";
   Console.WriteLine(myCat.name);

**Console Output**

.. sourcecode:: csharp

   Porkchop


Creating Multiple Objects
----------------------------

What if we want to create multiple instances of the ``Cat`` class?  
Classes are templates remember, we can use them to do just that.

If we want to create multiple instances of the ``Cat`` class, we need to instantiate more ``Cat`` objects.

.. sourcecode:: csharp
   :linenos:

   using System;
   
   //provide access to class definitions contained within this namespace.
   using Pets;

   class MainClass 
   {
      public static void Main (string[] args) 
      {
         Cat myCat = new Cat();       

         myCat.PetChin(); 
         Console.WriteLine(myCat.name);


         Cat hisCat = new Cat();

         Console.WriteLine(hisCat.name);
         hisCat.PetChin();
      }
   }          

**Console Output**

:: 

   Purr
   Alyce

   Alyce
   Purr

   
Now we have two ``Cat`` objects, which have the same class members. But what if ``hisCat`` has a different name?
We can update the value of the attribute, just like any other variable.

.. sourcecode:: csharp
   :lineno-start: 16

   Cat hisCat = new Cat();

   hisCat.name = "Beatrice";
   Console.WriteLine(hisCat.name);

   hisCat.PetChin();
          

**Console Output**

:: 

   Beatrice
   Purr

   
We updated ``hisCat.name`` to ``Beatrice`` and we still have access to the method ``PetChin``. 
We have two ``Cat`` objects that have the same class members, though we have changed the values of ``name``.  
These objects were created by the same class, but are unique.  


Classes: Putting Things Together
----------------------------------

Classes create objects.  Therefore, an object is an *instance* of a class. 
Classes themselves are templates that contain attributes and methods to define an object.  
Constructors hold parameters that are required in order to instantiate objects.  
However, constructors can be parameterless.

To access class members, we use dot notation.

The attributes and methods created inside a class belong to that class.  
If you look at the `Cat class example <https://replit.com/@launchcode/ClassBasics101-CSharp#main.cs>`_
There is a Dog class as well.  The Dog class has its own method ``Bark``.  
If you tried to call that on a Cat object, an error would be thrown because ``Bark`` is not part of the Cat class definition.

This is a very, very simple explanation of classes in C#.  We will learn more in upcoming chapters.


Check Your Understanding
----------------------------

.. admonition:: Example
  
   Use the following code block for both questions.

   .. sourcecode:: csharp
      :linenos:

      //in the Car class
      public class Car
      {
         public void RevEngine() 
         {
            Console.WriteLine("Vroom! Vroom!");
         }

         public Car()
         {

         }
      }


.. admonition:: Question

   The **constructor** starts on which line number?

   #. 3
   #. 9
   #. 2
   #. 6

.. ans: b, ``6``

.. admonition:: Question

   How would we call the method ``RevEngine`` on the car object, ``redCar``, in the Main method?

   #. ``redCar.Car(RevEngine)``
   #. ``string car = new Car().RevEngine;``
   #. ``redCar.RevEngine();``
   #. ``RevEngine(redCar);``

.. ans: c, redCar.RevEngine();


