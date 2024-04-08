:original_name: functiongraph_01_0303.html

.. _functiongraph_01_0303:

Configuring Single-Instance Multi-Concurrency
=============================================

Overview
--------

By default, each function instance processes only one request at a specific time. For example, to process three concurrent requests, FunctionGraph triggers three function instances. To address this issue, FunctionGraph has launched the single-instance multi-concurrency feature, allowing multiple requests to be processed concurrently on one instance.

Scenario
--------

This feature is suitable for functions which spend a long time to initialize or wait for a response from downstream services. The feature has the following advantages:

-  Fewer cold starts and lower latency: Usually, FunctionGraph starts three instances to process three requests, involving three cold starts. If you configure the concurrency of three requests per instance, only one instance is required, involving only one cold start.
-  Shorter processing duration and lower cost: Normally, the total duration of multiple requests is the sum of each request's processing time.

Comparison
----------

If a function takes 5s to execute each time and you set the number of requests that can be concurrently processed by an instance to 1, three requests need to be processed in three instances, respectively. Therefore, the total execution duration is 15s.

When you set **Max. Requests per Instance** to **5**, if three requests are sent, they will be concurrently processed by one instance. The total execution time is 5s.

.. note::

   If the maximum number of requests per instance is greater than 1, new instances will be automatically added when this number is reached. The maximum number of instances will not exceed **Max. Instances per Function** you set.

.. table:: **Table 1** Comparison

   +-----------------------+---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Comparison Item       | Single-Instance Single-Concurrency                | Single-Instance Multi-Concurrency                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   +=======================+===================================================+=================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | Log printing          | ``-``                                             | To print logs, Node.js Runtime uses the **console.info()** function, Python Runtime uses the **print()** function, and Java Runtime uses the **System.out.println()** function. In this mode, current request IDs are included in the log content. However, when multiple requests are concurrently processed by an instance, the request IDs are incorrect if you continue to use the preceding functions to print logs. In this case, use **context.getLogger()** to obtain a log output object, for example, Python Runtime. |
   |                       |                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   |                       |                                                   | log = context.getLogger()                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                       |                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   |                       |                                                   | log.info("test")                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   +-----------------------+---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Shared variables      | Not involved.                                     | Modifying shared variables will cause errors. Mutual exclusion protection is required when you modify non-thread-safe variables during function writing.                                                                                                                                                                                                                                                                                                                                                                        |
   +-----------------------+---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Monitoring metrics    | Perform monitoring based on the actual situation. | Under the same load, the number of function instances decreases significantly.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   +-----------------------+---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Flow control error    | Not involved.                                     | When there are too many requests, the error code in the body is **FSS.0429**, the status in the response header is **429**, and the error message is **Your request has been controlled by overload sdk, please retry later**.                                                                                                                                                                                                                                                                                                  |
   +-----------------------+---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


Configuring Single-Instance Multi-Concurrency
---------------------------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Concurrency**.

   Set parameters by referring to :ref:`Table 2 <functiongraph_01_0303__en-us_topic_0000001252067196_table1167224813179>` and click **Save**.


   .. figure:: /_static/images/en-us_image_0000001387407430.png
      :alt: **Figure 1** Concurrency configuration

      **Figure 1** Concurrency configuration

   .. _functiongraph_01_0303__en-us_topic_0000001252067196_table1167224813179:

   .. table:: **Table 2** Description

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================================+
      | Max. Requests per Instance        | Number of concurrent requests supported by a single instance. Value range: 1-1000.                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. Instances per Function       | Maximum number of instances in which a function can run. Default: **400**. Maximum: **1000**. **-1**: The function can run in any number of instances. **0**: The function is disabled.                        |
      |                                   |                                                                                                                                                                                                                |
      |                                   | .. note::                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                |
      |                                   |    Requests that exceed the processing capability of instances will be discarded.                                                                                                                              |
      |                                   |                                                                                                                                                                                                                |
      |                                   |    Errors caused by excessive requests will not be displayed in function logs. You can obtain error details by referring to :ref:`Configuring Asynchronous Execution Notification <functiongraph_01_0390_03>`. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Configuration Constraints
-------------------------

-  For Python functions, threads on an instance are bound to one core due to the Python Global Interpreter Lock (GIL) lock. As a result, concurrent requests can only be processed using the single core, not multiple cores. The function processing performance cannot be improved even if larger resource specifications are configured.
-  For Node.js functions, the single-process single-thread processing of the V8 engine results in processing of concurrent requests only using a single core, not multiple cores. The function processing performance cannot be improved even if larger resource specifications are configured.
