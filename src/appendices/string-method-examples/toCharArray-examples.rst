.. _string-toCharArray-examples:

``ToCharArray`` Examples
==========================

Copies characters from string into character array.  Can be used for entire string, or with sections of a string.

General syntax for this method: 
   
.. sourcecode:: csharp

   //Option 1
   stringName.ToCharArray();

   //Option 2
   stringName.ToCharArray(startIndex, rangeIndex);

This copies characters of a string into an array.  

.. admonition:: Example

   .. sourcecode:: csharp

      string nonprofit = "LaunchCode";

      //Option 1
      nonprofit.ToCharArray();

      //Option 2
      nonprofit.ToCharArray(3, 6);

   **Output**

   .. sourcecode:: bash


      LaunchCode
      nchCod


This method will grow in usefulness once you learn about arrays and array methods.
