.. _contains-examples:

``Contains`` Method
======================

Determines if an element is contained in the List.  Returns a ``bool`` value.

.. sourcecode:: csharp

   listName.Contains(element);


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

      bool plutoCheck = planets.Contains("Pluto");
      Console.WriteLine(plutoCheck);

   **Output**

   ::

      False

