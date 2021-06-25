HTTP in the Browser
===================

While we have covered all of the HTTP concepts you need to know at this point, it's worth spending some time explaining how web browsers submit requests and receive responses.

Viewing Requests and Response Using Developer Tools
---------------------------------------------------


Before You Get Started
^^^^^^^^^^^^^^^^^^^^^^

This section uses Firefox's developer tools to explore HTTP in the browser. 
If you need a reference for using Firefox, visit 
`MDN <https://developer.mozilla.org/en-US/docs/Tools>`_.

The overall concepts of the tools will be the same for any browser.  
Just be aware that if you are not using Firefox, the display will vary, but the data will be there.

If using chrome, this guide will help walk you through the developer tools: `Chrome DevTools <https://developer.chrome.com/docs/devtools/>`_

If using Safari, this guide will also provide you the same guidance: `How to inspect request and response headers on Safari <https://jun711.github.io/web/how-to-inspect-network-request-and-response-headers-on-safari/>`_

Working In the Browser
^^^^^^^^^^^^^^^^^^^^^^

Open a web browser and visit some web page, say, `our example from the HTML Me Something assignment <https://education.launchcode.org/html-me-something/submissions/chrisbay/index.html>`_. After the page loads, open your browser's developer tools and select the *Network* tab.

You'll see something like this:

.. figure:: figures/empty-network-tab.png
   :alt: Firefox's developer tools, with an empty Network pane.

The *Network* pane displays all HTTP requests and responses involved in loading a page. However, it only tracks and displays such data if it is open during the request. To see some data in this tab, refresh the page.

Now you'll see something like this:

.. figure:: figures/network-tab.png
   :alt: Firefox's developer tools, with several requests in the Network pane.

Each entry within the pane represents a single HTTP request. A summary of the request is shown in a table format, including the resource requested, server name, response code, and more. Clicking on one of the entries shows more detailed information about the request.

.. figure:: figures/network-tab-details.png
   :alt: The details of an HTTP request, viewed in the Network pane.

On the right, we see additional request and response details, including response headers and (scrolling down) request headers. We can even view the response body by clicking on the *Response* label.

.. admonition:: Try It!

   Navigate to a different page with the *Network* pane open. Find the response code and ``Content-Type`` header for the first request shown in the pane.

Browser Flow
------------

As you can see from using the *Network* pane, loading a single web page usually involves *several* HTTP requests. Each resource *within* the page is loaded in a separate request. 

Let's examine the flow of loading a page. We'll consider the case of an HTML page with CSS and images, loaded via a ``GET`` request.

#. Browser requests a page from the server.
#. Browser receives the HTML page and parses it.
#. For *each* image, external CSS file, and any other external file type, the browser issues a *new* HTTP request for the given file.
#. As additional responses are received, the browser processes the data or media and updates the page. 

This process explains why you will sometimes load a web page, only to see an image on that page load a few seconds later. In such situations, the HTTP request fetching the image takes substantially more time, making it noticeable.

 

Check Your Understanding
------------------------

.. admonition:: Question

   For the first screenshot on this page, answer these questions:

   #. What is its file name?
   #. How large is it?   
