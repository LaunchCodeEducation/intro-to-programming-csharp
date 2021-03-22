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


.. admonition:: Example

   When dealing with user input, we can not account for capitalization consistency, 
   which can cause errors in our code if we are looking for a specfic answer, such as 
   Using a method like ``ToUpper`` or ``ToLower`` can make 

   This program standardizes an email address by converting it to all lowercase characters.

   .. sourcecode:: csharp

      string input = "fake.email@LAUNCHCODE.ORG";
      string email = input.ToLower();
      Console.WriteLine(email);

   **Output**

   .. sourcecode:: bash

      fake.email@launchcode.org

.. admonition:: Warning

   This example is a bit crude, since the portion of an email address *before*
   the ``@`` symbol is allowed to be case-sensitive. When standardizing the
   case of an email in a real application, we would want to be more precise and
   only convert the domain portion to lowercase characters.
