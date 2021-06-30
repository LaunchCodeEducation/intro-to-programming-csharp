Select Input
============

Select inputs create a clickable menu that displays options and allows the user
to select one. The available options are defined by ``<option>`` tags inside of
the ``<select></select>`` tag.

``<option>`` tags have a ``value`` attribute which defines the value submitted
if that option is selected. The text inside the
``<option>Option text</option>`` is what is displayed in the select menu.

``<option>`` tag ``values`` can also include a **default** option.  
This is what will be displayed first upon loading regardless of location in your html.
To create a default option, you add ``selected`` after the ``value``.  
See the table below for proper placement of this code. 

.. role:: raw-html(raw)
   :format: html

.. list-table::
   :header-rows: 1

   * - Type
     - Syntax
     - Description
     - Demo
   * - select
     - ``<select name="weather"><option value="1">clear</option><option value="2">cloudy</option></select>``
     - A menu that allows selection of one option. Requires options to be in ``<option>`` tags.
     - :raw-html:`<select name="weather"><option value="1">clear</option><option value="2">cloudy</option></select>`
   * - default select option
     - ``<select name="game"><option value="1">Checkers</option><option value="2" selected>Chess</option></select>``
     - A menu that allows selection of one option, but the ``selected`` default option is the one the list will display once loaded. 
     - :raw-html:`<select name="game"><option value="1">Checkers</option><option value="2" selected>Chess</option></select>`

Example
-------

.. admonition:: Example

   .. sourcecode:: html

      <form action="https://handlers.education.launchcode.org/request-parrot" method="post">
         <label>Operation Code:
         <!-- includes empty value "Select One" option -->
         <select name="operation">
            <option value="">* Select One *</option>
            <option value="1">Simulation</option>
            <option value="2">Rocket Test</option>
            <option value="3">Crew Related</option>
         </select>
         </label>

         <!-- includes selected "Default" option -->
         <label>Facility:
         <select name="facility">
            <option value="kennedy">Kennedy Space Center, FL</option>
            <option value="white-sands">White Sands Test Facility, NM</option>
            <option value="johnson" selected>Johnson Space Center, TX</option>
         </select>
         </label>
         <button>Send Report</button>
      </form>

   **Default Form Values**

   .. figure:: figures/select-inputs-example1.png
      :alt: Web form showing select inputs for Operation Code and Facility.

   **Select "Rocket Test" and "White Sands Test Facility, NM"**

   .. figure:: figures/select-inputs-example2.png
      :alt: Web form with select inputs with "Rocket Test" and "White Sands Test Facility, NM" selected.

   **Submitted Values**

   ::

      operation=2
      facility=white-sands 

   `Run it <https://replit.com/@launchcode/select-inputs-example-2>`__


Check Your Understanding
------------------------

.. admonition:: Question

   For a select input, what determines the value that is submitted during form submission?
