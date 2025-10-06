:original_name: functiongraph_01_1834.html

.. _functiongraph_01_1834:

Managing Function Logs
======================

.. _functiongraph_01_1834__en-us_topic_0000001251924344_section15548615132812:

Using LTS to Manage Function Logs
---------------------------------

You can enable LTS to better manage function logs. After you enable LTS, FunctionGraph automatically creates a log group starting with **functiongraph**. When you create a function, a log stream starting with the function name is generated.

.. note::

   -  By default, 20 log streams are created, which cannot be customized. On the **Logs** tab page of the function, press **F12** to find out the log stream ID of the **query** API, and then locate the corresponding log stream ID in LTS.

      |image1|

   -  Deleting a function log group by mistake on the LTS console will not be detected by FunctionGraph, and the historical log data can no longer be retrieved. To use a log group, modify the function description and save the changes. A new log group will be created.

#. Enable LTS.
#. Set filter criteria.

   -  **Request List**: Filter requests by request ID, result (success or failure), or cause (initialization failed, load failed, system error, timed out, out of memory, out of disk space, or code error).
   -  **Request Log**: Filter logs by keyword, request ID, or instance ID.

   .. table:: **Table 1** Invocation result

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Result                            | Description                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================+
      | Execution successful              | Log printed when a function is successfully executed.                                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Execution failed                  | Log printed when a function fails to be executed due to invocation timeout, memory or disk threshold exceeded, or code errors.                                          |
      |                                   |                                                                                                                                                                         |
      |                                   | To view the logs about invocation timeout, select **Invocation timed out** from the drop-down list. The methods for viewing the other three types of logs are the same. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Cause analysis

      +---------------------------+----------------------------------------------------------------------------------+
      | Cause                     | Description                                                                      |
      +===========================+==================================================================================+
      | Initialization failed     | Log printed when the function initialization fails.                              |
      +---------------------------+----------------------------------------------------------------------------------+
      | Load failed               | Log generated when the runtime fails to load your function file.                 |
      +---------------------------+----------------------------------------------------------------------------------+
      | System error              | Internal error.                                                                  |
      +---------------------------+----------------------------------------------------------------------------------+
      | Invocation timed out      | Log printed when the function invocation period is longer than the preset limit. |
      +---------------------------+----------------------------------------------------------------------------------+
      | Memory threshold exceeded | Log printed when the function memory size exceeds the preset limit.              |
      +---------------------------+----------------------------------------------------------------------------------+
      | Disk threshold exceeded   | Log printed when the disk size exceeds the preset limit.                         |
      +---------------------------+----------------------------------------------------------------------------------+
      | Code error                | Log printed when a code error occurs.                                            |
      +---------------------------+----------------------------------------------------------------------------------+

   .. note::

      -  You can view logs of the last hour, last day, last 3 days, or a custom time period.
      -  To manage function logs, go to the LTS console.
      -  Max. 10 MB logs can be retained for common instances during initialization. When this limit is reached, the latest logs replace the old ones.

.. |image1| image:: /_static/images/en-us_image_0000001258086894.png
