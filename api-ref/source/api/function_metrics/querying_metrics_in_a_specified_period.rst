:original_name: functiongraph_06_0138.html

.. _functiongraph_06_0138:

Querying Metrics in a Specified Period
======================================

Function
--------

This API is used to query metrics of a function in a specified period.

URI
---

GET /v2/{project_id}/fgs/functions/{func_urn}/statistics/{period}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                         |
   +============+===========+========+=====================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | func_urn   | Yes       | String | Function URN. For details, see the function model description.                      |
   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | period     | Yes       | String | Time range specified to query function execution metrics.                           |
   +------------+-----------+--------+-------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                               |
   |                 |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is the user token. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Message body type (format).                                                                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter             | Type                                                                                      | Description                       |
   +=======================+===========================================================================================+===================================+
   | count                 | Array of :ref:`SlaReportsValue <functiongraph_06_0138__response_slareportsvalue>` objects | Function invocations.             |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | duration              | Array of :ref:`SlaReportsValue <functiongraph_06_0138__response_slareportsvalue>` objects | Average latency, in milliseconds. |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | fail_count            | Array of :ref:`SlaReportsValue <functiongraph_06_0138__response_slareportsvalue>` objects | Number of errors.                 |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | max_duration          | Array of :ref:`SlaReportsValue <functiongraph_06_0138__response_slareportsvalue>` objects | Maximum latency, in milliseconds. |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | min_duration          | Array of :ref:`SlaReportsValue <functiongraph_06_0138__response_slareportsvalue>` objects | Minimum latency, in milliseconds. |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | reject_count          | Array of :ref:`SlaReportsValue <functiongraph_06_0138__response_slareportsvalue>` objects | Number of throttles.              |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | function_error_count  | Array of :ref:`SlaReportsValue <functiongraph_06_0138__response_slareportsvalue>` objects | Number of function errors.        |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | system_error_count    | Array of :ref:`SlaReportsValue <functiongraph_06_0138__response_slareportsvalue>` objects | Number of system errors.          |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | reserved_instance_num | Array of :ref:`SlaReportsValue <functiongraph_06_0138__response_slareportsvalue>` objects | Reserved instance metrics.        |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | concurrency_num       | Array of :ref:`SlaReportsValue <functiongraph_06_0138__response_slareportsvalue>` objects | Elastic instance metrics.         |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+

.. _functiongraph_06_0138__response_slareportsvalue:

.. table:: **Table 4** SlaReportsValue

   +-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type    | Description                                                                                                                       |
   +===========+=========+===================================================================================================================================+
   | timestamp | Integer | Timestamp.                                                                                                                        |
   +-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------+
   | value     | Double  | Value. If the value is -1, the metric has no data in the current period. The possible cause is that the function is not executed. |
   +-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Query metrics of a function in a specified period.

.. code-block:: text

   GET /v2/{project_id}/fgs/functions/{func_urn}/statistics/{period}

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "count" : [ {
       "timestamp" : 1596679200000,
       "value" : -1
     }, {
       "timestamp" : 1596682800000,
       "value" : 2
     }, {
       "timestamp" : 1596686400000,
       "value" : -1
     } ],
     "duration" : [ {
       "timestamp" : 1596679200000,
       "value" : -1
     }, {
       "timestamp" : 1596682800000,
       "value" : 950
     }, {
       "timestamp" : 1596686400000,
       "value" : -1
     } ],
     "fail_count" : [ {
       "timestamp" : 1596679200000,
       "value" : -1
     }, {
       "timestamp" : 1596682800000,
       "value" : 0
     }, {
       "timestamp" : 1596686400000,
       "value" : -1
     } ],
     "max_duration" : [ {
       "timestamp" : 1596679200000,
       "value" : -1
     }, {
       "timestamp" : 1596682800000,
       "value" : 740
     }, {
       "timestamp" : 1596686400000,
       "value" : -1
     } ],
     "min_duration" : [ {
       "timestamp" : 1596679200000,
       "value" : -1
     }, {
       "timestamp" : 1596682800000,
       "value" : 210
     }, {
       "timestamp" : 1596686400000,
       "value" : -1
     } ],
     "reject_count" : [ {
       "timestamp" : 1596679200000,
       "value" : -1
     }, {
       "timestamp" : 1596682800000,
       "value" : 0
     }, {
       "timestamp" : 1596686400000,
       "value" : -1
     } ]
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         ok
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
