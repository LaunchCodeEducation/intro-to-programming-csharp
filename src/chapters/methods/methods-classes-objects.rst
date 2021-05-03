.. _methods-classes-objects:

Methods, Classes, and Objects! Oh My!
==========================================

Before we leave this chapter, we should touch on classes and objects briefly.  
These are big concepts in C#, and OOP in general.  
Before we deep dive into classes, let's get familiar with the larger concepts of classes and objects.
We will explore definitions and walkthrough examples that will demonstarate how classes, objects, and methods work together.

Classes: A Primer
--------------------

Classes are templates for creating **objects**.  Objects are *instances* of classes.
They are the endgame in OOP.  We create, modify, manipulate, and store objects in our programs. 

You have been working with classes and objecst since day 1.  ``Console.WriteLine`` is a method of the ``Console`` class.  
You have created string objects, and instantiated new array and ``List`` objects.  If you recall, each of these objects have their own rules.
You can't reverse a string as if it were an array.  You can't add elements to an array like you can with a ``List``, etc., etc.  

Who dictates these rules?  The class they belong to.  

A class is a template, or set of blueprints.  It is this template that defines the behvior or the objects it creates.  This is why string methods will not 
work on arrays, etc.  

Classes are the definition for the objects they create.  
That definition will deterimine the **attributes** the object requires, as well as the **behaviors** of the object.
Attributes are class variables.  They can be hard coded, or filled in at the time of instantiation.
Methods are the behvaiors or actions your class is able to preform on objects created by that class.

This allows you to be able to create multiple unique objects from a single class.  

Hopefully, this sounds similar to the methods you recently learned about.  
Like a method, we create a class with generic placeholders for specific values.  
Unlike a method, a class is able to be *overloaded* with multiple **constructors** that determine how the final object will be created.
Constructors are specialized methods that are used to create the object.  Constructors contain parameters required to create the object. 
A class can have multiple constuctors, containing a range of parameters from all to none, and any combination between.  
The parameters reflect what members are contained within the class.  
Parameterless constructors exist and are sometimes called the **default constuctor**, relying on the class to provide any default values or settings.  

The examples in this section will be using parameterless, or empty, constructors to walkthrough basic concepts of classes.  
We will explore these class members and constuctors deeper in the upcoming chapters.

When working with classes to create objects, you will see a familiar pattern.  
To delcare a *new* object of a class you will use the keyword ``new`` as you have done with ``Lists``, arrays, and dictionaries.  
The data type for these objects is the class, which you reference directly.

.. sourcecode:: csharp

 //data type                  constructor with possilbe parameters
   ClassName objectName = new ClassName(possible parameters);  

Class Type
-------------

Quick refesher on data types.  As discussed in chapter 4, C# contains value types and reference types.  
An **int** or **char** are examples of value data types.
While **strings** are reference types.  Classes are also reference data types that define objects, and objects are also reference types. 

If you remember, a reference type does not contain the actual value.  
Instead holds a reference point that leads to the memory location of the data. 

If we have a class ``Cat`` with a constructor that takes no arguments, we
declare and create a new instance of ``Cat`` using its constructor.

.. sourcecode:: c#

   Cat myCat = new Cat();

#. ``Cat myCat`` declares the variable ``myCat`` and sets it to be of type
   ``Cat``.
#. ``= new Cat()`` initializes the variable with a new ``Cat`` object. 
#. Any arguments that are required to build the new ``Cat`` object must be
   included within the parentheses. In this case, there are no required arguments.  Note the empty ``()``.

This statement creates a new variable that is initialized to
hold a new ``Cat`` object. Note that in C#, we must declare the
variable’s type. Also note that we precede the constructor with the
``new`` keyword. And, as we'll see with all C# statements, the 
declaration ends with a semi-colon.  

Variables and parameters that are of the type of a class are said to be
of **reference type** (in contrast to **primitive type**). In plain
English, we would say of the C# example: “``myCat`` is a reference
variable of type ``Cat``.”

As mentioned above, classes define reference types. A variable of a
reference type (such as ``myCat`` above) does not actually store the
object in question. Instead, it stores a **reference** to the object. A
reference is literally a memory address. We visualize references as an
arrow pointing to the object in memory.

Consider this code:

.. sourcecode:: c#

   int catAge = 11;
   Cat myCat = new Cat();
   Cat sameCat = myCat;

Visually, we can represent these three variables as shown here.

.. figure:: figures/references.png
   :alt: Reference Types.  First variable is int catAge = 11.  Second variable is Cat myCat = new Cat().  Third variable is Cat sameCat = myCat;
      Both myCat and sameCat point back to the Cat class type. 

   Reference Types

Since ``int`` is a value type, the variable ``catAge`` functions as a
box holding the integer value 11. On the other hand, ``myCat`` is a
reference variable, since it refers to an object of type ``Cat``. The 
variable actually stores the memory address of the object, which we visualize 
as an arrow from the variable box to the object. Instead of holding the actual ``Cat``
data, ``myCat`` stores *directions* for finding the data in memory.

When we assign ``myCat`` to another variable, as in ``Cat sameCat = myCat``,
we do NOT create a second copy of the object or its data. Instead, we make a
second *pointer* to the same memory location.

The distinction between reference types and value types is important,
but can be difficult to wrap your brain around at first. We will see
that reference types are handled differently in essential and important
ways in a lot of different situations.

.. index:: ! boxing, ! unboxing 

Boxing
^^^^^^

All types in C# are treated as objects. Even value types. This can be accomplished 
through processes called boxing and unboxing. Converting from a value type to a reference type is called 
**boxing**, and the reverse process (reference to value) is called **unboxing**. C# is known as a unified 
type system because it implicitly boxes values types to be treated as objects.   



.. sourcecode:: c#

   int i = 123;     // This is a value type.
   object o = i;    // Boxing the value type into a reference type.
   int j = (int)o;  // Unboxing the reference type back into a value type.


Working With Class Objects
----------------------------

When you instaniate a new object, you use the following signature:

.. sourcecode:: csharp

   ClassName objectName = new ClassName(possible parameters);  




Accessing Object Attributes and Methods
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Once instantiated, you can call any class member of your object using **dot notation**.

.. sourcecode:: csharp

   objectName.MethodName(); 

   Console.WriteLine(objectName.Attribute);
  

.. admonition:: Example
   
   Fork this `replit <https://replit.com/@launchcode/ClassBasics101-CSharp#main.cs>`_ to run the example on your own machine.
   Note that the attribute in this example is hard coded. 


.. admonition:: Example

   In this example we will instantiate a new ``Cat`` object and then invoke the ``PetChin`` method using dot notation.

   .. sourcecode:: csharp
      :linenos:

      //in the Cat class
      public class Cat
      {
         public string name = "Alyce";

         public void PetChin() 
         {
            Console.WriteLine("Purr");
         }

         public Cat()
         {

         }
      }

   .. sourcecode:: csharp
      :linenos:

      //in the MainClass, within the Main method
      class MainClass 
      {
         public static void Main (string[] args) 
         {
            Cat myCat = new Cat;       

            myCat.PetChin(); 
            Console.WriteLine(myCat.Name);
         }
      }          

   **Console Output**

   :: 

      Purr
      Alyce


In the ``Cat`` Class:
   - **Line 4** we create our class attribute ``name`` and set it to the string value of "Alyce".
   - **Line 6** we create the method ``PetChin``.  It is a void method, and will print "Purr" to the console when invoked.
   - **Line 11** we define the default constuctor.

In the ``MainClass`` Class:
   - **Line 6** we instantiate a new cat object, ``myCat``, using the defualt, or empty, constructor.
   - **Line 8** we call ``PetChin`` on ``myCat`` via dot notation and "Purr" prints to the console.
   - **Line 9** we use dot notation to print the attribute ``myCat.name`` and "Alyce" prints.  




Classes: Putting Things Together
-----------------------------------------------

Classes create objects.  Therefore, an object is an instance of a class. 
Classes themselves are templates that contain attributes and methods to define an object.  
Constructors are used to define parameters, and are part of the instantiation process.  
We can access class members by using dot notation.

This is a very very simple explanation of classes in C#.  We will learn more in upcoming chapters.


Check Your Understanding
---------------------------

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