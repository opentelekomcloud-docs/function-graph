:original_name: functiongraph_01_0304.html

.. _functiongraph_01_0304:

Creating an Alarm Rule
======================

After creating a function and trigger, you can monitor the invocation and running statuses of the function in real time.

Viewing Function Metrics
------------------------

FunctionGraph differentiates the metrics of a function by version, allowing you to query the metrics of a specific function version.

Procedure
---------

Create an alarm rule for a function to report metrics to Cloud Eye so that you can view monitoring graphs and alarm messages on the Cloud Eye console.

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the name of the desired function.

#. On the displayed function details page, select a function version or alias, and choose **Monitoring** > **Metrics**.

#. Click **Create Alarm Rule**.

#. Set alarm parameters and click **Next** as shown in :ref:`Figure 1 <functiongraph_01_0304__en-us_topic_0000001298507409_fig443464332216>`.

   .. _functiongraph_01_0304__en-us_topic_0000001298507409_fig443464332216:

   .. figure:: /_static/images/en-us_image_0000001630462528.png
      :alt: **Figure 1** Creating an alarm rule

      **Figure 1** Creating an alarm rule

#. Enter a rule name and click **OK**.

.. caution::

   After a function is deleted, the alarm rules created for it will not be updated in real time on the Cloud Eye console and may continue to be displayed there for a maximum of seven days.

Function Metrics
----------------

:ref:`Table 1 <functiongraph_01_0304__en-us_topic_0000001298507409_table8963813131616>` lists the function metrics that can be monitored by Cloud Eye.

.. _functiongraph_01_0304__en-us_topic_0000001298507409_table8963813131616:

.. table:: **Table 1** Function metrics

   +-------------------+-------------------+---------------------------------------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+----------------------+
   | Metric            | Display Name      | Description                                                                           | Unit  | Upper Limit | Lower Limit | Recommended Threshold | Value Type | Dimension            |
   +===================+===================+=======================================================================================+=======+=============+=============+=======================+============+======================+
   | count             | Invocations       | Number of function invocations                                                        | Count | ``-``       | 0           | ``-``                 | int        | package-functionname |
   +-------------------+-------------------+---------------------------------------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+----------------------+
   | failcount         | Errors            | Number of invocation errors                                                           | Count | ``-``       | 0           | ``-``                 | int        | package-functionname |
   +-------------------+-------------------+---------------------------------------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+----------------------+
   | rejectcount       | Throttles         | Number of function throttles                                                          | Count | ``-``       | 0           | ``-``                 | int        | package-functionname |
   +-------------------+-------------------+---------------------------------------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+----------------------+
   | duration          | Average Duration  | Average duration of function invocation                                               | ms    | ``-``       | 0           | ``-``                 | float      | package-functionname |
   +-------------------+-------------------+---------------------------------------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+----------------------+
   | maxDuration       | Maximum Duration  | Maximum duration of function invocation                                               | ms    | ``-``       | 0           | ``-``                 | float      | package-functionname |
   +-------------------+-------------------+---------------------------------------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+----------------------+
   | minDuration       | Minimum Duration  | Minimum duration of function invocation                                               | ms    | ``-``       | 0           | ``-``                 | float      | package-functionname |
   +-------------------+-------------------+---------------------------------------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+----------------------+
   | concurrency       | Concurrency       | The number of requests that can be processed concurrently                             | Count | ``-``       | 0           | ``-``                 | int        | package-functionname |
   +-------------------+-------------------+---------------------------------------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+----------------------+
   | payPerUseInstance | Elastic Instances | Number of instances actually used by a function after reserved instances are excluded | Count | ``-``       | 0           | ``-``                 | int        | package-functionname |
   +-------------------+-------------------+---------------------------------------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+----------------------+
   | failRate          | Error Rate        | Percentage of errors to the total invocations of a function                           | %     | ``-``       | 0           | ``-``                 | float      | package-functionname |
   +-------------------+-------------------+---------------------------------------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+----------------------+
