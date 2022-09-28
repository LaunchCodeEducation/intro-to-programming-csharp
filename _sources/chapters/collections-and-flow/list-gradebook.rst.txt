
List Gradebook
================


Now that we have learned about the ``List`` class, let's apply that to the gradebook example.

Before going any further, we suggest you run the `List Gradebook <https://replit.com/@launchcode/Gradebook-List-CSharp>`_
program in your replit IDE.  

.. sourcecode:: csharp
   :linenos:

   using System;
   using System.Collections.Generic;


   class MainClass
   {
      static void Main(string[] args)
      {
         List<string> students = new List<string>();
         List<double> grades = new List<double>();
         string newStudent;
         string input;

         Console.WriteLine("Enter your students (or ENTER to finish):");

         // Get student names
         do
         {
            input = Console.ReadLine();
            newStudent = input;

            if (!Equals(newStudent, "")) {
               students.Add(newStudent);
            }

         } while(!Equals(newStudent, ""));

         // Get student grades
         foreach (string student in students) {
            Console.WriteLine("Grade for " + student + ": ");
            input = Console.ReadLine();
            double grade = double.Parse(input);
            grades.Add(grade);
         }

         // Print class roster
         Console.WriteLine("\nClass roster:");
         double sum = 0.0;

         for (int i = 0; i < students.Count; i++) {
            Console.WriteLine(students[i] + " (" + grades[i] + ")");
            sum += grades[i];
         }

         double avg = sum / students.Count;
         Console.WriteLine("Average grade: " + avg);
      }
   }


Here we declare and initialize two objects, ``students`` and ``grades``,
which appear to be of type ``List<string>`` and
``List<double>``, respectively. 

In **Lines 10 and 11**, we also initialize each ``List`` by creating a new, empty ``List``.  
So how do we fill these ``Lists``?

``List`` Iteration
-----------------------

``do-while``
^^^^^^^^^^^^

We then use a ``do-while`` loop to collect the names of each of the students
in the class.

.. sourcecode:: csharp
   :lineno-start: 17

   // Get student names
   do
   {
      newStudent = Console.ReadLine();

      if (!Equals(newStudent, "")) {
         students.Add(newStudent);
      }

   } while(!Equals(newStudent, ""));

Recall that a ``do-while`` loop is very similar to a ``while`` loop, but the
execution condition is checked at the end of the loop block. This has the net
effect that the code block will always run at least once. In this example, we
prompt the user for a name, which C# processes via ``Console.ReadLine()`` when
the user hits the enter key. To finish entering names, the user enters a blank
line.

.. admonition:: Note

   On **Lines 22 and 26**, we use a method to compare the value of ``newStudent`` and ``""``.
   The ``Equals(a,b)`` compares two strings, ``a`` and ``b``, and returns true if the strings are the same.
   If the strings are not the same, the method returns false.

.. index:: ! List.Add()

For each student that is entered (that is, each non-empty line), we add
the new string to the end of our List with ``students.Add(newStudent)``.

``foreach``
^^^^^^^^^^^

Below the ``do-while`` loop are two different loops that demonstrate two ways
you can loop through a List in C#. Here’s the first, which collects the
numeric grade for each student:

.. sourcecode:: csharp
   :lineno-start: 31

   // Get student grades
   foreach (string student in students) {
      Console.WriteLine("Grade for " + student + ": ");
      string input = Console.ReadLine();
      double grade = double.Parse(input);
      grades.add(grade);
   }

This, you may recall, is C#'s ``foreach`` loop syntax. You may read this
in your head, or even aloud, as: ``for each student in students``. As you might
expect at this point, we must declare the iterator variable ``student``
with its data type.

``for``
^^^^^^^
The next loop on display prints out each student’s name and grade:

.. sourcecode:: csharp
   :lineno-start: 34

   // Print class roster
   Console.WriteLine("\nClass roster:");
   double sum = 0.0;

   for (int i = 0; i < students.Count; i++) {
      Console.WriteLine(students[i] + " (" + grades[i] + ")");
      sum += grades[i];
   }

.. index:: ! List.Count

Here, we introduce the syntax ``students.Count`` which utilizes the ``Count``
property of ``List``. This property holds the integer representing the
number of items in the List. This is similar to string's ``.Length`` property.

In this ``for`` loop, we use a *loop index* to define the starting point,
ending point, and increment for iteration. It may be helpful for you to
consider this kind of construction as something like,  ``for integer i in the
range of the number of items in students...``. The first statement inside the
parenthesis declares and initializes a loop index variable ``i``. The second
statement is a boolean expression that is our exit condition. In other words,
we will keep looping as long as this expression evaluates to ``true``. The
third statement is used to increment the value of the loop index variable at
the end of iteration through the loop.

Again, the syntax ``i++`` is C# shorthand for ``i = i + 1``. C# also
supports the shorthand ``i--`` to decrement the value of ``i``.
We can also write ``i += 2`` as shorthand for ``i = i + 2``.

In the final lines of the program, we compute the average grade for all
students:

.. sourcecode:: csharp
   :lineno-start: 43

   double avg = sum / students.Count;
   Console.WriteLine("Average grade: " + avg);



And now we have a gradebook that uses two lists.  Let's compare that to an array gradebook next.