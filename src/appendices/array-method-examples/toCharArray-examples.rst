.. _toCharArray-examples:

``ToCharArray`` Examples
==========================

``ToCharArray`` is a string method, but a string method that converts a string into a character array.

This can be useful if you need to change an element in your string without creating a new string.  
Remember that strings are immutable, but arrays are mutable.  

The general syntax for this method is:

.. sourcecode:: csharp

   char[] arrayName = stringName.ToCharArray();

Now you have access to all the characters in your string.  
This could be useful if you need to fix a typo, if you are counting the numbers of a specific char, etc.

.. admonition:: Example

   Update the typo in the ``string name``.

   .. sourcecode:: csharp
      :linenos:

      string name = "Launchcode";

      char[] nameArray = name.ToCharArray();

      int findTypo = Array.LastIndexOf(nameArray,'c');

      Console.WriteLine(findTypo);

      nameArray[6] = 'C';
      name = string.Join("", nameArray);

      Console.WriteLine(name);

   ::

      6
      LaunchCode

In this example, we used ``LastIndexOf`` to find the index of the LAST ``'c'``.  We reassigned the ``'c'`` to ``'C'``.
To ``Join`` the chars back into the string, we used the **empty string**, or ``""``.  
Now when we print ``name`` we have it formatted the way we want it.


