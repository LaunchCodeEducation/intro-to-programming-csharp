Running Tests Part 2: 
======================

Now that you have walked through a few ``[TestMethod]`` examples, 
we are going to cover a few testing methods you might find useful. 

.. index:: ! [TestInitialize]

``[TestInitialize]``
--------------------

While ``[TestClass]`` and ``[TestMethod]`` are required to run tests, 
there are many other attributes you may find useful as your test files grow in scope. 
One such item to know is **[TestInitialize]**. Methods with the attribute 
``[TestInitialize]`` will run *before* each test method is run in a class. 

In the case of ``CarTest``, it would be nice to not need to create a new ``Car`` 
instance for each test we write. In your ``TestInitialGasTank()`` method, 
remove the line initiating ``test_car``. 
Above your relevant test, add the following ``[TestInitialize]`` method:

.. sourcecode:: c#
   :lineno-start: 16

   Car test_car;

   [TestInitialize]
   public void CreateCarObject()
   {
      test_car = new Car("Toyota", "Prius", 10, 50);
   }

Now, run the test project and ensure your test still passes.

.. index:: ! [TestCleanup]

``[TestCleanup]``
-----------------

``[TestCleanup]``, conversely, defines a set of conditions to be met *after* each test in a 
suite is run. 

.. admonition:: Note

   We won't encounter a scenario where we ask you to use ``[TestCleanup]`` in this class. 
   As you explore writing your own unit tests, you may find yourself in a situation where 
   you need or want it. One use case for ``[TestCleanup]`` might be testing database transactions. 
   You don't want changes to a database to persist after test execution, so you can use 
   ``[TestCleanup]`` to rollback, or reverse, a test transaction.

You can find more information on this attribute and other items available in the 
Visual Studio testing namespace 
`here <https://docs.microsoft.com/en-us/dotnet/api/microsoft.visualstudio.testtools.unittesting?view=mstest-net-1.2.0>`__.


Common ``Assert`` Methods
-------------------------

In addition to the very commonly used ``Assert.AreEqual()`` method
you see above, here are a few other methods you should have in 
your unit testing playbook.

.. list-table:: MSTest Assert Methods
   :header-rows: 1

   + - Assertion
     - Description
   + - ``AreEqual(expected, actual, optional_delta)``
     - Asserts that two values, expected and actual, are equal to each other (optionally, within a given range of difference)
   + - ``IsFalse(condition)``
     - Asserts that a given condition is false
   + - ``IsTrue(condition)``
     - Asserts that a given condition is true
   + - ``IsNotNull(object)``
     - Asserts that a given object is not null

Checkout `the Assert class <https://docs.microsoft.com/en-us/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert?redirectedfrom=MSDN&view=mstest-net-1.2.0>`__
for a full listing of methods.

Check Your Understanding
-------------------------

.. admonition:: Question

   Write another version of ``TestInitialGasTank()`` using ``IsFalse()``, 
   comparing the value to ``0``.

   #. ``Assert.IsFalse(Car.GasTankLevel == 0);``
   #. ``Assert.IsFalse(test_car.GasTankLevel == 0);``
   #. ``Assert.False(test_car.GasTankLevel == 0);``
   #. ``Assert.IsFalse(test_car.GasTankLevel = 0);``

.. ans: b, Assert.IsFalse(test_car.GasTankLevel == 0);

.. admonition:: Question

   Write another version of ``TestInitialGasTank()`` using ``IsTrue()``.

   #. ``Assert.IsTrue(test_car.gasTankLevel == 10);``
   #. ``Assert.IsTrue(Car.GasTankLevel == 10);``
   #. ``Assert.IsTrue(test_car.GasTankLevel == 0);``
   #. ``Assert.IsTrue(test_car.GasTankLevel == 10);``

..  ans: d, Assert.IsTrue(test_car.GasTankLevel == 10);


