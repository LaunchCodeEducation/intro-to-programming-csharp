.. _add-examples:

``Add`` Method
=================


Adds object to the *end* of the List.  Often used when initializing a new list object.

.. sourcecode:: csharp

   listName.Add(object);




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
	


   .. sourcecode:: csharp

      //Oops! forgot Pluto

      planets.Add("Pluto");


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
      Pluto