:original_name: functiongraph_01_0303.html

.. _functiongraph_01_0303:

Configuring Concurrency
=======================

Overview
--------

FunctionGraph allows you to configure the maximum number of instances that can be run for a function at a time. The number of instances is limited to prevent resource exhaustion, ensure that each instance has sufficient resources to run, and improve processing efficiency.

Configuring Function Concurrency
--------------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Concurrency**.

   Set parameters by referring to :ref:`Table 1 <functiongraph_01_0303__en-us_topic_0000001252067196_table1167224813179>` and click **Save**.


   .. figure:: /_static/images/en-us_image_0000002225526736.png
      :alt: **Figure 1** Concurrency configuration

      **Figure 1** Concurrency configuration

   .. _functiongraph_01_0303__en-us_topic_0000001252067196_table1167224813179:

   .. table:: **Table 1** Description

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================+
      | Max. Instances per Function       | **Explanation**:                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                             |
      |                                   | Maximum number of on-demand instances that can be enabled for a function.                                                                                                                                   |
      |                                   |                                                                                                                                                                                                             |
      |                                   | **Restrictions:**                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                             |
      |                                   | -  Requests that exceed the processing capability of instances will be discarded.                                                                                                                           |
      |                                   | -  Errors caused by excessive requests will not be displayed in function logs. You can obtain error details by referring to :ref:`Configuring Asynchronous Notification Policy <functiongraph_01_0390_03>`. |
      |                                   |                                                                                                                                                                                                             |
      |                                   | **Value range**:                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                             |
      |                                   | -1 or an integer ranging from 1 to 1000. The value **-1** indicates that the number of instances is not limited.                                                                                            |
      |                                   |                                                                                                                                                                                                             |
      |                                   | **Default value**:                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                             |
      |                                   | 400                                                                                                                                                                                                         |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Configuration Constraints
-------------------------

-  For Python functions, threads on an instance are bound to one core due to the Python Global Interpreter Lock (GIL) lock. As a result, concurrent requests can only be processed using the single core, not multiple cores. The function processing performance cannot be improved even if larger resource specifications are configured.
-  For Node.js functions, the single-process single-thread processing of the V8 engine results in processing of concurrent requests only using a single core, not multiple cores. The function processing performance cannot be improved even if larger resource specifications are configured.
