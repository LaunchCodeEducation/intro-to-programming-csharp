.. _string-indexof-examples:

=====================
``IndexOf`` Examples
=====================

The general syntax for this method is:

.. sourcecode:: csharp

   stringName.IndexOf(substr);

Given a candidate substring, this method returns the integer index of the *first* occurrence of the substring in the string. If the substring does not occur in the string, -1 is returned.

.. admonition:: Example
   
   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine("LaunchCode".IndexOf('C'));

      Console.WriteLine("LaunchCode".IndexOf('A'));

      Console.WriteLine("dogs and dogs and dogs!".IndexOf("dog"));

   **Output**

   ::

      6
      -1
      0

.. admonition:: Example

   An email address must contain an ``@`` symbol. Checking for the presence of this symbol is a part of email address verification in most programs.

   .. sourcecode:: csharp
      :linenos:
   
      string input = "fake.email@launchcode.org";
      int atIndex = input.IndexOf('@');
      
      if (atIndex > -1) {
         Console.WriteLine("Email contains @");
      } else {
         Console.WriteLine("Invalid email");
      }

   **Output**

   .. sourcecode:: bash

      Email contains @   
