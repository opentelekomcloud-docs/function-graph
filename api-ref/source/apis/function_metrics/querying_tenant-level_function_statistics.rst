:original_name: functiongraph_06_0139.html

.. _functiongraph_06_0139:

Querying Tenant-Level Function Statistics
=========================================

Function
--------

This API is used to query tenant-level function statistics.

The statistics include function format, quota and usage, and traffic report.

You can query data in a specific period using the filter and period parameters.

URI
---

GET /v2/{project_id}/fgs/functions/statistics

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                         |
   +============+===========+========+=====================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                    |
   +=================+=================+=================+================================================================================================+
   | filter          | Yes             | String          | Parameter filter.                                                                              |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  monitor_data: Query detailed statistics.                                                    |
   |                 |                 |                 | -  monthly_report: Query monthly statistics.                                                   |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | Enumeration values:                                                                            |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **monitor_data**                                                                            |
   |                 |                 |                 | -  **monthly_report**                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+
   | period          | No              | String          | The unit is minute. This parameter must be used together with the filter parameter metric.     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+
   | option          | No              | String          | Monthly statistical period. This parameter is valid only when filter is set to monthly_report. |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | If a value beyond the preceding range is specified, the default value 0 will be used.          |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  0: current month                                                                            |
   |                 |                 |                 | -  1: last month                                                                               |
   |                 |                 |                 | -  2: last three months                                                                        |
   |                 |                 |                 | -  3: last six months                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+
   | limit           | No              | String          | Maximum number of data records returned in a request. Max.: 500. Default: 100.                 |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | Default: **100**                                                                               |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | Minimum: **1**                                                                                 |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | Maximum: **64**                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Start position of the current query. The default value is 0.                                   |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | Default: **0**                                                                                 |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | Minimum: **1**                                                                                 |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | Maximum: **64**                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

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

.. table:: **Table 4** Response body parameters

   +------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------+
   | Parameter  | Type                                                                                                                  | Description                    |
   +============+=======================================================================================================================+================================+
   | count      | Array of :ref:`MonthUsed <functiongraph_06_0139__response_monthused>` objects                                         | Number of monthly invocations. |
   +------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------+
   | gbs        | Array of :ref:`MonthUsed <functiongraph_06_0139__response_monthused>` objects                                         | Monthly resource usage.        |
   +------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------+
   | gpu_gbs    | Array of :ref:`MonthUsed <functiongraph_06_0139__response_monthused>` objects                                         | Monthly GPU usage.             |
   +------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------+
   | statistics | :ref:`ListFunctionStatisticsResponseBody <functiongraph_06_0139__response_listfunctionstatisticsresponsebody>` object | Function Metrics               |
   +------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------+

.. _functiongraph_06_0139__response_monthused:

.. table:: **Table 5** MonthUsed

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   date      String Date.
   value     Number Usage.
   ========= ====== ===========

.. _functiongraph_06_0139__response_listfunctionstatisticsresponsebody:

.. table:: **Table 6** ListFunctionStatisticsResponseBody

   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter             | Type                                                                                      | Description                       |
   +=======================+===========================================================================================+===================================+
   | count                 | Array of :ref:`SlaReportsValue <functiongraph_06_0139__response_slareportsvalue>` objects | Function invocations.             |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | duration              | Array of :ref:`SlaReportsValue <functiongraph_06_0139__response_slareportsvalue>` objects | Average latency, in milliseconds. |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | fail_count            | Array of :ref:`SlaReportsValue <functiongraph_06_0139__response_slareportsvalue>` objects | Number of errors.                 |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | max_duration          | Array of :ref:`SlaReportsValue <functiongraph_06_0139__response_slareportsvalue>` objects | Maximum latency, in milliseconds. |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | min_duration          | Array of :ref:`SlaReportsValue <functiongraph_06_0139__response_slareportsvalue>` objects | Minimum latency, in milliseconds. |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | reject_count          | Array of :ref:`SlaReportsValue <functiongraph_06_0139__response_slareportsvalue>` objects | Number of throttles.              |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | function_error_count  | Array of :ref:`SlaReportsValue <functiongraph_06_0139__response_slareportsvalue>` objects | Number of function errors.        |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | system_error_count    | Array of :ref:`SlaReportsValue <functiongraph_06_0139__response_slareportsvalue>` objects | Number of system errors.          |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | reserved_instance_num | Array of :ref:`SlaReportsValue <functiongraph_06_0139__response_slareportsvalue>` objects | Reserved instance metrics.        |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+
   | concurrency_num       | Array of :ref:`SlaReportsValue <functiongraph_06_0139__response_slareportsvalue>` objects | Elastic instance metrics.         |
   +-----------------------+-------------------------------------------------------------------------------------------+-----------------------------------+

.. _functiongraph_06_0139__response_slareportsvalue:

.. table:: **Table 7** SlaReportsValue

   +-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type    | Description                                                                                                                       |
   +===========+=========+===================================================================================================================================+
   | timestamp | Integer | Timestamp.                                                                                                                        |
   +-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------+
   | value     | Double  | Value. If the value is -1, the metric has no data in the current period. The possible cause is that the function is not executed. |
   +-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Query tenant-level function statistics.

.. code-block:: text

   GET /v2/{project_id}/fgs/functions/statistics

Example Responses
-----------------

**Status code: 200**

Query successful.

.. code-block::

   {
     "statistics" : {
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
   }

Status Codes
------------

=========== =================
Status Code Description
=========== =================
200         Query successful.
400         Bad Request
=========== =================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
