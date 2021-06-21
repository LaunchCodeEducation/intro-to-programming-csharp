.. _array-methods:

Array Methods
==============

.. index::
   single: array; methods

As with strings, C# provides us with useful **methods** for arrays.
These methods will either *alter* an existing array, *return* information about
the array, or *create and return* a new array.

Common Array Methods
--------------------

Here is a sample of the most frequently used array methods. More complete lists
can be found here:

#. `Microsoft Array Methods <https://docs.microsoft.com/en-us/dotnet/api/system.array?view=net-5.0>`__
#. `Geeks for Geeks Array Methods <https://www.geeksforgeeks.org/c-sharp-array-class/>`_


To see detailed examples for a particular method, control-click
(or right-click) on its name.

.. list-table:: Methods That Return Information About The Array
   :header-rows: 1

   * - Method
     - Syntax
     - Description
   * - :ref:`IndexOf <array-indexOf-examples>`
     - ``Array.IndexOf(arrayName, item)``
     - Returns the index of the FIRST occurrence of an item in the array.  
   * - :ref:`LastIndexOf <lastIndexOf-examples>`
     - ``Array.LastIndexOf(arrayName, item)``
     - Returns the index of the LAST occurrence of an item in the array. If the item is not in the array, -1 is returned.
   * - :ref:`GetValue <getValue-examples>`
     - ``arrayName.GetValue(index)``
     - Returns the value of specified index.

.. list-table:: Methods That Rearrange The Entries In The Array
   :header-rows: 1

   * - Method
     - Syntax
     - Description
   * - :ref:`Reverse <array-reverse-examples>`
     - ``Array.Reverse(arrayName)``
     - Reverses the order of the elements in an array.
   * - :ref:`Sort <array-sort-examples>`
     - ``Array.Sort(arrayName)``
     - Arranges the elements of an array into increasing order.


.. list-table:: Methods That Add Or Remove Values From An Array
   :header-rows: 1

   * - Method
     - Syntax
     - Description
   * - :ref:`Resize <resize-examples>`
     - ``Array.Resize(ref arrayName, desiredLength)``
     - Adds of Removes indicies based on desiredLength value.  

.. list-table:: Methods That Update Values Within An Array
   :header-rows: 1

   * - Method
     - Syntax
     - Description
   * - :ref:`SetValue <setValue-examples>`
     - ``arrayName.SetValue(new item, index)``
     - Updates index value with new item. 
   * - :ref:`Copy <copy-examples>`
     - ``Array.Copy(originalArray, copiedArray, numItems)``
     - Updates index value with new item. 

.. list-table:: String Methods That Update Array Values
   :header-rows: 1

   * - Method
     - Syntax
     - Description

   * - :ref:`Join <join-examples>`
     - ``string.Join("connecter", arrayName)``
     - Combines all the elements of an array into a string.

   * - :ref:`Split <split-examples>`
     - ``stringName.Split("delimiter")``
     - Divides a string into smaller string pieces, which are stored in a new array.
     
   * - :ref:`ToCharArray <toCharArray-examples>`
     - ``stringName.ToCharArray()``
     - Divides a string into chars, which are stored in a new array.
     


Check Your Understanding
------------------------

Follow the links in the table above for the ``Sort``, ``Reverse``, ``Split`` and
``Join`` methods. Review the content and then answer the following questions.

.. admonition:: Question

   What is printed by the following code?

   .. sourcecode:: csharp
      :linenos:

      string[] charles = {"coder", "Tech", "47", "23", "350"};
      Array.Sort(charles);
      Console.WriteLine(charles[0]);
      Console.WriteLine(charles[1]);
      Console.WriteLine(charles[2]);
      Console.WriteLine(charles[3]);
      Console.WriteLine(charles[4]);

   a. ``"350", "23", "47", "Tech", "coder"``
   b. ``"coder", "Tech", "23", "47", "350"``
   c. ``"23", "47", "350", "Tech", "coder"``
   d. ``"23", "350", "47", "coder", "Tech"``

.. ans: d, ``"23", "350", "47", "coder", "Tech"``

.. admonition:: Question

   Which statement converts the string ``string phrase = "LaunchCode students rock!"`` into the array ``string[] words = {"LaunchCode", "students", "rock!"}``?

   a. ``string.Join(" ", phrase);``
   b. ``phrase.Split(" ");``
   c. ``string.Join("", phrase);``
   d. ``phrase.Split("");``

.. ans: b, ``phrase.Split(" ");``

.. admonition:: Question

   What is printed by the following program?

   .. sourcecode:: csharp
      :linenos:

      string[] groceryBag = {"bananas", "apples", "edamame", "chips", "cucumbers", "milk", "cheese"};
      string[] selectedItems = new string[4];

      Array.Copy(groceryBag, selectedItems, 4);
      Array.Sort(selectedItems);

      Console.WriteLine(selectedItems[0]);
      Console.WriteLine(selectedItems[1]);
      Console.WriteLine(selectedItems[2]);
      Console.WriteLine(selectedItems[3]);


   a. ``"apples", "bananas", "edamame", "chips"``
   b. ``"chips", "cucumbers", "edamame", "milk"``
   c. ``"apples", "banana", "chips", "edamame"``
   d. ``"cheese", "chips", "cucumbers", "edamame"``

.. ans: c, ``"apples", "banana", "chips", "edamame"``
