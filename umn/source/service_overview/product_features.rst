:original_name: functiongraph_01_0200_0.html

.. _functiongraph_01_0200_0:

Product Features
================

Function Management
-------------------

FunctionGraph provides console-based function management.

-  The Node.js, Java, Python, Go, and custom runtimes are supported. :ref:`Table 1 <functiongraph_01_0200_0__en-us_topic_0000001257380265_table10794101711416>` provides the details.

   .. note::

      You are advised to use the latest runtime version.

   .. _functiongraph_01_0200_0__en-us_topic_0000001257380265_table10794101711416:

   .. table:: **Table 1** Runtimes

      ======= ======================================
      Runtime Supported Version
      ======= ======================================
      Node.js 6.10, 8.10, 10.16, 12.13, 14.18, 16.17
      Python  2.7, 3.6, 3.9
      Java    8.0 and 11
      Go      1.x
      C#      .NET Core 2.1 and .NET Core 3.1
      PHP     7.3
      Custom  ``-``
      ======= ======================================

-  Multiple code entry modes

   FunctionGraph allows you to edit code inline, upload a ZIP file from Object Storage Service (OBS), or directly upload a ZIP or JAR file. :ref:`Table 2 <functiongraph_01_0200_0__en-us_topic_0000001257380265_table35034283164337>` lists the code entry modes supported for each runtime.

   .. _functiongraph_01_0200_0__en-us_topic_0000001257380265_table35034283164337:

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

Trigger
-------

:ref:`Table 3 <functiongraph_01_0200_0__en-us_topic_0000001257380265_table1316993416219>` lists the invocation modes for different trigger types.

.. _functiongraph_01_0200_0__en-us_topic_0000001257380265_table1316993416219:

.. table:: **Table 3** Function invocation modes

   ======================================= ========================
   Trigger                                 Function Invocation Mode
   ======================================= ========================
   SMN trigger                             Asynchronous invocation
   APIG trigger                            Synchronous invocation
   OBS trigger                             Asynchronous invocation
   Data Ingestion Service (DIS) trigger    Asynchronous invocation
   Timer trigger                           Asynchronous invocation
   Log Tank Service (LTS) trigger          Asynchronous invocation
   Cloud Trace Service (CTS) trigger       Asynchronous invocation
   Document Database Service (DDS) trigger Asynchronous invocation
   Kafka trigger                           Asynchronous invocation
   ======================================= ========================

Logs and Metrics
----------------

FunctionGraph graphically displays function monitoring metrics and collects function running logs, enabling you to view function statuses, and locate problems by querying logs.

To query logs, see :ref:`Managing Function Logs <functiongraph_01_1834>`.

For details about monitoring metric, see :ref:`Function Monitoring <functiongraph_01_0212>`.

For details about tenant-level function monitoring metrics, see :ref:`Introduction to Dashboard <functiongraph_01_0110__en-us_topic_0000001251907944_section123696302544>`.

Function Initialization
-----------------------

The initializer interface is introduced to:

-  Isolate function initialization and request processing to enable clearer program logic and better structured and higher-performance code.
-  Ensure smooth function upgrade to prevent performance loss during the application layer's cold start initialization. Enable new function instances to automatically execute initialization logic before processing requests.
-  Identify the overhead of application layer initialization, and accurately determine the time for resource scaling and the quantity of required resources. This feature makes request latency more stable when the application load increases and more function instances are required.

HTTP Functions
--------------

You can set **Function Type** to **HTTP Function** on the function creation page. HTTP functions are designed to optimize web services. You can send HTTP requests to URLs to trigger function execution. HTTP functions support APIG and API Connect (APIC) triggers only.

Custom Images
-------------

You can directly package and upload container images. The images are loaded and started by the platform and can be called in a similar way as HTTP functions. Unlike the previous code upload mode, you can use a custom code package, which is flexible and reduces migration costs.
