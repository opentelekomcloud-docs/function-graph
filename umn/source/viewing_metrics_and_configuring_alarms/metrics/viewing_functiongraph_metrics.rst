:original_name: functiongraph_01_0212.html

.. _functiongraph_01_0212:

Viewing FunctionGraph Metrics
=============================

FunctionGraph is interconnected with AOM, allowing you to view function metrics without the need for any configurations.

Viewing Function Metrics
------------------------

FunctionGraph collects function metrics and displays aggregated results. Switch to your target function version before viewing metrics.

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. Click the function to be configured to go to the function details page.
#. Choose **Monitoring** > **Metrics**, select an interval (last hour, last 3 hours, last 12 hours, last day, last 3 days, or custom), and check the running status of the function.

Metric Description
------------------

:ref:`Table 1 <functiongraph_01_0212__en-us_topic_0000001298786825_table34086103152643>` describes the function metrics.

.. _functiongraph_01_0212__en-us_topic_0000001298786825_table34086103152643:

.. table:: **Table 1** Function metrics

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Metric                | Unit                  | Description                                                                                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================================================================================+
   | Invocations           | Count                 | Total number of invocation requests, including invocation errors and throttled invocations. In case of asynchronous invocation, the count starts only when a function is executed in response to a request. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Duration              | ms                    | **Maximum duration**: the maximum duration a function is executed within a period.                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                             |
   |                       |                       | **Minimum duration**: the minimum duration a function is executed within a period.                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                             |
   |                       |                       | **Average duration**: the average duration a function is executed within a period.                                                                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Errors                | Count                 | Number of times that your functions failed with status code **200** being returned. Errors caused by function syntax or execution are also included.                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Throttles             | Count                 | Number of times that FunctionGraph throttles your functions due to the resource limit.                                                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Instance Statistics   | Count                 | Numbers of concurrent requests and reserved instances.                                                                                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Memory Usage          | MB                    | **Maximum**: the maximum memory usage during function execution within a period.                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                             |
   |                       |                       | **Minimum**: the minimum memory usage during function execution within a period.                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                             |
   |                       |                       | **Average**: the average memory usage during function execution within a period.                                                                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
