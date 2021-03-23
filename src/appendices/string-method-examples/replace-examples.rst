.. _string-replace-examples:

======================
``Replace`` Examples
======================

Returns a new string where **all** occurances of a specified character or string has been replaced.

The general syntax for this method is:

.. sourcecode:: csharp

   stringName.Replace(searchChar, replacementChar);

Given a search string ``searchChar`` and a replacement value ``replacementChar``, this method returns a
new instance of ``stringName`` with the *all* occurrences of ``searchChar`` replaced by ``replacementChar``.


.. admonition:: Example

   .. sourcecode:: csharp
      
      string forestAnimal = "box";
      Console.WriteLine(forestAnimal.Replace('b', 'f'));

      string rabbitFood = "carrot";
      Console.WriteLine(rabbitFood.Replace('r', 'q'));
      
      string nonprofit = "Launch Code";
      Console.WriteLine(nonprofit.Replace(" ", ""));

   **Output**

   .. sourcecode:: bash

      fox
      caqqot
      LaunchCode

