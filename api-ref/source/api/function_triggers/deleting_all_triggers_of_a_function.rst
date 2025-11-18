:original_name: functiongraph_06_0121.html

.. _functiongraph_06_0121:

Deleting All Triggers of a Function
===================================

Function
--------

This API is used to delete all triggers of a function.

If a non-latest function version is specified, all triggers corresponding to the version will be deleted. If an alias is specified, all triggers corresponding to the alias will be deleted. If neither function versions nor aliases are specified or the latest version is specified, all triggers of the function (including all versions and aliases) will be deleted.

URI
---

DELETE /v2/{project_id}/fgs/triggers/{function_urn}

.. table:: **Table 1** Path parameters

   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                         |
   +==============+===========+========+=====================================================================================+
   | project_id   | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | function_urn | Yes       | String | Function URN. For details, see the function model descriptions.                     |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                              |
   +=================+=================+=================+==========================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                              |
   |                 |                 |                 |                                                                                                                          |
   |                 |                 |                 | The token can be obtained by calling the IAM API. The value of X-Subject-Token in the response header is the user token. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Message body type or format.                                                                                             |
   |                 |                 |                 |                                                                                                                          |
   |                 |                 |                 | Default value: **application/json**                                                                                      |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 3** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

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

**Status code**: **404**

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

Delete all triggers of a function.

.. code-block:: text

   DELETE https://{Endpoint}/v2/{project_id}/fgs/triggers/{function_urn}

Example Responses
-----------------

None

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
204         No Content
400         Bad request.
401         Unauthorized.
403         Forbidden.
404         Not found.
500         Internal server error.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
