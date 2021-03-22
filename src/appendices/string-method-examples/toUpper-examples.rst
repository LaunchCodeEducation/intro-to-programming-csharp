.. _string-touppercase-examples:

``toUpperCase`` Examples
========================

The general syntax for this method is:

.. sourcecode:: csharp

   stringName.ToUpper();

This method returns a copy of ``stringName`` with all lowercase letters replaced by their uppercase counterparts. It leaves non-alphabetic characters unchanged.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine("LaunchCode".ToUpper());
      Console.WriteLine("launchcode".ToUpper());
      Console.WriteLine("C Sharp rocks!".ToUpper());

   **Output**

   ::

      LAUNCHCODE
      LAUNCHCODE
      C SHARP ROCKS!
