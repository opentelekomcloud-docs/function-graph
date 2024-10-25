:original_name: functiongraph_06_0125.html

.. _functiongraph_06_0125:

Executing a Function Synchronously
==================================

Function
--------

This API is used to execute a function synchronously. Clients must wait for explicit responses to their requests from the function. Responses are returned only after function invocation is complete.

URI
---

POST /v2/{project_id}/fgs/functions/{function_urn}/invocations

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                         |
   +==============+===========+========+=====================================================================================+
   | project_id   | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | function_urn | Yes       | String | Function URN. For details, see the function model description.                      |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                   |
   +=======================+=================+=================+===============================================================================================================================================+
   | X-Auth-Token          | Yes             | String          | User token.                                                                                                                                   |
   |                       |                 |                 |                                                                                                                                               |
   |                       |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is the user token. |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type          | Yes             | String          | Message body type (format).                                                                                                                   |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Cff-Log-Type        | No              | String          | Options: tail (4 KB logs will be returned) and null (no logs will be returned).                                                               |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | X-CFF-Request-Version | No              | String          | Response body format. Options: v0 and v1.                                                                                                     |
   |                       |                 |                 |                                                                                                                                               |
   |                       |                 |                 | -  v0: text format.                                                                                                                           |
   |                       |                 |                 | -  v1: JSON format. Select this format when using an SDK.                                                                                     |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   ================ ========= ====== ======================================
   Parameter        Mandatory Type   Description
   ================ ========= ====== ======================================
   {Customized_key} Yes       Object Request body for executing a function.
   ================ ========= ====== ======================================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response header parameters

   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                                                                               |
   +========================+=======================+===========================================================================================================================================================+
   | X-Cff-Invoke-Summary   | String                | Execution summary of the synchronous invocation.                                                                                                          |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Cff-Request-Id       | String                | Request ID of the synchronous invocation.                                                                                                                 |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Cff-Function-Log     | String                | User log of the synchronous invocation. Set X-Cff-Log-Type:tail in the request header. Intercept and encode the last 2,000 bytes of the log using Base64. |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-CFF-Billing-Duration | String                | Billing information of the synchronous invocation.                                                                                                        |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Cff-Response-Version | String                | Response format:                                                                                                                                          |
   |                        |                       |                                                                                                                                                           |
   |                        |                       | v0: text format                                                                                                                                           |
   |                        |                       |                                                                                                                                                           |
   |                        |                       | v1: JSON format                                                                                                                                           |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Func-Err-Code        | String                | Error code of the synchronous invocation. The value is 0 if the execution is successful.                                                                  |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Is-Func-Err          | String                | Indicates whether the error occurs in a user function.                                                                                                    |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 5** Response body parameters

   ========== ======= ==========================
   Parameter  Type    Description
   ========== ======= ==========================
   request_id String  Request ID.
   result     String  Function execution result.
   log        String  Function execution log.
   status     Integer Function execution status.
   ========== ======= ==========================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 503**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Execute a function synchronously with the request parameter as a key pair ("k":"v").

.. code-block:: text

   POST /v2/{project_id}/fgs/functions/{function_urn}/invocations

   {
     "k" : "v"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "result" : "{\"statusCode\": 200, \"isBase64Encoded\": false, \"body\": \"{\\\"key\\\": \\\"value\\\"}\", \"headers\": {\"Content-Type\": \"application/json\"}}",
     "log" : "2022-09-20T11:43:57Z Start invoke request '1cbe80f3-3c65-475e-ad88-76ac518d386a', version: v1\nHello, World!\n\n2022-09-20T11:43:58Z Finish invoke request '1cbe80f3-3c65-475e-ad88-76ac518d386a', duration: 65.828ms, billing duration: 66ms, memory used: 21.473MB, billing memory: 128MB",
     "status" : 200,
     "request_id" : "1cbe80f3-3c65-475e-ad88-76ac518d386x"
   }

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
200         OK
400         Bad request.
401         Unauthorized.
403         Forbidden.
404         Not found.
500         Internal server error.
503         Service unavailable.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
