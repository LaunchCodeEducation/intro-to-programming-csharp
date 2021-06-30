.. _list-sort-examples:

``Sort`` Method
======================

Sorts elements in list in ascending order.

.. sourcecode:: csharp

   listName.Sort();



.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      List<string> planets = new List<string>()
      {
         "Mercury",
         "Venus",
         "Earth",
         "Mars",
         "Jupiter",
         "Saturn",
         "Uranus",
         "Neptune"
      };

      planets.Sort();

      foreach(string planet in planets)
      {
         Console.WriteLine(planet);
      }

   **Output**

   ::

      Earth
      Jupiter
      Mars
      Mercury
      Neptune
      Saturn
      Uranus
      Venus

