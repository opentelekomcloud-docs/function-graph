:original_name: functiongraph_01_0213.html

.. _functiongraph_01_0213:

FunctionGraph Metrics
=====================

Introduction
------------

This section describes the FunctionGraph namespaces, function metrics, and dimensions reported to Cloud Eye. You can view function metrics and alarms by using the Cloud Eye console or calling APIs.

Namespaces
----------

SYS.FunctionGraph

Constraints
-----------

The metrics displayed on the console vary depending on the region. All metrics supported by FunctionGraph are listed here.

Function Metrics
----------------

.. table:: **Table 1** Function metrics

   +---------------------+--------------------+---------------------------------------------------------------------------------------------------------+-------------+--------+-----------------+------------------------------+----------------------------------------+
   | Metric ID           | Metric Name        | Description                                                                                             | Value Range | Unit   | Conversion Rule | Monitored Object (Dimension) | Monitoring Period of Raw Data (Minute) |
   +=====================+====================+=========================================================================================================+=============+========+=================+==============================+========================================+
   | count               | Invocations        | Number of function invocations.                                                                         | >= 0        | Count  | None            | Function                     | 5                                      |
   +---------------------+--------------------+---------------------------------------------------------------------------------------------------------+-------------+--------+-----------------+------------------------------+----------------------------------------+
   | failcount           | Errors             | Number of invocation errors.                                                                            | >= 0        | Count  | None            | Function                     | 5                                      |
   |                     |                    |                                                                                                         |             |        |                 |                              |                                        |
   |                     |                    | The following errors are included:                                                                      |             |        |                 |                              |                                        |
   |                     |                    |                                                                                                         |             |        |                 |                              |                                        |
   |                     |                    | -  Function request error (causing an execution failure and returning status code 200)                  |             |        |                 |                              |                                        |
   |                     |                    | -  Function syntax or execution error                                                                   |             |        |                 |                              |                                        |
   +---------------------+--------------------+---------------------------------------------------------------------------------------------------------+-------------+--------+-----------------+------------------------------+----------------------------------------+
   | rejectcount         | Throttles          | Number of function throttles.                                                                           | >= 0        | Count  | None            | Function                     | 5                                      |
   |                     |                    |                                                                                                         |             |        |                 |                              |                                        |
   |                     |                    | It indicates the number of times that FunctionGraph throttles your functions due to the resource limit. |             |        |                 |                              |                                        |
   +---------------------+--------------------+---------------------------------------------------------------------------------------------------------+-------------+--------+-----------------+------------------------------+----------------------------------------+
   | concurrency         | Concurrency        | The number of requests that can be processed concurrently.                                              | >= 0        | Count  | None            | Function                     | 5                                      |
   +---------------------+--------------------+---------------------------------------------------------------------------------------------------------+-------------+--------+-----------------+------------------------------+----------------------------------------+
   | reservedinstancenum | Reserved Instances | Number of instances reserved for running a function.                                                    | >= 0        | Count  | None            | Function                     | 5                                      |
   +---------------------+--------------------+---------------------------------------------------------------------------------------------------------+-------------+--------+-----------------+------------------------------+----------------------------------------+
   | duration            | Average Duration   | Average duration of function invocation.                                                                | >= 0 ms     | ms     | None            | Function                     | 5                                      |
   +---------------------+--------------------+---------------------------------------------------------------------------------------------------------+-------------+--------+-----------------+------------------------------+----------------------------------------+
   | maxDuration         | Maximum Duration   | Maximum duration of function invocation.                                                                | >= 0 ms     | ms     | None            | Function                     | 5                                      |
   +---------------------+--------------------+---------------------------------------------------------------------------------------------------------+-------------+--------+-----------------+------------------------------+----------------------------------------+
   | minDuration         | Minimum Duration   | Minimum duration of function invocation.                                                                | >= 0 ms     | ms     | None            | Function                     | 5                                      |
   +---------------------+--------------------+---------------------------------------------------------------------------------------------------------+-------------+--------+-----------------+------------------------------+----------------------------------------+

Dimensions
----------

.. table:: **Table 2** Dimensions

   +-----------------------------------+------------------------------------+
   | Key                               | Value                              |
   +===================================+====================================+
   | package-functionname              | *App name*\ ``-``\ *Function name* |
   |                                   |                                    |
   |                                   | Example: default-myfunction_Python |
   +-----------------------------------+------------------------------------+
   | projectId                         | Project ID of the tenant           |
   +-----------------------------------+------------------------------------+
