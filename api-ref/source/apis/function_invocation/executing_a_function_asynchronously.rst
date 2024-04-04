:original_name: functiongraph_06_0126.html

.. _functiongraph_06_0126:

Executing a Function Asynchronously
===================================

Function
--------

This API is used to execute a function asynchronously.

URI
---

POST /v2/{project_id}/fgs/functions/{function_urn}/invocations-async

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

   +--------------------+-----------+--------+-------------------------------------------------------+
   | Parameter          | Mandatory | Type   | Description                                           |
   +====================+===========+========+=======================================================+
   | {User defined key} | Yes       | Object | Request body for executing a function asynchronously. |
   +--------------------+-----------+--------+-------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   ========== ====== ===========
   Parameter  Type   Description
   ========== ====== ===========
   request_id String Request ID.
   ========== ====== ===========

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 503**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Execute a function asynchronously with the request parameter as a key pair ("k":"v").

.. code-block:: text

   POST /v2/{project_id}/fgs/functions/{function_urn}/invocations-async

   {
     "body" : {
       "k" : "v"
     }
   }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "request_id" : "1167bf8c-87b0-43ab-8f5f-26b16c64f252"
   }

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
202         Accepted
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
