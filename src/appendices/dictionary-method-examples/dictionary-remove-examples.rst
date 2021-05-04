.. _dictionary-remove-examples:

``Remove`` Examples
==============================

Removes existing key/value pair from a dictionary using the **key** as the reference.

.. sourcecode:: csharp

   dictionaryName.Remove(key);


.. admonition:: Example   
   
   .. sourcecode:: csharp
   
      Dictionary<string, int> moons = new Dictionary<string, int>
      {
         {"Mercury", 0},
         {"Venus", 0},
         {"Earth", 1}, 
         {"Mars", 2}, 
         {"Jupiter", 79},
         {"Saturn", 82},
         {"Uranus", 27},
         {"Neptune", 14},
         {"Pluto", 5}
      };

      Console.WriteLine(moons.ContainsValue(3));	
	   Console.WriteLine(moons.ContainsValue(82));

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



   .. sourcecode:: csharp

      //oops forgot Pluto's not considered a planet

      moons.Remove("Pluto");

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
