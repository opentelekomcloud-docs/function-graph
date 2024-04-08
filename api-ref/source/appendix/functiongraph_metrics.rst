:original_name: functiongraph_06_1340.html

.. _functiongraph_06_1340:

FunctionGraph Metrics
=====================

Introduction
------------

This section describes the function metrics reported to Cloud Eye.

Their namespace and dimension are also included. You can view monitoring graphs and alarm messages on the Cloud Eye console.

Namespace
---------

SYS.FunctionGraph

Function Metrics
----------------

.. table:: **Table 1** Function metrics

   +-------------+------------------+--------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+--------------------------------------------------------+----------------------+
   | Metric      | Display Name     | Description                                            | Unit  | Upper Limit | Lower Limit | Recommended Threshold | Value Type | Meaning                                                | Dimension            |
   +=============+==================+========================================================+=======+=============+=============+=======================+============+========================================================+======================+
   | count       | Invocations      | Number of times a function is invoked                  | Count | ``-``       | 0           | ``-``                 | Int        | Number of times a function is invoked                  | package-functionname |
   +-------------+------------------+--------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+--------------------------------------------------------+----------------------+
   | failcount   | Errors           | Number of errors that occur when a function is invoked | Count | ``-``       | 0           | ``-``                 | Int        | Number of errors that occur when a function is invoked | package-functionname |
   +-------------+------------------+--------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+--------------------------------------------------------+----------------------+
   | rejectcount | Throttles        | Number of times a function is throttled when invoked   | Count | ``-``       | 0           | ``-``                 | Int        | Number of times a function is throttled when invoked   | package-functionname |
   +-------------+------------------+--------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+--------------------------------------------------------+----------------------+
   | duration    | Average Duration | Average time a function is invoked                     | ms    | ``-``       | 0           | ``-``                 | Int        | Average time a function is invoked                     | package-functionname |
   +-------------+------------------+--------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+--------------------------------------------------------+----------------------+
   | maxDuration | Maximum Duration | Maximum time a function is invoked                     | ms    | ``-``       | 0           | ``-``                 | Int        | Maximum time a function is invoked                     | package-functionname |
   +-------------+------------------+--------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+--------------------------------------------------------+----------------------+
   | minDuration | Minimum Duration | Minimum time a function is invoked                     | ms    | ``-``       | 0           | ``-``                 | Int        | Minimum time a function is invoked                     | package-functionname |
   +-------------+------------------+--------------------------------------------------------+-------+-------------+-------------+-----------------------+------------+--------------------------------------------------------+----------------------+

Dimension
---------

.. table:: **Table 2** Dimension

   ==================== ======================
   Key                  Value
   ==================== ======================
   package-functionname App_name-Function_name
   ==================== ======================
