:original_name: functiongraph_06_0146_00_1.html

.. _functiongraph_06_0146_00_1:

Stopping an Asynchronous Invocation Request
===========================================

Function
--------

This API is used to stop asynchronous invocation of a function with N concurrent instances. When calling this API, set recursive to false and force to true. The API will also stop the function's other concurrent requests and return "4208 function invocation canceled".

URI
---

POST /v2/{project_id}/fgs/functions/{function_urn}/cancel

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

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                               |
   |                 |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is the user token. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Message body type (format).                                                                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | request_id      | Yes             | String          | ID of a stopped request.                                                                                                                          |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Stop mode. Options: recursive and force. recursive: The subfunction that is being invoked will be stopped. force: Terminate the runtime directly. |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Enumeration values:                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **force**                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **recursive**                                                                                                                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Stop an asynchronous invocation request of a function.

.. code-block:: text

   POST /v2/{project_id}/fgs/functions/{function_urn}/cancel

   {
     "request_id" : "xxxx"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   null

**Status code: 400**

Invalid RequestId

.. code-block::

   {
     "error_code" : "FSS.0400",
     "error_msg" : "Invalid RequestId"
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

=========== =================
Status Code Description
=========== =================
200         OK
400         Invalid RequestId
403         FORBIDDEN
404         Not Found
500         Internal error.
=========== =================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
