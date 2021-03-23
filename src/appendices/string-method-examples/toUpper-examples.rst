.. _string-toupper-examples:

``ToUpper`` Examples
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


The ability to convert a string to a single letter case, either Upper or Lower, can be very helpful when working with user input.



.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      Console.WriteLine("Would you like to play a game?  YES/NO");
      string playerChoice = Console.ReadLine();
      string yesOrNo = playerChoice.ToUpper();

      if(yesOrNo == "YES")
      {
         Console.WriteLine("How about Global Thermonuclear War?");
      }
      else
      {
         Console.WriteLine("Not even Tic-Tac-Toe?");
      }

