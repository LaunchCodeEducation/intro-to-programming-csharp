.. _value-examples:

``Value`` Examples
===========================

A **property** that isolates the values of a dictionary.

   
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

      foreach(KeyValuePair<string,int> moon in moons)
      {
         Console.WriteLine(moon.Value);
      }

   **Output**

   ::

      0
      0
      1
      2
      79
      82
      27
      14
      5


