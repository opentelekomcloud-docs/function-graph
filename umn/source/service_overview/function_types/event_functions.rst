:original_name: functiongraph_02_1001.html

.. _functiongraph_02_1001:

Event Functions
===============

Overview
--------

FunctionGraph supports event functions. An event can trigger function execution. Generally, it is in JSON format. You can create an event to trigger your function through the cloud service platform or CodeArts IDE Online. All types of triggers supported by FunctionGraph can trigger event functions.

.. note::

   #. On the function creation page, **Function Type** is set to **Event Function** by default.
   #. During testing, a function can be triggered by simply entering the specified event in JSON format.
   #. You can also use triggers to trigger event functions.

Advantages
----------

-  Easy single-node programming

   You can edit event functions on FunctionGraph or upload code packages there and deploy them with just a few clicks. There is no need for you to care about function concurrency or fault rectification.

-  High-performance, high-speed runtimes

   Event functions can be started, scaled, and called within milliseconds. Faults can be detected and rectified within seconds.

-  Complete tool chain

   FunctionGraph provides comprehensive logging, tracing, debugging, and monitoring, allowing developers to roll out functions in just three steps.

Restrictions
------------

Event functions face event source restrictions. You need to comply with the function development rules of the function platform.
