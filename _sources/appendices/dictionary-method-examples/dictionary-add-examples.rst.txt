.. _dictionary-add-examples:

``Add`` Examples
=======================

Add a new key/value pair to a dictionary object.

.. sourcecode:: csharp

   Dictionary<TKey, TValue> methodDictionary = new Dictionary<TKeym TValue>();
      methodDictionary.Add(key1, value1);
      methodDictionary.Add(key2, value2);
      methodDictionary.Add(key3, value3);


Let's create a dictionary with the planets and the number of moons.

.. admonition:: Example

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

      foreach(KeyValuePair<string,int> moon in moons)
      {
         Console.WriteLine(moon);
      }

   **Output**

   .. sourcecode:: csharp

      [Mercury, 0]
      [Venus, 0]
      [Earth, 1]
      [Mars, 2]
      [Jupiter, 79]
      [Saturn, 82]
      [Uranus, 27]
      [Neptune, 14]



   .. sourcecode:: csharp

      //oops forgot Pluto

      moons.Add("Pluto", 5);

      foreach(KeyValuePair<string,int> moon in moons)
      {
         Console.WriteLine(moon);
      }

   **Output**

   .. sourcecode:: csharp

      [Mercury, 0]
      [Venus, 0]
      [Earth, 1]
      [Mars, 2]
      [Jupiter, 79]
      [Saturn, 82]
      [Uranus, 27]
      [Neptune, 14]
      [Pluto, 5]
      


