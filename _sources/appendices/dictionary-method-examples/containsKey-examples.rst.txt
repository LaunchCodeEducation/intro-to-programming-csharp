.. _containsKey-examples:

``ContainsKey`` Examples
===========================

Determines if dictionary contains specific key element.  Returns a ``bool``.



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


      Console.WriteLine(moons.ContainsKey("Pluto"));	
	   Console.WriteLine(moons.ContainsKey("Earth"));

   **Output**

   :: 

      False
      True