=====================
Exercises: Debugging
=====================

Imagine we are pirates running a space station. Captain Api Hook tells the crew the following:

   Avast, ye scurvy dogs! We be needn' ta fix yonder code!

   The cap'n in charge of clearing the shuttle for launch(code) be out with
   an illness, and ye be the next tech in line.

   Yer job is to evaluate the code and fix any errors. Remember, the lives
   of the crew rest squarely upon yer shoulders. Happy second day on the job!

   Yer directions are as follows:

   #. Launch the shuttle *only if* the fuel, crew and computer all check out OK.
   #. If a check fails, print that information to the console and scrub the
      launch (then scrub the deck).
   #. If all checks be successful, print a countdown to the console, then
      bellow "Liftoff!"


Debugging Practice
------------------

#. Fix **syntax errors** first. Run the following code as-is and squint yer
   eyes at the error message. Fix the mistake, and then re-run the code to
   check it.

   ::

      bool launchReady = false;
      int fuelLevel = 17000;
      
      if (fuelLevel >= 20000 
      { 
         Console.WriteLine("Fuel level cleared.");
         launchReady = true;
      } 
      else 
      {
         Console.WriteLine("WARNING: Insufficient fuel!");
         launchReady = false;
      }
      

   `Fix it at repl.it <https://repl.it/@launchcode/Debug1stSyntaxError-CSharp>`_

#. The next block of code hides two syntax errors. Run the code as-is to
   find the mistakes. *Tip*: Don't be too hasty, Matey! Only ONE error will
   be flagged at a time. Fix that ONE problem, and then re-run the code to
   check yer work. Avoid trying to fix multiple issues at once.

   ::

      
      
      bool launchReady = false;
      bool crewStatus = true;
      string computerStatus = "green";

      if (crewStatus && computerStatus === "green")
      {
         Console.WriteLine("Crew & computer cleared.");
         launchReady = true;
      } 
      else 
      {
         Console.WriteLine("WARNING: Crew or computer not ready!");
         launchReady = false;
      }

      if (launchReady) 
      {
         Console.WriteLine(("10, 9, 8, 7, 6, 5, 4, 3, 2, 1...");
         Console.WriteLine("Fed parrot...");
         Console.WriteLine("Ignition...");
         Console.WriteLine("Liftoff!");
      } 
      else 
      {
         Console.WriteLine("Launch scrubbed.");
      }

   `Fix it at repl.it <https://repl.it/@launchcode/DebugSyntaxErrors2-CSharp>`__

#. Watch out! **Warning** ahead. Remember to examine the warning message for
   clues about what is going wrong. Pay close attention to any line
   numbers mentioned in the message - these will help ye locate and repair
   the mistake in the code.

   ::

      bool launchReady = false;
      int fuelLevel = 17000;
      
      if (fuelLevel >= 20000)
      {
         Console.WriteLine("Fuel level cleared.");
         launchReady = true;
      } 
      else 
      {
         Console.WriteLine("WARNING: Insufficient fuel.");
         launchReady = false;
      }

   `Fix it at repl.it <https://repl.it/@launchcode/DebugRuntimeErrors1-CSharp>`__

#. *Arrr!*  Now find and fix the compiler error in a longer code sample.

   ::


      bool launchReady = false;
      int fuelLevel = 27000;
      
      if (fuelLevel >= 20000) 
      {
         Console.WriteLine("Fuel level cleared.");
         launchReady = true;
      } 
      else 
      {
         Console.WriteLine("WARNING: Insufficient fuel!");
         launchReady = false;
      }
      
      if (launchReady) 
      {
         Console.WriteLine("10, 9, 8...");
         Console.WriteLine("Fed parrot...");
         Console.WriteLine("6, 5, 4...");
         Console.WriteLine("Ignition...");
         Consoul.WriteLine("3, 2, 1..."); 
         Console.WriteLine("Liftoff!");
      } 
      else
      {
         Console.WriteLine("Launch scrubbed.");
      }


   `Fix it at repl.it <https://repl.it/@launchcode/DebugRuntimeErrors2-CSharp>`__

#. Solve **logic errors** last. Logic errors do not generate warning
   messages or prevent the code from running, but the program still does
   not work as intended. (Refer to :ref:`debugging logic errors <debugging-logic-errors>` if ye need to
   review).

   #. First, run this sample code as-is and examine the output.

      ::

         bool launchReady = false;
         int fuelLevel = 17000;
         bool crewStatus = true;
         string computerStatus = "green";
         
         if (fuelLevel >= 20000) 
         {
            Console.WriteLine("Fuel level cleared.");
            launchReady = true;
         } 
         else
         {
            Console.WriteLine("WARNING: Insufficient fuel!");
            launchReady = false;
         }

         if (crewStatus && computerStatus == "green")
         {
            Console.WriteLine("Crew & computer cleared.");
            launchReady = true;
         } 
         else 
         {
            Console.WriteLine("WARNING: Crew or computer not ready!");
            launchReady = false;
         }
         
         if (launchReady) 
         {
            Console.WriteLine("10, 9, 8, 7, 6, 5, 4, 3, 2, 1...");
            Console.WriteLine("Liftoff!");
         } 
         else 
         {
            Console.WriteLine("Launch scrubbed.");
         }

         

      `Run it at repl.it <https://repl.it/@launchcode/DebugLogicErrors1-CSharp>`__

      Should the shuttle have launched? Did it?

   #. Let's break the code down into smaller chunks. Consider the first if/else block below. Add ``Console.WriteLine(launchReady)`` after this block, then run the program.

      ::

         bool launchReady = false;
         int fuelLevel = 17000;
         
         if (fuelLevel >= 20000) 
         {
            Console.WriteLine("Fuel level cleared.");
            launchReady = true;
         } 
         else 
         {
            Console.WriteLine("WARNING: Insufficient fuel!");
            launchReady = false;
         }

      `Run it at repl.it <https://repl.it/@launchcode/DebugLogicErrors2-CSharp>`__

      Given the ``fuelLevel`` value, should ``launchReady`` be ``true`` or ``false`` after the check? Is the program behaving as expected?

   #. Now consider the second if/else block. Add another ``Console.WriteLine(launchReady)`` after this block and run the program.

      ::

         bool launchReady = false;
         int crewStatus = true;
         string computerStatus = "green";
         
         if (crewStatus && computerStatus == "green")
         {
            Console.WriteLine("Crew & computer cleared.");
            launchReady = true;
         } 
         else 
         {
            Console.WriteLine("WARNING: Crew or computer not ready!");
            launchReady = false;
         }


      `Run it at repl.it <https://repl.it/@launchcode/DebugLogicErrors3-CSharp>`__

      Given ``crewStatus`` and ``computerStatus``, should ``launchReady`` be ``true`` or ``false`` after this check? Is the program behaving as expected?

   #. Now consider both if/else blocks together (keeping the added ``Console.WriteLine`` lines). Run the code and examine the output.

      ::

         bool launchReady = false;
         int fuelLevel = 17000;
         bool crewStatus = true;
         string computerStatus = "green";
         
         if (fuelLevel >= 20000) 
         {
            Console.WriteLine("Fuel level cleared.");
            launchReady = true;
         } 
         else 
         {
            Console.WriteLine("WARNING: Insufficient fuel!");
            launchReady = false;
         }
         
         Console.WriteLine(launchReady);
         
         if (crewStatus && computerStatus == "green")
         {
            Console.WriteLine("Crew & computer cleared.");
            launchReady = true;
         } 
         else 
         {
            Console.WriteLine("WARNING: Crew or computer not ready!");
            launchReady = false;
         }
         
         Console.WriteLine(launchReady);

      `Run it at repl.it <https://repl.it/@launchcode/DebugLogicErrors4-CSharp>`__

      Given the values for ``fuelLevel``, ``crewStatus`` and ``computerStatus``, should ``launchReady`` be ``true`` or ``false``? Is the program behaving as expected?

   #. Ahoy, Houston! We spied a problem! The value of ``launchReady`` assigned
      in the first ``if/else`` block got changed in the second ``if/else``
      block. Dangerous waters, Matey. Since the issue is with ``launchReady``,
      ONE way to fix the logic error is to use a different variable to store the
      fuel check result. Update yer code to do this. Verify that yer change works
      by updating the ``Console.WriteLine`` statements.

      `Fix it at repl.it <https://repl.it/@launchcode/DebugLogicErrors5-CSharp>`__

   #. Almost done, so wipe the sweat off yer brow! Add a final ``if/else`` block
      to print a countdown and "Liftoff!" if all the checks pass, or print "Launch
      scrubbed" if any check fails.

      Blimey! That's some good work. Now go feed yer parrot.
