.. _string-contains-examples:

``Contains`` Examples
=====================

The general syntax for this method is:

.. sourcecode:: csharp

   stringName.Contians(substr);

Given a candidate substring, this method returns the boolean value if the substring is contained within the string. 
Can also be used to locate characters within a string.

.. admonition:: Example
   
   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine("LaunchCode".Contains("C"));

      Console.WriteLine("LaunchCode".Contains("A"));

   **Output**

   ::

      True
      False

.. admonition:: Example

   An email address must contain an ``@`` symbol. Checking for the presence of this symbol is a part of email address verification in most programs.

   .. sourcecode:: csharp
      :linenos:
   
      string input = "fake.email@launchcode.org";
      bool validEmail = input.Contains('@');
      
      if (validEmail) {
         Console.WriteLine("Email contains @");
      } else {
         Console.WriteLine("Invalid email");
      }

   **Output**

   .. sourcecode:: bash

      Email contains @   
