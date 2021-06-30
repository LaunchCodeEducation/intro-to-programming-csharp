.. _remove-examples:

``Remove`` Method
======================

Used to remove *first* instanace of a specific element from a list.

.. sourcecode:: csharp

   listName.Remove(element);



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
         "Neptune",
         "Pluto"
      };
      

      planets.Remove("Pluto");

      foreach(string planet in planets)
      {
         Console.WriteLine(planet);
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


There are a `few <https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.removeall?view=net-5.0>`_ `other <https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.removeat?view=net-5.0>`_ Remove methods if you are interested.