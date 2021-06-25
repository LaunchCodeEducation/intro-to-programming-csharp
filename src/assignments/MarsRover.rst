Assignment #3: Mars Rover
=========================

This task puts your unit testing, modules making, and exception handling knowledge to
use by writing tests and classes for the Mars rover named Curiosity.

.. figure:: figures/curiosity-rover-selfie.jpg
   :alt: Image of Curiosity rover taken by the rover on Mars.

   Selfie of Curiosity on Mars.

You will create a simulation for issuing commands to Curiosity. The idea is to
create a *command* at mission control, convert that command into a *message*
send it to the *rover*, then have the rover respond to that message.

We will provide descriptions of the required features you need to implement in 
three separate classes:

#. ``Command``: 
   A type of object containing a ``CommandType`` field. ``CommandType`` is one
   of the given strings in the table below. Some ``CommandTypes`` are coupled with
   a ``NewPosition`` property and some are coupled with a ``NewMode`` property. Every 
   ``Command`` object is a single instruction to be delivered to the rover.
#. ``Message``:
   A ``Message`` object has a ``Name`` field and can contain several ``Command`` objects. 
   ``Message`` is responsible for bundling the commands from mission control and 
   delivering them to the rover.
#. ``Rover``:
   An object representing Curiosity, the mars rover. This class contains information on the rover's
   ``Position``, operating ``Mode``, and ``GeneratorWatts``. It will also contain a method 
   that you will write, ``ReceiveMessage``. This method will include conditional statements 
   for each type of command the rover receives and updates the rover's properties. 

In true TDD form, you will be asked to first write the appropriate units tests for 
these features, then write the code in the given class to pass those tests. 


Getting Started
---------------

#. Fork the `Mars rover starter code <https://github.com/LaunchCodeEducation/MarsRoverCSharp>`__.
#. Write a unit test for each test item listed below.

   .. note::
   
      Two ``Command`` object tests have been created for you as examples.

#. Use :ref:`test-driven development (TDD) <tdd>` to create each of the
   classes described below.

#. You are responsible for creating the ``Rover.ReceiveMessage()`` method. 


How-To TDD
----------

Recall that in TDD, you write the test for a given behavior before you code the
actual function. Feel free to review the
:ref:`Test/Code cycle <test-code-cycle>` while you work on this project.

a. Focus on one test at a time.
b. Write the test and *then* create the code to make it pass.
c. Only write the minimum amount of code needed to make the test pass.
d. There are some constraints on how you can implement these features. A description
   of each class is below.

Each numbered item describes a test. *You should use the given phrases as the
test method names* when creating your tests. 

You must create 13 tests (14, if you do the bonus) for this assignment.

.. admonition:: Warning

   Did you catch the part about only working on ONE test at a time? Do NOT try
   to write all of the tests at once. Doing so will be inefficient and will
   cause excessive frustration.


A. ``Command``
--------------

.. _command-class:

``Command`` Class
^^^^^^^^^^^^^^^^^

We'll follow TDD practices for the creation of ``Message`` and ``Rover``, but for 
this class, ``Command``, we've provided the functionality. ``Command`` is already 
written for you and you do not need to modify it to write passing tests. Open up and 
examine the file ``Command.cs``. 

#. This class builds an object with three fields: ``CommandType``, ``NewPosition``, and ``NewMode``.

   a. ``CommandType`` is a string that represents the type of command. A command 
      type will be one of the following: ``'MODE_CHANGE'`` or ``'MOVE'``.
      
      i. To peek ahead at the full functionality of these types, refer to 
         :ref:`Command Types table <command-types-table>`. 

   b. ``NewPosition`` is an ``int`` value provided in conjunction with a "MOVE" command type.

   c. ``NewMode`` is a ``string`` value provided in conjunction with a "MODE_CHANGE" command type.

.. admonition:: Example

   .. sourcecode:: csharp

      Command ModeCommand = new Command("MODE_CHANGE", "LOW_POWER");
      Command MoveCommand = new Command("MOVE", 12000);

   ``'MODE_CHANGE'`` and ``'MOVE'`` are passed in and set the ``CommandType`` value
   by all constructors.

   ``'LOW_POWER'`` and 12000 are passed in as ``value``. Different command 
   types require different kinds of values and there are two different constructors to
   handle each command type and its corresponding value.
   
   Don't worry about the mode options for now. To peek ahead, see 
   :ref:`Rover Modes table <rover-modes-table>`.

Now that we've gone over the class, let's check out the tests.

.. _command-tests:

``Command`` Tests
^^^^^^^^^^^^^^^^^

To begin, open and examine ``MarsRoverTests/CommandTests.cs``. Two tests have been created for 
you. When a user creates a new ``Command`` object from the class, we want to make 
sure they pass a command type as the first argument.

Test 1 
~~~~~~
   
Note that the test name reads, "ArgumentNullExceptionThrownIfCommandTypeIsNullOrEmpty".

a. Look at the constructors in ``Command.cs``. In each, a null or empty ``commandType``
   argument results in an exception thrown. 
b. Use the "Tests" tab in Visual Studio to run the Command unit tests. 
   Verify that the tests pass. 
c. Next, change the first assertion in ``CommandTests.cs`` to expect ``message: 'Oops'``. 
   Run the tests again to verify that the test fails (the error message did not match
   ``"Command type required."``).
d. Restore the ``Assert`` method's expected argument to be ``"Command type required."``.

Test 2
~~~~~~

Look at the second ``Command`` test called "ConstructorSetsCommandType". 
This test checks that the constructor in the ``Command``
class correctly sets the ``CommandType`` property in the new object.

a. Without editing, ``Command.cs`` contains the correct code. Click "Run" to 
   verify that the first and second tests both pass.
b. You do not need to catch an exception in this test.
c. You may not need to know the specific types of commands to write this test. In fact, you can change the ``commandType``
   input to any string value and run the test. Does it still pass?

Test 3 
~~~~~~

Look at the third test. "ConstructorSetsInitialNewPositionValue" is the 
method name. This test checks that the constructor
correctly sets the ``NewPosition`` field in the new ``Command`` object.

a. You may not need to know a proper ``NewPosition`` value in order to write this test.
   
Run the tests to verify that all 3 command tests pass.

Test 4 
~~~~~~

Write a fourth ``Command`` class test. This should be called "ConstructorSetsInitialNewModeValue".
This test is responsible for checking that the third field on the ``Command`` class, ``NewMode``
is set by a ``Command`` constructor. 

a. Write the test to check that a ``Command`` constructor that is passed a second string value
   will set that string value to ``NewMode``.
b. Run the test suite. This new test will initially fail.
c. Add an additional constructor to ``Command`` that sets the ``NewMode`` field when 
   passed a string value.
d. Re-run the tests. Your new test should pass now.

.. admonition:: Note

   As you move through the remaining instructions, the amount of guidance will
   decrease. Refer to your earlier, passing tests to help you construct new
   tests and passing code.

B. ``Message``
--------------

Recall, the role of a message object is to bundle commands to send to the rover.

.. _message-class:

``Message`` Class
^^^^^^^^^^^^^^^^^

#. This class builds an object with two properties.
   ``Message(string name, Command[] commands)``

   a. ``Name`` is a string that is the name of the message.
   b. ``Commands`` is an array of ``Command`` objects.

.. admonition:: Example

   .. sourcecode:: csharp

      Command[] commands = {new Command("MODE_CHANGE", "LOW_POWER"), new Command("MOVE", 500)};
      Message newMessage = new Message("Test message with two commands", commands);

``Message`` Tests
^^^^^^^^^^^^^^^^^

At the same level as ``CommandTests``, open the test file ``MessageTests`` and 
write the unit tests for the ``Message`` class as described below.

.. admonition:: Tip

   Inside this test file, you will have to create at least one ``commands`` 
   array, fill it with some ``Command`` objects, and pass it into the ``Message``
   constructors you are testing.

Test 5
~~~~~~

This unit test has been started for you. The title, "ArgumentNullExceptionThrownIfNameNotPassedToConstructor"
indicates that it will look similar to the first test in the ``CommandTests`` file.
Review the first test in ``CommandTests`` for an example of how to write this test.

a. When you run the tests, the test will likely fail because you have not written 
   the class to include this feature.

b. Look at the code in ``Command``. Use that to help you write the
   ``Message`` class in ``Message.cs`` so that your test passes. Refer to
   the :ref:`Message Class <message-class>` description above for more
   details.

Test 6
~~~~~~

Use "ConstructorSetsName" as the test name. The test confirms
that the constructor in the ``Message`` class correctly sets the
``Name`` property in a new message object.

Test 7
~~~~~~

Use "ConstructorSetsCommandsField" as the method name.
This test confirms that the ``Commands`` property of a new message object
contains the data passed in from the ``Message(name, commands)`` call.

.. admonition:: Warning

   You are moving onto the red planet now. Be prepared for fewer instructions.


C. ``Rover``
------------

``Rover`` receives a message object, updates its properties from the message, and 
returns the results.

.. _rover-class:

Rover Class
^^^^^^^^^^^

This class builds a rover object with a few properties. It will also contain
a method called ``ReceiveMessage`` to handle updates to its properties.

#. ``public Rover(int position)``

   a. ``position`` is a number representing the rover's position.
   b. Sets ``Position`` to ``position``
   c. Sets ``Mode`` to ``'NORMAL'``
   d. Sets default value for ``generatorWatts`` to 110

#. ``public void ReceiveMessage(Message message)``

   a. ``message`` is a ``Message`` object
   b. This method does not return anything
   c. It applies the contents of the ``Message`` sent to update certain properties of the rover object

      i. Details about how to respond to different commands are in the
         :ref:`Command Types table <command-types-table>`.

.. admonition:: Example

   .. sourcecode:: csharp

      Command[] commands = {new Command("MOVE", 5000)};
      Message newMessage = new Message("Test message with one command", commands);
      Rover newRover = new Rover(98382);    // Passes 98382 as the rover's position.
      
      Console.WriteLine(newRover.ToString());
      
      newRover.ReceiveMessage(newMessage);
      Console.WriteLine(newRover.ToString());

   **Output**

   ::

      Position: 98382 - Mode: NORMAL - GeneratorWatts: 110
      Position: 5000 - Mode: NORMAL - GeneratorWatts: 110


``Rover`` Tests
^^^^^^^^^^^^^^^

Open ``RoverTests.cs`` and write the following tests. Write the code to
make them pass in ``Rover.cs``. Remember to use the given phrase as the test
method name.

Test 8 
~~~~~~

"ConstructorSetsDefaultPosition".
Refer to the :ref:`Rover Class <rover-class>` description above for the
default value.

Test 9 
~~~~~~

"ConstructorSetsDefaultMode".

Test 10
~~~~~~~

"ConstructorSetsDefaultGeneratorWatts".


Test 11
~~~~~~~

"RespondsCorrectlyToModeChangeCommand". 

a. The test should check that when a rover object receives a message that contains a "MODE_CHANGE" 
   command, that rover's ``Mode`` field is updated.
b. The rover has two modes that can be passed as values to a mode change command,
   "LOW_POWER" and "NORMAL".

Test 12
~~~~~~~

"DoesNotMoveInLowPower". 

a. The test confirms that the rover position does not change when sent a "MOVE" command in "LOW_POWER" mode.
b. Use the :ref:`Rover Modes table <rover-modes-table>` for guidance on how
   to handle move commands in different modes.

Test 13
~~~~~~~

"PositionChangesFromMoveCommand".

a. A ``MOVE`` command will update the rover's position with the position value in 
   the command.


.. _command-types-table:

Rover Command Types
--------------------
.. list-table::
   :widths: auto
   :header-rows: 1

   * - Command
     - Value sent with command
     - Updates to ``Rover`` object
   * - MOVE
     - Number representing the position the rover should move to.
     - ``Position``
   * - MODE_CHANGE
     - String representing rover mode (see modes)
     - ``Mode``

.. note::

   The rover does not move while in "LOW_POWER" mode.

.. _rover-modes-table:

Rover Modes
-----------
.. list-table::
   :widths: auto
   :header-rows: 1

   * - Mode
     - Restrictions
   * - LOW_POWER
     - Can't be moved in this state.
   * - NORMAL
     - None


Bonus Mission
--------------

Add the following test that checks for unknown commands in
``RoverTests.cs``.


Test 14
^^^^^^^
"RoverReturnsAMessageForAnUnknownCommand".

Submitting Your Work
--------------------

In Canvas, open the Mars Rover assignment and click the "Submit" button.
An input box will appear.

Copy the URL for your repl.it project and paste it into the box, then click
"Submit" again.
