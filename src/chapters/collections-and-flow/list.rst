.. _List:

.. index:: ! List

Lists
=======
 
A C# ``List`` is a class, which means it contains its own properties and methods that we can 
use in our programs.  You have seen this before when working with ``Strings`` and ``Arrays``. 
A ``List`` is more closely related to an ``Array`` than a ``String``, as in it is mutable.  
However, unlike an ``Array``, you do not have to declare the size of your ``List``.  In fact
methods exist to modify the size of a ``List`` in ways that will feel effortless compared to the ``Array``.

Let's start making some ``List`` objects so we can see how they work.  You can try them `here <https://replit.com/@launchcode/List-Initialization-Three-Ways#main.cs>`_.

``List`` Initialization
--------------------------

Like with arrays, there are a few ways to initialize lists. 
We could declare and initialize lists in one line like so:

.. sourcecode:: csharp

   List<T> newList = new List<T> {element1, element2, element3};
            
   List<string> sitesInSTL = new List<string> 
   {
      "The Gateway Arch", 
      "City Museum", 
      "Forest Park", 
      "Busch Stadium"
   };
            

We can also declare and initialize using the list method ``Add()``.

.. sourcecode:: csharp

   List<T> newList = new List<T>();
      newList.Add(element1);
      newList.Add(element2);
      newList.Add(element3);
      newList.Add(element4);

   List<int> houseNumbers = new List<int>();
      houseNumbers.Add(123);
      houseNumbers.Add(127);
      houseNumbers.Add(131);
      houseNumbers.Add(135);


And finally, we can pull in elements from an array into our list.

.. sourcecode:: csharp

   type[] demoArray = {element1, element2, element3};
   List<T> demoList = new List<T>(demoArray);

   string[] colors = {"red", "orange", "yellow", "green", "blue", "purple"};
   List<string> colorList = new List<string>(colors);

.. index:: ! generic class, generic type

.. admonition:: Note

   You will sometimes see the ``List`` class written as List<T>,
   where ``T`` represents a *placeholder* for the type that a programmer will
   declare a given List to hold. This is especially true in documentation.
   You can think of ``T`` as representing an arbitrary **type**.

   Classes like ``List<T>`` that take another type or class as a parameter
   are referred to as **generic classes** or **generic types**.


List Methods
------------

You've created a few new lists. Great! Now what?  Let's look at a few ``List`` methods to 
start using them in your programs.  While the table below contains some of the more common methods and
properties that you use with this class, they by no means represent a complete
record. Refer to the `official documentation on the List
class <https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1?view=netframework-4.8>`__
for such a record, and for more details.

To `demonstrate <https://replit.com/@launchcode/ListMethodsPractice-CSharp#main.cs>`_ the use of these methods, we'll create a new ``List``
called ``planets``.  

.. sourcecode:: csharp

   List<string> planets = new List<string>();

Ok, we've got an empty List. We need to use the class's ``.Add()`` method
to populate this collection with items.

Using ``.Add()`` to populate ``planets``:

.. sourcecode:: C#
   :linenos:

   planets.Add("Mercury");
   planets.Add("Venus");
   planets.Add("Earth");
   planets.Add("Mars");
   planets.Add("Jupiter");
   planets.Add("Saturn");
   planets.Add("Uranus");
   planets.Add("Neptune");

Thus, the first item in this table:

.. _list-methods:

.. _listsort:

.. list-table:: List Methods in C#
   :header-rows: 1

   * - C# Syntax
     - Description
     - Example
   * - :ref:`Add() <add-examples>`
     - Adds an item to the List
     - ``planets.Add("Pluto")`` adds ``Pluto`` to ``planets``
   * - :ref:`Contains() <contains-examples>`
     - Checks to see if the List contains a given item, returning a Boolean
     - ``planets.Contains("Earth")`` returns ``true``
   * - :ref:`IndexOf() <list-indexOf-examples>`
     - Looks for an item in a List, returns the index of the first occurrence of the item if it exists, returns -1 otherwise
     - ``planets.IndexOf("Jupiter")`` returns ``4``
   * - :ref:`Reverse() <list-reverse-examples>`
     - Reverses the elements of a ``List`` 
     - ``planets.Reverse()`` returns
       ``{"Pluto", "Neptune", "Uranus", "Saturn", "Jupiter", "Mars", "Earth", "Venus", "Mercury"}``
   * - :ref:`Sort() <list-sort-examples>`
     - Rearranges the elements of an ``List`` into ascending order.
     - ``planets.Sort()`` produces ``{"Earth", "Jupiter", "Mars", "Mercury", "Neptune", "Pluto", "Saturn", "Uranus", "Venus"}``
   * - :ref:`Remove() <remove-examples>`
     - Removes first occurance of a specified object
     - ``planets.Remove("Pluto")`` returns
       ``{"Earth", "Jupiter", "Mars", "Mercury", "Neptune", "Saturn", "Uranus", "Venus"}``
   * - :ref:`ToArray() <toArray-examples>`
     - Returns an Array containing the elements of the List
     - ``planets.ToArray()`` returns and array contianing
       ``{"Earth", "Jupiter", "Mars", "Mercury", "Neptune", "Saturn", "Uranus", "Venus"}``
   
.. admonition:: Example

   In order to use ``ToArray``, we could first declare a ``planetsArray`` of the same size as ``planets`` or do it in one line of code.

   .. sourcecode:: csharp
      :linenos:

      // Option A
      string[] planetsArray = new string[planets.Count];
      planetsArray = planets.ToArray();

      // Option B
      string[] planetsArray = planets.ToArray();

In addition to these different methods we can use, the ``List`` class has a
number of properties that are very helpful. You may find yourself using the
``Count`` property quite a bit. This property holds the number of values in the
list. In our example, after we add all of the planets in the solar system,
``planets.Count`` has a value of ``8`` (unless you also added Pluto to
``planets``, in which ``planets.Count`` returns ``9``).

Let's look at our gradebook examples.  We will start with a ``List`` version, then compare it to an array version.

Check Your Understanding
-------------------------

.. admonition:: Question

   The number of entries in a ``List`` may not be modified.

   #. True
   #. False

.. ans: False

.. admonition:: Question

   Create a ``List`` called ``charStars`` containing ``a``, ``b``, and ``c``.

   #.

      .. sourcecode:: C#
         :linenos:

         List<string> charStars = new List<string>();
         charStars.Add('a');
         charStars.Add('b');
         charStars.Add('c');

   #.
      .. sourcecode:: C#
         :linenos:

         List<char> charStars = new List<string>();
         charStars.Add('a');
         charStars.Add('b');
         charStars.Add('c');

   #.
      .. sourcecode:: C#

         List<char> charStars = new List<char>("a", "b", "c");

   #.
      .. sourcecode:: C#
         :linenos:

         List<string> charStars = new List<string>();
         charStars.Add("a");
         charStars.Add("b");
         charStars.Add("c");

.. ans: List<string> charStars = new List<string>();
         charStars.Add("a");
         charStars.Add("b");
         charStars.Add("c");
