Studio: HTTP and Forms
======================

Introduction
------------

This chapter taught you that forms submit data in HTTP requests. This studio
uses form and HTTP concepts to build a *search engine selector*, that is, a
search form that allows a user to choose which search engine they would like to
use. It will look like this:

.. figure:: figures/search-engine-selector.png
   :alt: A form with a text input and radio buttons corresponding to various search engines.

   The search engine selector that we will build.

Most search engines work the same way. They have a single text input, and they
submit data using a ``GET`` request. Additionally, many of the most popular
search engines also use the same name for the search parameter, ``q``.

.. admonition:: Try It!

   Use 2-3 different search engines to search for the same term. On the results page, look at the URL. Did the search happen via ``GET`` or ``POST``? If a ``GET`` request was made, what is the name of the parameter containing your search term?

   *Note:* You may have to copy/paste the URL into a text editor to find the search parameter. Some engines add other parameters to the URL, causing it to extend past the end of the browser's address bar.

.. note:: We remarked previously that most forms use ``POST`` because they cause data to be changed on the server. A web search only *retrieves* data. It does not change data. Therefore it's safe to use a ``GET`` request for searches.

The fact that most search engines use the name ``q`` for their search boxes
will allow us to easily create a form that is capable of sending a search
request to several search engines.

The form will send a request with query parameter ``q`` to the selected engine.
Since this request looks essentially the same as requests coming from the
search engine's own form (for example, at `google.com <https://google.com>`__)
it will give us back the results the same as if we had searched via those
sites.

Getting Started
---------------

Fork and clone the starter code from this `repo <https://github.com/LaunchCodeEducation/csharp-intro-to-program-lsn15-http-forms-studio>`_.


.. admonition:: Warning!
   
   **Before you get started, let's look at the starter code.**  There is a new HTML tag, ``<script>`` and ``</script>``.
   The HTML between these tags is JavaScript, designed to respond once the form is completed.  
   You will not be working with this code.  However, please make sure that you are using the naming options provided for you in the exercise instructions.


Create Form Inputs
------------------

Let's build out the form in ``index.html``. We will need some data for the
search engines we want to work with.

.. list-table:: Search Engine Options
   :header-rows: 1

   * - Label
     - Value
     - Search URL
   * - Google
     - ``google``
     - https://www.google.com/search
   * - DuckDuckGo
     - ``duckDuckGo``
     - https://duckduckgo.com/
   * - Bing
     - ``bing``
     - https://www.bing.com/search
   * - Ask
     - ``ask``
     - https://www.ask.com/web

#. Create a text input within the form and set its ``name`` attribute to the
   value ``"q"``.
#. Create a radio group with one radio button for each search engine. Recall
   that radio buttons with the same ``name`` are grouped, so use the same
   value for this attribute, ``"engine"``, on each radio button.
#. Create a ``label`` element for each radio button.
#. Finally, add a submit button to the form and set it's ``value`` to
   ``"Go!"``.

.. admonition:: Question

   How is the ``value`` attribute of a submit button used?

Congrats! You have just created a dynamic website. 

Bonus Mission
^^^^^^^^^^^^^^

Add some CSS rules to your page to make it look nice.

Uploading Your Work
--------------------

Push up your work to save your solution in your remote repository.




