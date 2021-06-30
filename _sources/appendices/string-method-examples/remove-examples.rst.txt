.. _string-remove-examples:

``Remove`` Examples
========================

Remove can be used two ways.  The first is simply to remove characters from a ``startIndex`` to the end of the sting, thus creating a new string instance.  
The other version creates a new string by removing characters between the ``startIndex`` and ``rangeIndex``.

The general syntax for this method is:

.. sourcecode:: csharp
   
   //Option 1
   stringName.Remove(startIndex);

   //Option 2
   stringName.Remove(startIndex, rangeIndex);



Both Option 1 and 2 return a new instance of ``stringName``.


.. admonition:: Example 

   .. sourcecode:: csharp

      //Option 1
      Console.WriteLine("LaunchCode".Remove(4));
   
      //Option 2
      Console.WriteLine("LaunchCode".Remove(4, 3));
   
   **Output**
   
   .. sourcecode:: csharp

      //Option 1
      Laun

      //Option 2
      Launode


Some email providers, including Gmail, allow users to put a ``.`` anywhere before the ``@`` symbol. 
This means that ``fake.email@launchcode.org`` is the same as ``fakeemail@launchcode.org``.
To remove the ``.`` before the ``@`` symbol in an email address, we can use the ``Remove`` and ``IndexOf`` methods.

.. admonition:: Example

   .. sourcecode:: csharp
      
      string email = "fake.email@launchcode.org";
      int dotIndex = email.IndexOf(".");
      string dotFreeEmail = email.Remove(dotIndex, 1);
      Console.WriteLine(dotFreeEmail);

   **Output**

   .. sourcecode:: bash

      fakeemail@launchcode.org


