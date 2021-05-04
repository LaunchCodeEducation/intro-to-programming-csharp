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

   objectName.attribute;
  





BEGIN INTRODUCING THE MATH CLASS/OBJECT Here
------------------------------------------------











.. admonition:: Example
   
   Fork this `replit <https://replit.com/@launchcode/ClassBasics101-CSharp#main.cs>`_ to run the example on your own machine.
   Note that the attribute in this example is hard coded. 


.. admonition:: Example

   Here is an example of two classes:  a new ``Cat`` class, and the ``MainClass``.

   The ``Cat`` class has been created under the ``namespace Pets`` (as seen in **Line 3**).
   The keyword ``class`` is used to declare that ``Cat`` is a class.

   .. sourcecode:: csharp
      :linenos:

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

      //in the MainClass, within the Main method
      class MainClass 
      {
         public static void Main (string[] args) 
         {
            Cat myCat = new Cat();       

            myCat.PetChin(); 
            Console.WriteLine(myCat.name);

            //creating a new Cat object and updating the name attribute
            Cat hisCat = new Cat();
            
            hisCat.name = "Beatrice";
            Console.WriteLine(hisCat.name);
            
            hisCat.PetChin();
         }
      }          

   **Console Output**

   :: 

      Purr
      Alyce

      Beatrice
      Purr
      


In the ``Cat`` Class:
   - **Line 5** we create our class attribute ``name`` and set it to the string value of "Alyce".
   - **Line 8** we create the method ``PetChin``.  It is a void method, and will print "Purr" to the console when invoked.
   - **Line 13** we define the default constuctor.  Meaning, we don't have to provide any arguements in order to create a Cat object.

In the ``MainClass`` Class:
   - **Line 6** we instantiate a new ``Cat`` object, ``myCat``, using the defualt, or empty, constructor.
   - **Line 8** we call ``PetChin`` on ``myCat`` via dot notation and "Purr" prints to the console.
   - **Line 9** we use dot notation to print the attribute ``myCat.name`` and "Alyce" prints.  
   - **Line 12** we created a second ``Cat`` object, ``hisCat``.
   - **Line 14** we update the ``name`` attribute for ``hisCat`` to ``"Beatrice"``.
   - **Line 15** verifying the update by printing the attribute.  Note the update in the output below
   - **Line 17** call the ``PetChin`` method on ``hisCat``.  "Purr" prints to the console, just as it did with ``myCat``.




Classes: Putting Things Together
-----------------------------------------------

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