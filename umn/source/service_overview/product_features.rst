:original_name: functiongraph_01_0200_0.html

.. _functiongraph_01_0200_0:

Product Features
================

Function Management
-------------------

FunctionGraph provides console-based function management.

-  The Node.js, Java, Python, Go, C#, PHP, and custom runtimes are supported. :ref:`Table 1 <functiongraph_01_0200_0__table10794101711416>` provides the details.

   .. note::

      You are advised to use the latest runtime version.

   .. _functiongraph_01_0200_0__table10794101711416:

   .. table:: **Table 1** Runtimes

      ======= ====================================================
      Runtime Supported Version
      ======= ====================================================
      Node.js 6.10, 8.10, 10.16, 12.13, 14.18, 16.17, 18.15, 20.15
      Python  2.7, 3.6, 3.9, 3.10, 3.12
      Java    8, 11, 17, 21
      Go      1.x
      C#      .NET Core 2.1, .NET Core 3.1, .NET Core 6.0
      PHP     7.3, 8.3
      Custom  ``-``
      ======= ====================================================

-  Multiple code entry modes

   FunctionGraph allows you to edit code inline, upload a ZIP file from Object Storage Service (OBS), or directly upload a ZIP or JAR file. :ref:`Table 2 <functiongraph_01_0200_0__table35034283164337>` lists the code entry modes supported for each runtime.

   .. _functiongraph_01_0200_0__table35034283164337:

   .. table:: **Table 2** Code entry modes

      +---------+---------------------+----------------------+----------------------+-------------------------------+
      | Runtime | Editing Code Inline | Uploading a ZIP File | Uploading a JAR File | Uploading a ZIP File from OBS |
      +=========+=====================+======================+======================+===============================+
      | Node.js | Supported           | Supported            | Not supported        | Supported                     |
      +---------+---------------------+----------------------+----------------------+-------------------------------+
      | Python  | Supported           | Supported            | Not supported        | Supported                     |
      +---------+---------------------+----------------------+----------------------+-------------------------------+
      | Java    | Not supported       | Supported            | Supported            | Supported                     |
      +---------+---------------------+----------------------+----------------------+-------------------------------+
      | Go      | Not supported       | Supported            | Not supported        | Supported                     |
      +---------+---------------------+----------------------+----------------------+-------------------------------+
      | C#      | Not supported       | Supported            | Not supported        | Supported                     |
      +---------+---------------------+----------------------+----------------------+-------------------------------+
      | PHP     | Supported           | Supported            | Not supported        | Supported                     |
      +---------+---------------------+----------------------+----------------------+-------------------------------+
      | Custom  | Supported           | Supported            | Not supported        | Supported                     |
      +---------+---------------------+----------------------+----------------------+-------------------------------+

.. _functiongraph_01_0200_0__section327204091911:

Function Triggers
-----------------

:ref:`Table 3 <functiongraph_01_0200_0__table134424315184>` lists the invocation modes for different trigger types.

.. _functiongraph_01_0200_0__table134424315184:

.. table:: **Table 3** Function trigger invocation

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Trigger                           | Invocation Mode                                                                                                                                                   |
   +===================================+===================================================================================================================================================================+
   | API Gateway (Dedicated)           | Synchronous invocation is used by default. You can change it to asynchronous invocation. For details, see :ref:`Asynchronous Invocation <functiongraph_01_1062>`. |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Timer                             | Synchronous (default)                                                                                                                                             |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cloud Trace Service (CTS)         | Asynchronous (default and cannot be changed)                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Document Database Service (DDS)   | Asynchronous (default and cannot be changed)                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DMS (for Kafka)                   | Asynchronous (default and cannot be changed)                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Kafka (Open-Source)               | Asynchronous (default and cannot be changed)                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Log Tank Service (LTS)            | Asynchronous (default and cannot be changed)                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Simple Message Notification (SMN) | Asynchronous (default and cannot be changed)                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _functiongraph_01_0200_0__section382816599214:

Logs and Metrics
----------------

FunctionGraph graphically displays function monitoring metrics and collects function running logs, enabling you to view function statuses, and locate problems by querying logs.

For details about how to query logs, see :ref:`Managing Function Logs <functiongraph_01_1834>`.

For details about a single monitoring metric, see section "Function Monitoring" in the *FunctionGraph User Guide*.

For details about tenant-level monitoring information, see :ref:`Introduction to Dashboard <functiongraph_01_0110__en-us_topic_0000001251907944_section123696302544>`.

Function Initialization
-----------------------

The initializer interface is introduced to:

-  Isolate function initialization and request processing to enable clearer program logic and better structured and higher-performance code.
-  Ensure smooth function upgrade to prevent performance loss during the application layer's cold start initialization. Enable new function instances to automatically execute initialization logic before processing requests.
-  Identify the overhead of application layer initialization, and accurately determine the time for resource scaling and the quantity of required resources. This feature makes request latency more stable when the application load increases and more function instances are required.

HTTP Functions
--------------

You can set **Function Type** to **HTTP Function** on the function creation page. HTTP functions are designed to optimize web services. You can send HTTP requests to URLs to trigger function execution. HTTP functions support APIG triggers only.

Custom Images
-------------

You can directly package and upload container images. The images are loaded and started by the platform and can be called in a similar way as HTTP functions. Unlike the previous code upload mode, you can use a custom code package, which is flexible and reduces migration costs.
