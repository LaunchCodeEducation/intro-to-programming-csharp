.. _containsValue-examples:

``ContainsValue`` Examples
==============================

Determines whether the dictionary contains a certain value.  Returns a ``bool``.




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

   ::

      False
      True


