.. _toArray-examples:

``ToArray`` Method
======================

Copies the elements within the list into an array.

This does *not* create the array, like ``ToCharArray``.  You must declare the array of the same size as your list.

.. sourcecode:: csharp

   // Option A
   string[] listArray = new string[listName.Count];
   listArray = listName.ToArray();

   // Option B
   string[] listArray = listName.ToArray();



.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      List<string> planets = new List<string>();
         planets.Add("Mercury");
         planets.Add("Venus");
         planets.Add("Earth");
         planets.Add("Mars");
         planets.Add("Jupiter");
         planets.Add("Saturn");
         planets.Add("Uranus");
         planets.Add("Neptune");

      string[] planetArray = planets.ToArray();

      foreach(string planet in planetArray) 
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