.. _list-reverse-examples:

``Reverse`` Method
======================

Reverses the order of the elements contained in a list based on index number.  
Can also reverse a range of elements within a list

.. sourcecode:: csharp

   listName.Reverse();     //reverses entire list
   listName.Reverse(3,2)   //reverse starting at index 3 for 2 indices


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

      planets.Reverse()
      
      foreach(string planet in planets)
      {
         Console.WriteLine(planet);
      }

   **Output**

   ::

      Neptune
      Uranus
      Saturn
      Jupiter
      Mars
      Earth
      Venus
      Mercury
	


   .. sourcecode:: csharp

      //Reverse only a few

      planets.Reverse(1,4);


      foreach(string planet in planets)
      {
         Console.WriteLine(planet);
      }
   
   **Output**

   ::

      Mercury
      Jupiter
      Mars
      Earth
      Venus
      Saturn
      Uranus
      Neptune