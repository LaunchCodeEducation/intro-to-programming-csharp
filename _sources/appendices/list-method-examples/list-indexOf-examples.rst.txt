.. _list-indexOf-examples:

``IndexOf`` Method
======================

Returns the index number of specified element.  If element is *not* in the list, returns -1.

.. sourcecode:: csharp

   listName.IndexOf(element);


Can also be used to verify the location of an element.

.. sourcecode:: csharp

   listName.IndexOf(element, index);


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

      Console.WriteLine(planets.IndexOf("Jupiter"));
      Console.WriteLine(planets.IndexOf("Mars", 7));
      Console.WriteLine(planets.IndexOf("Pluto"));

   **Output**

   ::

      4
      -1    
      -1

