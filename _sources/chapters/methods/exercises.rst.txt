Exercises: Methods
=====================

To become good at solving problems with code you need to be able to break large
problems into small ones. Usually, these smaller problems will take the form of
methods that are used to solve the larger problem. Therefore, to become good
at solving problems you need to become good at writing methods. And to master
methods, you need to write a *lot* of them.

These exercises ask you to write lots of methods, starting with 
small one and end with a larger, more complicated one.

At the end, you will be able to create strings of shapes, like this nifty
diamond:

::

       #
      ###
     #####
    #######
   #########
   #########
    #######
     #####
      ###
       #

.. admonition:: Note

   As you build your methods, remember to keep the output in mind.  
   Do you want a value returned or should it print directly to the console when invoked?
   How many things are being repeated?


Getting Started
------------------

Click here and fork the `starter code <https://replit.com/@launchcode/Hashtag-Exercises-CSharp>`_.  

.. admonition:: Tip

   As you create these methods, keep the shape of your output in mind.  
   Remember the differences between ``Console.WriteLine`` and ``Console.Write``.  


Rectangles
----------

#. Write a method ``MakeLine(size)`` that prints a line with exactly ``size``
   hashes.

   .. sourcecode:: csharp

      MakeLine(5);

   **Console Output**

   ::

      #####

#. Write a method called ``MakeSquare(size)`` that prints a ``size`` by
   ``size`` iteration of hashes. 

   .. sourcecode:: csharp

      MakeSquare(5);

   **Console Output**

   ::

      #####
      #####
      #####
      #####
      #####

   
   Asthetically it's not a "perfect" square, but a single argument led to its creation.

#. Write a method ``MakeRectangle(width, height)`` that prints a
   rectangle with the given width and height. 

   .. sourcecode:: csharp

      MakeRectangle(8, 3);

   **Console Output**

   ::

      ########
      ########
      ########


Triangles
----------

#. Write a method ``MakeDownwardStairs(height)`` that prints the staircase
   pattern shown below, with the given height. 

   .. sourcecode:: csharp

      MakeDownwardStairs(5);

   **Console Output**

   ::

      #
      ##
      ###
      ####
      #####

2. Write a method ``MakeSpaceLine(numSpaces, numChars)`` that prints a line
   with exactly the specified number of spaces, followed by the
   specified number of hashes, followed again by ``numSpaces`` more spaces.

   .. sourcecode:: csharp

      MakeSpaceLine(3, 5);

   **Console Output**

   ::

      ---#####---

   .. note:: We have inserted dashes to represent spaces, so they are visible in the output. 
      This can be helpful for building the pattern, but make sure to remove them from your final code.

#. Write a method ``MakeIsoscelesTriangle(height)`` that prints a triangle
   of the given height.

   .. sourcecode:: csharp

      MakeIsoscelesTriangle(5);

   **Console Output**

   ::

          #
         ###
        #####
       #######
      #########


Diamonds
---------

#. Write a method ``MakeDiamond(height)`` that prints a diamond where the
   triangle formed by the *top* portion has the given height.

   .. sourcecode:: csharp

      MakeDiamond(5);

   **Console Output**

   ::

          #
         ###
        #####
       #######
      #########
      #########
       #######
        #####
         ###
          #

   .. tip::

      Consider what happens if you create a triangle and reverse it within the same method?

Bonus Mission
--------------

#. Refactor your methods so that they also take a single character as a parameter,
   and draw the shapes with that character instead of always using ``#``.  Some ideas ``*`` or ``>``.
#. Make the new parameter optional, with default value ``#``.
