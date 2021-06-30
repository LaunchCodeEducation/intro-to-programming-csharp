.. _string-trim-examples:

``Trim`` Examples
==================

The general syntax for this method is:

.. sourcecode:: csharp

   stringName.Trim();

.. index::
   single: whitespace; leading
   single: whitespace; trailing

This method returns a new string with any leading or trailing
whitespace removed. Whitespace characters are those that do not display
anything on the screen, such as spaces and tabs.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine("Saint Louis ".Trim());
      Console.WriteLine(" Saint Louis".Trim());
      Console.WriteLine(" Saint Louis ".Trim());

   **Output**

   .. sourcecode:: bash

      Saint Louis
      Saint Louis
      Saint Louis


.. admonition:: Example

   When typing an email address into a web site, a user may inadvertently type a space before and/or after the email address. We can clean up such input using the ``trim`` method.

   This example cleans up user input with ``trim``.

   .. sourcecode:: csharp

      string input = " fake.email@launchcode.org ";
      string email = input.Trim();
      Console.WriteLine(email);

   **Output**

   .. sourcecode:: bash

      fake.email@launchcode.org
