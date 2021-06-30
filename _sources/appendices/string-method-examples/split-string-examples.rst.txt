.. _split-string-examples:

======================
``Split`` Examples
======================

Returns a string array containing substrings that are deliminated by a specialize element.

.. admonition:: Note

   Split is not always the best method to create substrings.  
   For more information on this, please read the following `documentation <https://docs.microsoft.com/en-us/dotnet/standard/base-types/divide-up-strings>`_


General syntax for this method:

.. sourcecode:: csharp

   stringName.Split(deliminator)



.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      string duck = "Duck, duck, goose!";

      string[] substrings = duck.Split(' ');

      foreach(string sub in substrings)
      {
         Console.WriteLine(sub);
      }
   
   **Output**

   .. sourcecode:: csharp
      
      Duck,
      duck,
      goose!
