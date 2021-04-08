.. _string-substring-examples:

``Substring`` Examples
========================

Substring can be used two ways.  The first is simply to create a new string from the characters starting at the ``startIndex`` to the end of the sting.  
The other version creates a new string at the ``startIndex`` followed by as many chracters as specified by the ``rangeIndex``.

The general syntax for this method is:
   
.. sourcecode:: csharp
   
   //Option 1
   stringName.Substring(startIndex);

   //Option 2
   stringName.Substring(startIndex, rangeIndex);



Both Option 1 and 2 return a new substring of ``stringName``.


.. admonition:: Example 

   .. sourcecode:: csharp

      //Option 1
      Console.WriteLine("LaunchCode".Substring(4));
   
      //Option 2
      Console.WriteLine("LaunchCode".Substring(4, 3));
   
   **Output**
   
   .. sourcecode:: csharp

      //Option 1
      chCode

      //Option 2
      chC


On some websites, the portion of an email address before the ``@`` symbol is used as a username. 
We can extract this portion of an email address using ``Substring`` in conjunction with ``IndexOf``.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
   
      string input = "fake.email@launchcode.org";
      int atIndex = input.IndexOf("@");
      string username = input.Substring(0, atIndex);
      Console.WriteLine(username);

   **Output**

   .. sourcecode:: bash

      fake.email
