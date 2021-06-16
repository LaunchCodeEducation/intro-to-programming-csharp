
Dictionary Gradebook
=====================

We suggest you open the following `Dictionary Gradebook  <https://replit.com/@launchcode/Gradebook-Dictionary-CSharp#main.cs>`_ in your replit IDE.

.. sourcecode:: csharp
   :linenos:

   using System;
   using System.Collections.Generic;

   class MainClass
   {
      static void Main(string[] args)
      {
         Dictionary<string, double> students = new Dictionary<string, double>();
         string newStudent;

         Console.WriteLine("Enter your students (or ENTER to finish):");

         // Get student names and grades
         do
         {
               Console.WriteLine("Student: ");
               string input = Console.ReadLine();
               newStudent = input;

               if (!Equals(newStudent, ""))
               {
                  Console.WriteLine("Grade: ");
                  input = Console.ReadLine();
                  double newGrade = double.Parse(input);
                  students.Add(newStudent, newGrade);

                  // Read in the newline before looping back
                  Console.ReadLine();
               }

         } while (!Equals(newStudent, ""));

         // Print class roster
         Console.WriteLine("\nClass roster:");
         double sum = 0.0;

         foreach (KeyValuePair<string, double> student in students)
         {
               Console.WriteLine(student.Key + " (" + student.Value + ")");
               sum += student.Value;
         }

         double avg = sum / students.Count;
         Console.WriteLine("Average grade: " + avg);
      }
   }

Notice how a ``Dictionary`` called ``students`` is declared on **Line 8**:

.. sourcecode:: C#
   :lineno-start: 8

   Dictionary<string, double> students = new Dictionary<string, double>();

Here, ``<string, double>`` defines the data types for this dictionary's
``<key, value>`` pairs.

We can add a new item with a ``.Add()`` method, specifying both key and
value:

.. sourcecode:: csharp
   :lineno-start: 25

   students.Add(newStudent, newGrade);

.. index:: ! bracket notation

And while we don’t do so in this example, we may also access ``Dictionary``
elements using **bracket notation**. If we had a key/value pair of
``"jesse"/4.0`` in the ``students`` dictionary, we could access the grade with:

.. sourcecode:: csharp

   double jesseGrade = students["jesse"];

Variables may be used to access elements:

.. sourcecode:: csharp
   :linenos:

   string name = "jesse";
   double jesseGrade = students[name];


.. _kvp-foreach:


Looping through a dictionary is slightly more complex than it is for ordered lists.
Let’s look at the ``foreach`` loop from this example:

.. sourcecode:: csharp
   :lineno-start: 37

   foreach(KeyValuePair<string, double> student in students) {
      Console.WriteLine(student.Key + " (" + student.Value + ")");
      sum += student.Value;
   }

.. index:: ! KeyValuePair<T,T>

The iterator variable, ``student``, is of type
``KeyValuePair<string, double>``. The class **KeyValuePair<T,T>** is specifically
constructed to be used in this fashion, to represent key/value pairs
within dictionaries. Each ``KeyValuePair`` object has a ``Key`` property and a
``Value`` property.

If you only need to access the key of each item, you can
construct a simpler loop and use the ``Keys`` property of the ``Dictionary`` class:

.. sourcecode:: csharp
   :linenos:

   foreach (string studentName in students.Keys) {
      Console.WriteLine(studentName);
   }

A similar structure applies if you only need the values, using
``students.Values``:

.. sourcecode:: csharp
   :linenos:

   foreach (double grade in students.Values) {
      Console.WriteLine(grade);
   }


We have only brushed the surface of how arrays, ``Lists``, and dictionaries work.
We leave it to you to refer to the official documentation linked througout the chapter for more
details. You’ll certainly be using ``Lists`` and dictionaries in more ways than
those covered in this lesson, but with the knowledge you have now, you
should be able to use C# collections and learn new uses as you go.