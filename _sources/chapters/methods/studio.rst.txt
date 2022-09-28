Studio: Methods
====================

Getting Started
-----------------

**Getting Started:**  Click `here <https://replit.com/@launchcode/StringAndArrayStudio01-CS>`_ for the starter code.  As you work through the studio, you'll be updating this code.


Creating A Better ``Reverse`` Method
-------------------------------------------

The ``Reverse`` method flips the order of the elements within an array.
However, ``Reverse`` does not affect the digits or characters within those
elements.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      string[] arr = new string[] {"hello", "world", "123", "orange"};

      Array.Reverse(arr);

      foreach(string a in arr)
      {
         Console.WriteLine(a);
      }

   **Console Output**

   ::
      
      orange
      123
      world
      hello
      

What if we wanted the reversed array to be

:: 
 
   egnaro
   321
   dlrow
   olleh

Let's have some fun by creating a process that reverses BOTH the order of the
entries in an array AND the order of characters within the individual elements.

Remember that a method should perform only *one* task. 


Warm-Up: Reverse a Number Array
--------------------------------

1. Define a method called ``ReverseNumbers`` that will sort the numbers within an array in descending order.
2. Within the method, ``Sort`` the array.
3. Use ``Reverse`` method to put the items into descending order.  
4. Using a loop of your choice, print your final array to the console.
5. Be sure to test your method, call it at least twice with arrays of different sizes and numbers.  


Reverse a String
------------------

1. Define a method called ``ReverseLetters`` that will reverse each character inside a string and print the results to the console.  This will be similar to the ``ReverseNumbers`` method.
2.  Look through the `String Methods <string-methods>`_  and `Array Methods <array-methods>`_ to figure out the best approach for this.  Consider the following: How can you access or alter characters within strings? What data types are going into your method, being used in your method, and printed by your method?
3. Be sure to test your method by invoking it a few times.  Some test examples you could use: ``C Sharp``, ``Hello``, ``Coding is fun!`` they should return as ``prahS C``, ``olleH``, and ``!nuf si gniodC`` .
4.  Now make this method take input from a user.  Print a message that contains the original string and the newly reversed string.
   

Palindrome Checker
--------------------

Now that you can completely reverse a string, let's use this to check to see if a word is a palindrome.
A palindrome is a word that is spelled the same forwards and backwards.  Some examples are ``sagas``, ``kayak``, and ``racecar``.

.. admonition:: Note

   There are other factors that are sometimes included in the definition of a palindrome. For example, an alternative definition is that a palindrome is a sentence or phrase that contains letters in the same order, whether considered from beginning-to-end, or end-to beginning, ignoring punctuation, case, and spaces.

One way to state a palindrome condition is to say that a palindrome is a string that is equal to its reverse.  
When we think about it that way, what we need to do is create a method that will take a string, reverse it, compare it to the original and verify if they are equal.


You have alredy built a function that reverses a string.  It shouldn't be too hard to extend that method to be able to detect palindromes. 
  
1.  Define your method ``IsPalindrome``, to check if a string is equal to its reverse.  Think what data type the overall outcome will require.
2.  Make sure your method provides a message that informs whether or not the input is a palidrome or not.  Some single word examples you can test:  ``racecar``, ``civic``, ``sagas``.  
3.  Make this method accept user input. 
4.  Will upper or lowercase be an issue?

**Bonus Mission:** Modify your method to accept mulitple word palindromes.  For example, ``Drab as a fool, aloof as a bard`` or ``Never odd or even``.  

