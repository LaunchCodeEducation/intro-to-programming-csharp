Exercises: Arrays
=================

Parts One And Two
-------------------
OK, rookie. It's time to train you on how to modify the shuttle's cargo
manifest. The following actions will teach you how to add, remove, modify and
rearrange our records for the items stored in our hold.

1. Create an string array called ``practiceFile`` and add the following items. 
   Use **bracket notation** to update indicies 0 and 1 with items a and b to the array.  
   Use the ``SetValue`` method to update indices 2 and 3 with items c and d.


   #. "42"
   #. "hello"
   #. "false"
   #. "-4.6"


   `Code it at repl.it <https://repl.it/@launchcode/ArrayExercises01-CSharp>`__  

   *Congratulations, rookie. You can now add items to an array.*


2. Sometimes you need to update your array.  Maybe the number of items is wrong, 
   or the items need to be updated.  In C#, we can change the size with the 
   ``Resize`` method.  The ``SetValue`` method and bracket notation can be used
   to update existing array items.  Starting with the ``cargoHold`` string array
   ``{"oxygen tanks", "space suits", "parrot", "instruction manual",
   "20 meters", "slinky", "security blanket"}``, write statements to do the
   following:

   #. Start by using ``Console.WriteLine`` to print all the items in the array.  
      Use string interpolation to update the following:  ``"The length of the array is ____"``.  
      This will give us a way to check our updates.
   #. Remove the last item from the array with Resize. Print an updated length statement using a new string interpolation.
   #. Using ``Resize`` once more, extend your array by 3.  Set the following items
      into the new indices:  ``"1183"``, ``"meal packs"``, and ``"toothbrush"``.  Print the new items 
      to verify their placement. 
   #. Before we move on, we need to update a few items in our array.  Use bracket notation to replace ``"slinky"`` 
      in the array with ``"space tether"``.  Use ``SetValue`` to update ``"1183"`` to ``"keys"``.  And update ``"parrot"`` to 
      ``"flashlight"`` using a method of your choice. 
   #. Use a ``Console.WriteLine`` to print the final array.  
      Determine the final length and use a new string interpolation to print an updated length statement.

   `Code it at repl.it <https://repl.it/@launchcode/ArrayExercises02-CSharp>`__   



Parts Three And Four
---------------------

   *Well done, cadet. Now let's look at some finer details about array methods.
   We've got to keep our paperwork straight, so you need to know when your
   actions change the original records.*

3. Some methods---like ``Sort`` and ``Reverse``---alter the original array,
   while others do not. Use the arrays

   .. sourcecode:: csharp

      string[] holdCabinet1 = new string[] {"duct tape", "gum", "3.14", "false", "6.022e23"};

   and

   .. sourcecode:: csharp

      string[] holdCabinet2 = new string[] {"orange drink", "nerf toys", "camera", "42", "parsnip"};

   to explore the following methods: ``Sort``, ``Reverse``. Refer back to the chapter if you need to review the proper syntax for any of these methods.

   #. ``Reverse`` the first array, and ``Sort`` the second. Print each array to verify your changes.
      What is the difference between these two methods? Do the methods alter the original arrays?  
      How does ``Reverse`` work?  What is reversed?  How does ``Sort`` work?  What is being sorted?
      How are things sorted when using ``Sort``?
   #. Select one of the arrays.  Using your array methods, update the items within the array so that they are in descending (
      reverse alphabetical) order.  Print the array to verify your changes.
      

   `Code it at repl.it <https://repl.it/@launchcode/ArrayExercises03-CSharp>`__


   *Good progress, cadet. Here are three more methods for you to examine.*

4. The ``Split`` method converts a string into an array, the ``Join``
   method does the opposite, and the ``ToCharArray`` converts a string into its characters within an array.

   #. Try it! Given the string ``string str = "In space, no one can hear you code."``,
      see what happens when you print ``str.Split()`` vs. ``str.Split('e')``
      vs. ``str.Split(' ')`` vs. ``str.Split('')``. What is the purpose of the
      parameter inside the ``()``?  Print at least 3 indices of each ``Split`` to verify your changes.
   #. Given the array ``char[] arr = ['B', 'n', 'n', 5]``, see what happens when
      you print ``arr.Join()`` vs. ``arr.Join('a')`` vs. ``arr.Join(' ')`` vs.
      ``arr.Join('')``. What is the purpose of the parameter inside the ``()``?
   #. Do ``Split`` or ``Join`` change the original string/array?
   #. The benefit, cadet, is that we can take a string with **delimiters**
      (like commas) and convert it into a modifiable array. *Try it!*
      Alphabetize these hold contents: ``"water,space suits,food,plasma
      sword,batteries"``, and then combine them into a new string.
   #. Strings are **immutable**, but arrays are **mutable**.  So what can you do when your string has a typo?
      Given the string ``string message = "Hullo World!"``, use ``ToCharArray`` to fix is so that it 
      reads ``Hello World!``.  Does ``ToCharArray`` change the original string?

   `Code it at repl.it <https://repl.it/@launchcode/ArrayExercises04-CSharp>`__

Part Five:  Bonus Mission
---------------------------------
   *Nicely done, astronaut. Now it's time to bring you fully up to speed.*

5. Arrays can hold many different data types, even other arrays! A
   **multi-dimensional array** is one with entries that are themselves arrays.

   #. Define and initialize the following arrays, which hold the name, chemical
      symbol and mass for different elements:

      i. ``string[] element1 = {"hydrogen", "H", "1.008"};``
      ii. ``string[] element2 = {"helium", "He", "4.003"};``
      iii. ``string[] element26 = {"iron", "Fe", "55.85"};``

   #. Using bracket notation and the ``table`` array, print the mass of
      element1, the name for element 2 and the symbol for element26.  
   #. ``table`` is an example of a *2-dimensional array*. The first "level"
      contains the element arrays, and the second level holds the
      name/symbol/mass values. **Experiment!** Create a *3-dimensional* array and
      print out one entry from each level in the array.

   

*Excellent work, records keeper. Welcome aboard.*
