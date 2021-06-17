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
   A type of object containing a ``commandType`` property. ``commandType`` is one
   of the given strings in the table below. Some ``commandTypes`` are coupled with
   a ``value`` property, but not all. Every ``Command`` object is a single instruction 
   to be delivered to the rover.
#. ``Message``:
   A ``Message`` object has a ``name`` and contains several ``Command`` objects. 
   ``Message`` is responsible for bundling the commands from mission control and 
   delivering them to the rover.
#. ``Rover``:
   An object representing the mars rover. This class contains information on the rover's
   ``position``, operating ``mode``, and ``generatorWatts``. It also contains a function,
   ``receiveMessage`` that handles the various types of commands it receives and updates 
   the rover's properties.

In true TDD form, you will be asked to first write the appropriate units tests for 
these features, then write the code in the given class to pass those tests. 


Getting Started
---------------

#. Fork the `Mars rover starter repl.it <https://repl.it/@launchcode/mars-rover-starter>`__.
#. Write a unit test for each test item listed.
   shown below.

   .. note::
   
      One complete test has been created for you as an example.

#. Use :ref:`test-driven development (TDD) <tdd>` to create each of the
   classes described below.

#. Each class should be defined in its own file, which will be exported and
   imported as a module.


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
test descriptions* when creating your ``it`` statements. You must create 13
tests (14, if you do the bonus) for this assignment.

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
examine the file ``command.js``. 

#. This class builds an object with two properties.
   ``constructor(commandType, value)``

   a. ``commandType`` is a string that represents the type of command. We will go over
      the details of the types when we get to the ``Rover`` class and tests. At this 
      time, note that a command type will be one of the following: ``'MODE_CHANGE'``, 
      ``'MOVE'``, or ``'STATUS_CHECK'``.
      
      i. To peek ahead at the full functionality of these types, refer to 
         :ref:`Command Types table <command-types-table>`. 

   b. ``value`` is a value related to the type of command.

.. admonition:: Example

   .. sourcecode:: js

      let modeCommand = new Command('MODE_CHANGE', 'LOW_POWER');
      let moveCommand = new Command('MOVE', 12000);

   ``'MODE_CHANGE'`` and ``'MOVE'`` are passed in as the ``commandType``

   ``'LOW_POWER'`` and 12000 are passed in as the ``value``. Different command 
   types require different kinds of values. ``'STATUS_CHECK'`` takes no value.
   
   Don't worry about the mode options for now. To peek ahead, see 
   :ref:`Rover Modes table <rover-modes-table>`.

Now that we've gone over the class, let's check out the tests.

.. _command-tests:

``Command`` Tests
^^^^^^^^^^^^^^^^^

To begin, open and examine ``spec/command.spec.js``. One test has been created for 
you. When a user creates a new ``Command`` object from the class, we want to make 
sure they pass a command type as the first argument.

Test 1 
~~~~~~
   
Note that the test description reads, "throws error if a command type is NOT
passed into the constructor as the first parameter".

a. So far, you have only used ``assert`` methods to check for equality.
   Using ``assert.throws`` to verify if a specific error is thrown is a new
   concept. To learn how to use this new ability of ``assert``, look at the
   constructor in ``command.js`` and look at the test description in
   ``command.spec.js``. You can also look at the
   `official Node.js assert.throws documentation <https://nodejs.org/docs/latest-v10.x/api/assert.html#assert_assert_throws_fn_error_message>`__.
b. Click "Run" to verify that the test passes. Next, comment out lines 4-6 in
   ``command.js``. Click "Run" again to verify that the test fails (the
   expected error is not thrown when the ``Command`` class is called).
c. Restore lines 4-6 to ``throw Error("Command type required.");``.
d. Change line 12 in ``command.spec.js`` to ``message: 'Oops'``. Click "Run"
   again to verify that the test fails (the error message did not match
   ``"Command type required."``).
e. Restore line 12 to ``message: "Command type required."``.

Test 2
~~~~~~

Create a second ``Command`` test using, "constructor sets command type" as the
description. This test checks that the ``constructor`` in the ``Command``
class correctly sets the ``commandType`` property in the new object.

a. Without editing, ``command.js`` contains the correct code. Click "Run" to verify that the first
   and second tests both pass.
b. You do not need to use ``assert.throws()`` in this test.
c. You may not need to know the specific types of commands to write this test.

Test 3 
~~~~~~

Code a third test using, "constructor sets a value passed in as the 2nd
argument" as the description. This test checks that the ``constructor``
correctly sets the ``value`` property in the new object.

a. You may not need to know a proper ``value`` in order to write this test.
   
Click "Run" to verify that all 3 command tests pass.

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
   ``constructor(name, commands)``

   a. ``name`` is a string that is the name of the message.
   b. ``commands`` is an array of ``Command`` objects.

.. admonition:: Example

   .. sourcecode:: js

      let commands = [new Command('MODE_CHANGE', 'LOW_POWER'), new Command('STATUS_CHECK')];
      let message = new Message('Test message with two commands', commands);

``Message`` Tests
^^^^^^^^^^^^^^^^^

At the same level as ``command.spec.js``, create a file ``message.spec.js`` and 
write the unit tests for the ``Message`` class as described below. Remember to use 
the given phrase as the test description.

Test 4
~~~~~~

For this test description, use the text, "throws error if a name is NOT
passed into the constructor as the first parameter". Review the first test
in ``command.spec.js`` for an example of how to write this test.

a. When you click "Run", the test will likely fail, either because you have no 
   ``Message`` class yet or have not written the class to include this feature.

b. If you haven't done so yet, create a ``message.js`` file and add ``exports`` 
   and ``require`` statements as needed for your modules.

   .. admonition:: Tip

      For help using ``require`` to import a ``class``, notice in ``command.js``
      that the ``Command`` class is exported using:
      
      .. sourcecode:: js
      
         module.exports = Command;

      In ``spec/command.spec.js`` the ``Command`` class is imported with this
      statement:
      
      .. sourcecode:: js 
      
         const Command = require('../command.js');

c. Look at the code in ``command.js``. Use that to help you write the
   ``Message`` class in ``message.js`` so that your test passes. Refer to
   the :ref:`Message Class <message-class>` description above for more
   details.

Test 5
~~~~~~

Use "constructor sets name" as the description. The test confirms
that the ``constructor`` in the ``Message`` class correctly sets the
``name`` property in a new message object.

Test 6
~~~~~~

Use "contains a commands array passed into the constructor as 2nd argument".
This test confirms that the ``commands`` property of a new message object
contains the data passed in from the ``Message(name, commands)`` call.

a. Hint: Inside this test, you will have to create a ``commands`` array, fill
   it with some ``Command`` objects, and pass it into the ``Message``
   constructor.

.. admonition:: Warning

   You are moving onto the red planet now. Be prepared for fewer instructions.


C. ``Rover``
------------

``Rover`` receives a message object, updates its properties from the message, and 
returns the results.

.. _rover-class:

Rover Class
^^^^^^^^^^^

This class builds a rover object with a few properties, and it also contains
a function outside of ``constructor`` to handle updates to its properties.

#. ``constructor(position)``

   a. ``position`` is a number representing the rover's position.
   b. Sets ``this.position`` to ``position``
   c. Sets ``this.mode`` to ``'NORMAL'``
   d. Sets default value for ``generatorWatts`` to 110

#. ``receiveMessage(message)``

   a. ``message`` is a ``Message`` object
   b. Returns an object containing at least two properties:
         
      i. ``message``: the name of the original ``Message`` object
      ii. ``results``: an array of *results*. Each element in the array is an 
          object that corresponds to one ``Command`` in ``message.commands``.
         
   c. Updates certain properties of the rover object

      i. Details about how to respond to different commands are in the
         :ref:`Command Types table <command-types-table>`.

.. admonition:: Example

   .. sourcecode:: js

      let commands = [new Command('MODE_CHANGE', 'LOW_POWER'), new Command('STATUS_CHECK')];
      let message = new Message('Test message with two commands', commands);
      let rover = new Rover(98382);    // Passes 98382 as the rover's position.
      let response = rover.receiveMessage(message);

      console.log(response);

   **Output**

   ::

      {
         message: 'Test message with two commands',
         results: [
            {
               completed: true
            },
            {
               completed: true, 
               roverStatus: { mode: 'LOW_POWER', generatorWatts: 110, position: 98382 }
            }
         ]
      }


``Rover`` Tests
^^^^^^^^^^^^^^^

Create ``spec/rover.spec.js`` and write the following tests. Write the code to
make them pass in ``rover.js``. Remember to use the given phrase as the test
description.

Test 7 
~~~~~~

"constructor sets position and default values for mode and generatorWatts".
Refer to the :ref:`Rover Class <rover-class>` description above for these
default values.

Test 8
~~~~~~

"response returned by receiveMessage contains name of message"

Test 9
~~~~~~

"response returned by receiveMessage includes two results if two commands
are sent in the message"

Test 10
~~~~~~~

"responds correctly to status check command"

a. For the ``STATUS_CHECK`` command, ``receiveMessage(message).results`` 
   includes a ``roverStatus`` object describing the current state of the 
   rover object --- ``mode``, ``generatorWatts``, and ``position``. The test 
   should check each of these for accuracy.
b. See the :ref:`Rover Command Types <command-types-table>` table for more
   details.

Test 11
~~~~~~~

"responds correctly to mode change command". 

a. The test should check the ``completed`` property and rover mode for accuracy.
b. The rover has two modes that can be passed a values to a mode change command,
   'LOW_POWER' and 'NORMAL'.

Test 12
~~~~~~~

"responds with false completed value when attempting to move in LOW_POWER
mode". 

a. The test should check the ``completed`` property for accuracy and confirm 
   that the rover position did not change.
b. Use the :ref:`Rover Modes table <rover-modes-table>` for guidance on how
   to handle move commands in different modes.

Test 13
~~~~~~~

"responds with position for move command".

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
     - Result returned
   * - MOVE
     - Number representing the position the rover should move to.
     - ``position``
     - ``{completed: true}``
   * - STATUS_CHECK
     - No values sent with this command.
     - No updates
     - ``{completed: true, roverStatus: {mode: 'NORMAL', generatorWatts: 110, position: 87382098}}`` Values for ``mode``, ``generatorWatts``, ``position`` will depend on current state of rover.
   * - MODE_CHANGE
     - String representing rover mode (see modes)
     - ``mode``
     - ``{completed: true}``

.. note::

   The response value for ``completed`` will be ``false`` if the command could
   NOT be completed.

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
``spec/rover.spec.js``.


Test 14
^^^^^^^
"completed false and a message for an unknown command".

Submitting Your Work
--------------------

In Canvas, open the Mars Rover assignment and click the "Submit" button.
An input box will appear.

Copy the URL for your repl.it project and paste it into the box, then click
"Submit" again.
