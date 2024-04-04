:original_name: functiongraph_02_1005.html

.. _functiongraph_02_1005:

Concepts
========

Function
--------

Functions are code defined to handle events.

Event Source
------------

An event source is a public cloud service or custom application that publishes events.

Synchronous Invocation
----------------------

Clients wait for explicit responses to their requests from a function. Responses are returned only after the function is invoked.

Asynchronous Invocation
-----------------------

Clients do not care about the function invocation results of their requests. After receiving a request, FunctionGraph puts it in a queue, returns a response, and processes other requests when there are idle resources.

Trigger
-------

A trigger is an event that triggers function execution.

Single-Instance Multi-Concurrency
---------------------------------

The number of requests that can be concurrently processed by an instance.

Custom Images
-------------

You can directly package and upload container images. The platform then loads and starts these images to create functions.

Custom Function Execution
-------------------------

You can customize scripts and files to execute functions.

Function Logs
-------------

Logs generated during function invocation.

Function Monitoring
-------------------

Monitoring information generated during function execution.

Function Version
----------------

FunctionGraph allows you to publish one or more versions throughout the development, testing, and production processes to manage your function code. The code and environment variables of each version are saved as a snapshot. After the function code is published, modify settings when necessary.

Function Alias
--------------

You can create an alias for a specific function version. To roll back to a previous version, use the corresponding alias to represent the version instead of modifying the function code.

Each function alias can be bound to a major version and an additional version for traffic shifting.

Dependency Package
------------------

FunctionGraph enables you to manage dependencies in a unified manner. You can upload dependencies from a local path, or through OBS if they are too large, and specify names for them.

Bootstrap File
--------------

The **bootstrap** file is the startup file of an HTTP function. The HTTP function can only read **bootstrap** as the startup file name. If the file name is not **bootstrap**, the service cannot be started.
