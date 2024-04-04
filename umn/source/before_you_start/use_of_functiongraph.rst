:original_name: functiongraph_01_0110.html

.. _functiongraph_01_0110:

Use of FunctionGraph
====================

FunctionGraph allows you to run your code without provisioning or managing servers, while ensuring high availability and scalability. All you need to do is upload your code and set execution conditions, and FunctionGraph will take care of the rest.

Process
-------

:ref:`Figure 1 <functiongraph_01_0110__en-us_topic_0000001251907944_fig24661772619>` shows the process of using functions.

#. Write code, package and upload it to FunctionGraph, and add event sources such as Simple Message Notification (SMN), Object Storage Service (OBS), and API Gateway (APIG) event sources to build applications.

#. Functions are triggered by RESTful API calls or event sources to achieve expected service purposes. During this process, FunctionGraph automatically schedules resources.

#. View logs and metrics. Note that you will be billed based on code execution duration.

   .. _functiongraph_01_0110__en-us_topic_0000001251907944_fig24661772619:

   .. figure:: /_static/images/en-us_image_0000001252067288.png
      :alt: **Figure 1** Flowchart

      **Figure 1** Flowchart

The following shows the details:

#. Write code.

   Write code in Node.js, Python, Java, or Go.

#. Upload code.

   Edit code inline, upload a local ZIP or JAR file, or upload a ZIP file from OBS. For details, see :ref:`Creating a Deployment Package <functiongraph_01_0152>`.

#. Trigger functions by API calls or cloud service events.

   Functions are triggered by API calls or cloud service events. For details, see :ref:`Creating Triggers <functiongraph_01_0200>`.

#. Implement auto scaling.

   FunctionGraph implements auto scaling based on the number of requests. For details, see section "Notes and Constraints".

#. View logs.

   View run logs of function. FunctionGraph is interconnected with Log Tank Service (LTS). For details, see :ref:`Logs <functiongraph_01_1833>`.

#. View monitoring information.

   View graphical monitoring information. FunctionGraph is interconnected with Cloud Eye. For details, see :ref:`Metrics <functiongraph_01_0211>`.

.. _functiongraph_01_0110__en-us_topic_0000001251907944_section123696302544:

Introduction to Dashboard
-------------------------

Log in to the FunctionGraph console and choose **Dashboard** in the navigation pane on the left.

-  View your created functions/function quota, used storage/storage quota, and monthly invocations and resource usage.


   .. figure:: /_static/images/en-us_image_0000001629968978.png
      :alt: **Figure 2** Monthly statistics

      **Figure 2** Monthly statistics

-  View tenant-level metrics, including invocations, errors, duration, and throttles.

   :ref:`Table 1 <functiongraph_01_0110__en-us_topic_0000001251907944_table34086103152643>` describes the function metrics.

   .. _functiongraph_01_0110__en-us_topic_0000001251907944_table34086103152643:

   .. table:: **Table 1** Function metrics

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Metric                | Unit                  | Description                                                                                                                                                                                                 |
      +=======================+=======================+=============================================================================================================================================================================================================+
      | Invocations           | Count                 | Total number of invocation requests, including invocation errors and throttled invocations. In case of asynchronous invocation, the count starts only when a function is executed in response to a request. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Duration              | ms                    | **Maximum duration**: the maximum duration all functions are executed at a time within a period.                                                                                                            |
      |                       |                       |                                                                                                                                                                                                             |
      |                       |                       | **Minimum duration**: the minimum duration all functions are executed at a time within a period.                                                                                                            |
      |                       |                       |                                                                                                                                                                                                             |
      |                       |                       | **Average duration**: the average duration all functions are executed at a time within a period.                                                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Errors                | Count                 | Number of times that your functions failed with error code **200** being returned. Errors caused by function syntax or execution are also included.                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Throttles             | Count                 | Number of times that FunctionGraph throttles your functions due to the resource limit.                                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
