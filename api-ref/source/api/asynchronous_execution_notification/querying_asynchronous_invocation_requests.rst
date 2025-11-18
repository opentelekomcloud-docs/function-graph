:original_name: functiongraph_06_0112_00_3.html

.. _functiongraph_06_0112_00_3:

Querying Asynchronous Invocation Requests
=========================================

Function
--------

This API is used to query the asynchronous invocation requests of a function.

URI
---

GET /v2/{project_id}/fgs/functions/{function_urn}/async-invocations

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                         |
   +==============+===========+========+=====================================================================================+
   | project_id   | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | function_urn | Yes       | String | Function URN. For details, see the function model description.                      |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                                        |
   +==================+=================+=================+====================================================================================================================================================================+
   | request_id       | No              | String          | ID of the asynchronous invocation request to be queried. If this parameter is not specified, all asynchronous invocation requests are queried by default.          |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | Minimum: **0**                                                                                                                                                     |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | Maximum: **64**                                                                                                                                                    |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker           | No              | String          | Start position of the current query. The default value is 0.                                                                                                       |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | Default: **0**                                                                                                                                                     |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | Minimum: **0**                                                                                                                                                     |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | Maximum: **64**                                                                                                                                                    |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit            | No              | String          | Maximum number of data records returned in a request. Max.: 500. Default: 100.                                                                                     |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | Default: **100**                                                                                                                                                   |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | Minimum: **0**                                                                                                                                                     |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | Maximum: **64**                                                                                                                                                    |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status           | No              | String          | Asynchronous invocation status to be queried. Five statuses are supported. If this parameter is not specified, the invocation records of all statuses are queried. |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | -  WAIT                                                                                                                                                            |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | -  RUNNING                                                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | -  SUCCESS                                                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | -  FAIL                                                                                                                                                            |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | -  DISCARD                                                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | Minimum: **0**                                                                                                                                                     |
   |                  |                 |                 |                                                                                                                                                                    |
   |                  |                 |                 | Maximum: **64**                                                                                                                                                    |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query_begin_time | No              | String          | Start time of the query. The format is "YYYY-MM-DD'T'HH:mm:ss" (UTC time). If this parameter is not specified, the time starts from the last hour by default.      |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query_end_time   | No              | String          | End time of the query. The format is "YYYY-MM-DD'T'HH:mm:ss" (UTC time). If this parameter is not specified, the end time is the current time by default.          |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-------------+--------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+
   | Parameter   | Type                                                                                                                                 | Description                                           |
   +=============+======================================================================================================================================+=======================================================+
   | invocations | Array of :ref:`ListFunctionAsyncInvocationsResult <functiongraph_06_0112_00_3__response_listfunctionasyncinvocationsresult>` objects | Asynchronous invocation records.                      |
   +-------------+--------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+
   | count       | Integer                                                                                                                              | Total number of queried data records.                 |
   +-------------+--------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+
   | next_marker | Integer                                                                                                                              | Start position for querying records on the next page. |
   +-------------+--------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+

.. _functiongraph_06_0112_00_3__response_listfunctionasyncinvocationsresult:

.. table:: **Table 5** ListFunctionAsyncInvocationsResult

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                      |
   +=======================+=======================+==================================================================================================+
   | request_id            | String                | Asynchronous invocation request ID.                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | status                | String                | Asynchronous invocation status. Options:                                                         |
   |                       |                       |                                                                                                  |
   |                       |                       | -  WAIT                                                                                          |
   |                       |                       |                                                                                                  |
   |                       |                       | -  RUNNING                                                                                       |
   |                       |                       |                                                                                                  |
   |                       |                       | -  SUCCESS                                                                                       |
   |                       |                       |                                                                                                  |
   |                       |                       | -  FAIL                                                                                          |
   |                       |                       |                                                                                                  |
   |                       |                       | -  DISCARD                                                                                       |
   |                       |                       |                                                                                                  |
   |                       |                       | Enumeration values:                                                                              |
   |                       |                       |                                                                                                  |
   |                       |                       | -  **WAIT**                                                                                      |
   |                       |                       |                                                                                                  |
   |                       |                       | -  **RUNNING**                                                                                   |
   |                       |                       |                                                                                                  |
   |                       |                       | -  **SUCCESS**                                                                                   |
   |                       |                       |                                                                                                  |
   |                       |                       | -  **FAIL**                                                                                      |
   |                       |                       |                                                                                                  |
   |                       |                       | -  **DISCARD**                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | error_message         | String                | Asynchronous invocation error information. If the execution is successful, no value is returned. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | error_code            | Integer               | Asynchronous invocation error code. If the execution is successful, 0 is returned.               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | start_time            | String                | Start time of the asynchronous invocation. The format is "YYYY-MM-DD'T'HH:mm:ss" (UTC time).     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | end_time              | String                | End time of the asynchronous invocation. The format is "YYYY-MM-DD'T'HH:mm:ss" (UTC time).       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

**Status code: 403**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Query asynchronous invocation requests of a function.

.. code-block:: text

   GET /v2/{project_id}/fgs/functions/{function_urn}/async-invocations

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "invocations" : [ {
       "request_id" : "403fcbd6-ec41-401f-9fa7-386f3d3d****",
       "status" : "SUCCESS",
       "error_message" : "",
       "start_time" : "2019-10-25T15:37:27",
       "end_time" : "2019-10-25T15:37:27",
       "error_code" : 0
     } ]
   }

**Status code: 403**

FORBIDDEN

.. code-block::

   {
     "error_code" : "FSS.0403",
     "error_msg" : "invalid token"
   }

**Status code: 404**

Not Found

.. code-block::

   {
     "error_code" : "FSS.0404",
     "error_msg" : "can not find function"
   }

**Status code: 500**

Internal error.

.. code-block::

   {
     "error_code" : "FSS.0500",
     "error_msg" : "xxx"
   }

Status Codes
------------

=========== ===============
Status Code Description
=========== ===============
200         OK
403         FORBIDDEN
404         Not Found
500         Internal error.
=========== ===============

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
