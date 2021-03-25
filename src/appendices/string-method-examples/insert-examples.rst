.. _string-insert-examples:

``Insert`` Examples
=====================

The general syntax for this method is:

.. sourcecode:: csharp

   stringName.Insert(index, "stringValue");

This method returns a new string where a specific string has been inserted at a specific index.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine("HelloWorld!".Insert(5, " "));
      Console.WriteLine("fake.emaillaunchcode.org".Insert(10, "@"));
      Console.WriteLine("abde".Insert(2, "c"));

   **Output**

   .. sourcecode:: bash

      Hello World!
      fake.email@launchcode.org
      abcde


.. admonition:: Example

   This method could be used to create something like a department specific username.  

   This example adds department identification to a username with ``Insert``.

   .. sourcecode:: csharp

      string input = "userName";
      string devDeptCode = input.Insert(0, "019-wd:");
      Console.WriteLine(devDeptCode);

   **Output**

   .. sourcecode:: bash

      019-wd:userName
