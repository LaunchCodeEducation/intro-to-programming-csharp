=====================
Values and Variables
=====================

Programs may be thought of as being made up of two things:

1. Data
2. Operations that manipulate data

This chapter focuses primarily on the first of these two fundamental components, data.

.. index:: ! value

Data can be stored in a program in a variety of ways. The most basic unit of data is a value.

A **value** is a specific piece of data, such as a word or a number.  To store values we create variables.

.. _def-value:

.. _def-variable:

A **variable** is a way of referring to a value.  
It is a container that holds the value, which makes it easier to use in your programs.  
Imagine writing a program that uses the number miles to the moon for five different calculations.  
Instead of manually typing 238,855 over and over again, we can create a variable called ``milesToMoon`` 
to hold that number for us.  Then as we code we can call ``milesToMoon`` in the number’s place.  
This can help reduce typing errors and also give your code context.  Using a variable with a specific 
name helps someone reading your code to understand what ``milesToMoon`` is instead of looking at a random number. 

In the code block below, we created a variable called ``milesToMoon`` which holds the value of ``238855``.  In the ``Console.WriteLine`` we 
called that varialbe to print.  

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      int milesToMoon = 238855;
      Console.WriteLine(milesToMoon);

   **Console Output**

   ::

      238855

.. admonition:: Note
   
   Notice there are no commas in the number.  They are not needed in this context.  

If you notice that when the text, ``milesToMoon``, is called in the ``Console.WriteLine`` there are no quotation marks. 
It is a variable and not a string of text.  If you look at the output, you will see the numeric value we intialized in line 1.

So what happend?  In line 1, we created a statement that says ``milesToMoon`` is equal to 238855.  ``milesToMoon`` is the reference point 
for that specific value.  When the variable is sent to the ``Console.WriteLine``, the value is printed not the variable.  The varialbe is a 
placeholder for the value, and when called it will refer back to the specific value it was assigned.  This is a very important concept and we 
will explore it in more depth in a later section.


There is one piece of this code we have not talked about.  In line 1 you may have noticed **int**.  This is a data type and in this instance
declares that we are working with an **integer** or whole number.  Data types are very important in C#.  In fact they are vital to the creation 
of variables.  Before we explore variables more, we need to learn more about data types.    






   