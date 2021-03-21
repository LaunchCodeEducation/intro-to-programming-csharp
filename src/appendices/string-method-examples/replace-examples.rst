.. _string-replace-examples:

======================
``replace`` Examples
======================

The general syntax for this method is:

.. sourcecode:: csharp

   stringName.Replace(searchChar, replacementChar);

Given a search string ``searchChar`` and a replacement value ``replacementChar``, this method returns a copy of ``stringName`` with the *all* occurrences of ``searchChar`` replaced by ``replacementChar``.


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

.. admonition:: Example

   Some email providers, including Gmail, allow users to put a ``.`` anywhere before the ``@`` symbol. This means that ``fake.email@launchcode.org`` is the same as ``fakeemail@launchcode.org``.

   Remove the ``.`` before the ``@`` symbol in an email address.

   .. sourcecode:: js
   
      let input = "fake.email@launchcode.org";
      let email = input.replace(".", "");
      console.log(email);

   **Output**

   .. sourcecode:: bash

      fakeemail@launchcode.org

   This example illustrates a common use case of ``replace``, which is to *remove* a character by replacing it with the empty string.

.. warning::

   Notice in the last example that if there is not a ``.`` before the ``@`` symbol, the ``.`` that is part of the domain, ``launchcode.org`` would be inadvertently removed. In a real application, we would want to isolate the portion in front of ``@`` using ``slice``.
