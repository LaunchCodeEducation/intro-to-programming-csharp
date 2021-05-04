Classes, Objects, and Methods! Oh My!
=========================================

Classes are templates for creating **objects**.  Objects are *instances* of classes.
They are the endgame in OOP.  We create, modify, manipulate, and store objects in our programs. 

You have been working with classes and objecst since day 1.  ``Console.WriteLine`` is a method of the ``Console`` class.  
You have created string objects, and instantiated new array and ``List`` objects.  
If you recall, each of these objects have their own rules.
You can't reverse a string as if it were an array.  
You can't add elements to an array like you can with a ``List``, etc., etc.  

Who dictates these rules?  The class they belong to.  

What Is A Class?
^^^^^^^^^^^^^^^^^

A class is a template, or set of blueprints, used to create objects.  
The template dictates what an object of this class requires, as well as how that object behaves.

To declare a new class, you will need the keyword ``class``.  
When working with replit.com, you will need to create a new class in a new file.  
In order for your class to be recognized by ``MainClass`` in replit, you will need to provide your class its own unique ``namespace``.

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
^^^^^^^^^^^^^^^^^^^^^^^^

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

When we instantiate an object, we use the class **constructor** to provide any needed values to initialize any attributes.  
The syntax just like the parameter list of a method.
In fact, the constructor is a specialized method.  
Any parameters passed to a consturctor will be used to initialize any attributes for that object.

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

Methods are the behvaiors or actions your class is able to preform on objects created by that class.  
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
the attribute ``name`` will "Alyce" or exactly what we coded it to be.  

If we wanted to update the name, you would do so like any other variable.

.. sourcecode:: csharp
   :lineno-start: 10
   
   //within the Main method
   Cat hisCat = new Cat();
   
   myCat.name = "Porkchop";
   Console.WriteLine(myCat.name);

**Console Output**

.. sourcecode:: csharp

   Porkchop


Creating Multiple Objects
^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^

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

   How would we instantiate a new car object in the Main method?

   #. ``newCar.Car()``
   #. ``string car = new Car();``
   #. ``Car newCar = new Car();``
   #. ``Car() newCar = new Car();``

.. ans: c, Car newCar = new Car();


