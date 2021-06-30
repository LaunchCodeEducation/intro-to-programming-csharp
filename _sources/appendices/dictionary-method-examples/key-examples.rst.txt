.. _key-examples:

``Key`` Examples
===========================

A **property** that isolates the keys of a dictionary.   

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
         Console.WriteLine(moon.Key);
      }

   **Output**

   ::

      Mercury
      Venus
      Earth
      Mars
      Jupiter
      Saturn
      Uranus
      Neptune


