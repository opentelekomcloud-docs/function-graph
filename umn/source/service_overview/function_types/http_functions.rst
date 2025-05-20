:original_name: en-us_topic_0000001257403573.html

.. _en-us_topic_0000001257403573:

HTTP Functions
==============

Overview
--------

FunctionGraph supports event functions and HTTP functions. HTTP functions are designed to optimize web services. You can send HTTP requests to URLs to trigger function execution. HTTP functions support APIG triggers only.

.. note::

   #. HTTP functions support the HTTP/1.1 protocol.
   #. On the function creation page, **HTTP Function** is newly added.
   #. The HTTP function must be set to bootstrap. You can directly write the startup command and **allow access over port 8000**.

Advantages
----------

-  Support for multiple frameworks

   You can use common web frameworks, such as Node.js Express and Koa, to write web functions, and migrate your local web framework services to the cloud with least modifications.

-  Fewer request processing steps

   Functions can directly receive and process HTTP requests, eliminating the need for API Gateway to convert the JSON format. This accelerates request processing and improves web service performance.

-  Premium writing experience

   Writing HTTP functions is similar to writing native web services. You can also use native Node.js APIs to enjoy local development-like experience.

Restrictions
------------

-  HTTP functions support APIG (dedicated) triggers only.
-  Multiple API triggers can be bound to the same function, but all the APIs must belong to the same APIG service.
-  For HTTP functions, the size of the HTTP response body cannot exceed 6 MB.
-  HTTP functions cannot be executed for a long time, invoked asynchronously, or retried.
