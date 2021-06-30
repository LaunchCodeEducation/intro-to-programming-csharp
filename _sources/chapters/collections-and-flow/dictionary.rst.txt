
.. _dictionary:

.. index:: ! Dictionary

Dictionary
==========

While ``Lists`` are nice, sometimes we could use a different way to organize our data.  
So far in the gradebook examples we have had to use two separate lists or arrays to store student
names and grades.  The worst part is that, an index is required for both objects in order to pair 
the student with their grade correctly.  That is two indices you have to track and manipulate 
between two separate objects.  With a dozen students we could handle this, but what if you had one hundred? 
What if you wanted to search for a specific name, such as Nicole, but your roster has three Nicoles.  You 
are looking for the one who scored an 88.  But that 88 is in the other array, and another student scored 88 as well.
There are methods for finding the right Nicole and the right 88, but talk about a logic headache.  

What if we could pair the name and the grade together in a single collection type?  That would be pretty nice, right?

Luckily, the ``Dictionary`` class allows us to do just that.  The ``Dictionary`` works with pairs of **keys** and **values**, sometimes
referred to as **key/value** **pairs**.  The key is a reference point that holds values.  Using our gradebook analogy, we 
could use the student names as keys and their grades as values.  We could sort through the dictionary using the keys, or we could use the values, 
and we can also sort for specific key/value pairs.  This can simplify our search by using the student key "Nicole" with the grade value of 88 in *one* collection.  

The key/value pair structure does come with a few rules, such as *every* key must have a pair, and every pair *must* have a key.
Only one value *object* per key.  If you use an ``int`` for the value, then only one int allowed.  If you use a ``List<int>`` as a value, you still 
only have one value per key, your value is a list containing multiple elements.  You typically want only one key object, as keys are a fast way to 
search a dictionary object.

In the next section we will look at the gradebook again, only this time as a ``Dictionary`` and you will get to see the key/value pairs in action.

.. _initialize-dictionary: 

``Dictionary`` Initialization
--------------------------------

As usual, there are a few ways to `initalize a dictionary <https://replit.com/@launchcode/Dictionary-Initialization#main.cs>`_.  

.. sourcecode:: csharp

   Dictionary<TKey, TValue> newDictionary = new Dictionary<TKey, TValue>
   {
      {key1, value1},
      {key2, value2},
      {key3, value3}
   };

   Dictionary<string, int> classSize = new Dictionary<string, int>
   {
      {"Biology", 36},
      {"Ecology", 28},
      {"English", 45}
   };


We can also use index initialization to create a dictionary.

.. sourcecode:: csharp

   Dictionary<TKey, TValue> demoDictionary = new Dictionary<KeyT, ValueT>
   {
      [key1] = value1,
      [key2] = value2,
      [key3] = value3
   };

   Dictionary<int, string> roomAssignments = new Dictionary<int, string>
   {
      [25] = "Hernandez",
      [35] = "Stein",
      [27] = "Starkey"
   };

And finally, you can declare the dictionary and use the ``Add`` method to initalize.

.. sourcecode:: csharp

   Dictionary<TKey, TValue> methodDictionary = new Dictionary<TKeym TValue>();
      methodDictionary.Add(key1, value1);
      methodDictionary.Add(key2, value2);
      methodDictionary.Add(key3, value3);

   Dictionary<string, string> teachingAssignments = new Dictionary<string, string>();
      teachingAssignments.Add("Biology", "E. Stein");
      teachingAssignments.Add("English", "J. Starkey");
      teachingAssignments.Add("Ecology", "F. Hernandez");

.. admonition:: Note
   
   The easiest way to print each key/value pair is to use the class ``KeyValuePair<TKey, TValue>``.  

   ``KeyValuePair<TKey, TValue>`` will print each key/value pair as an object, which in the console can look like this:
   
   .. sourcecode::  csharp
      
      foreach(KeyValuePair kvp in dictionaryName)
      {
         Console.WriteLine(kvp)
      }

      //output
      [key1, value1]

   This class will also allow you to print either only keys or values when you use the ``.Key`` or ``.Value`` properties of the dictionary.
   This is demonstrated in the `initialization replit example <https://replit.com/@launchcode/Dictionary-Initialization#main.cs>`_.
   Be sure to match your data types when you use this class.  


.. _accessing-dictionary-elements:

Accessing Dictionary Elements
--------------------------------

.. index:: ! bracket notation

If you want to access a key/value pair from within your dictionary, you can do so using the indexer or **bracket notation**.


.. admonition::  Example

   .. replit:: csharp
      :slug: DictionaryBracketNotation


      Dictionary<TKey, TValue> newDictionary = new Dictionary<TKey, TValue>
      {
         {key1, value1},
         {key2, value2},
         {key3, value3}
      };

      if(newDictionary.ContainsKey(key2))
      {
          //prints the values of key2 if contained within dictionary using bracket notation.
         Console.WriteLine(newDictionary[key2]);     
      } 



Dictionary Methods
------------------

Let’s collect some ``Dictionary`` methods as we have for ``List``. As we
said about ``Lists``, this is by no means a comprehensive catalog. For full
details on all properties and methods available, see the `documentation <https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2?view=netframework-4.8>`_ on the ``Dictionary`` class.

For the purposes of this table, we'll `create a dictionary <https://replit.com/@launchcode/DictionaryMethodsPractice-CSharp#main.cs>`_ to hold our solar system's
planets and the number of moons associated with each.

.. sourcecode:: csharp
   :linenos:

   Dictionary<string, int> moons = new Dictionary<string, int>();
   moons.Add("Mercury", 0);
   moons.Add("Venus", 0);
   moons.Add("Earth", 1);
   moons.Add("Mars", 2);
   moons.Add("Jupiter", 79);
   moons.Add("Saturn", 82);
   moons.Add("Uranus", 27);
   moons.Add("Neptune", 14);


.. list-table:: Dictionary Methods and Properties
   :header-rows: 1

   * - C# Syntax
     - Description
     - Example
   * - :ref:`Count <count-examples>`
     - Returns the number of items in the dictionary, as an ``int``.
     - ``moons.Count`` returns ``8``
   * - :ref:`Key <key-examples>`
     - Returns a collection containing all keys in the dictionary. This collection may be used in a
       ``foreach`` loop just as lists are, but the dictionary *may not be modified* within such a loop.
     - ``moons.Key`` returns
       ``{"Earth", "Mars", "Neptune", "Jupiter", "Saturn", "Venus", "Uranus", "Mercury"}``
   * - :ref:`Value <value-examples>`
     - Returns a collection containing all values in the dictionary. This collection may be used in a
       ``foreach`` loop just as lists are.
     - ``moons.Value`` returns ``{1, 2, 14, 79, 82, 0, 27, 0}``
   * - :ref:`Add() <dictionary-add-examples>`
     - Add a key/value pair to a dictionary.
     - ``moons.Add("Pluto", 5)`` adds ``"Pluto": 5`` to the ``moons``
   * - :ref:`Remove() <dictionary-remove-examples>`
     - Removes a key/value pair to a dictionary using key as a reference.
     - ``moons.Remove("Pluto")`` removes ``"Pluto": 5`` from the ``moons``
   * - :ref:`ContainsKey() <containsKey-examples>`
     - Returns a boolean indicating whether or not the dictionary contains a given key.
     - ``moons.ContainsKey("Earth")`` returns ``true``
   * - :ref:`ContainsValue() <containsValue-examples>`
     - Returns a boolean indicating whether or not the dictionary contains a given value.
     - ``moons.ContainsValue(79)`` returns ``true``



Check Your Understanding
-------------------------

.. admonition:: Question

   Given our ``Dictionary``,

   .. sourcecode:: csharp
      :linenos:

      moons = {
         "Mercury" = 0,
         "Venus" = 0,
         "Earth" = 1,
         "Mars" = 2,
         "Jupiter" = 79,
         "Saturn" = 82,
         "Uranus" = 27,
         "Neptune" = 14
      }

   What is the syntax to get the key names?

   #. ``Dictionary.Keys(moons);``
   #. ``moons.Keys();``
   #. ``moons.Keys;``
   #. ``moons.KeySet();``

.. ans - ``moons.Keys;``

.. admonition:: Question

   Given our ``Dictionary``,

   .. sourcecode:: csharp
      :linenos:

      moons = {
         "Mercury" = 0,
         "Venus" = 0,
         "Earth" = 1,
         "Mars" = 2,
         "Jupiter" = 79,
         "Saturn" = 82,
         "Uranus" = 27,
         "Neptune" = 14
      }

   What will ``moons["Mars"];`` return?

   #. ``2``

   #. ``{Mars: 2}``

   #. ``2.0``

   #. ``"Mars"``

.. ans - ``2``
