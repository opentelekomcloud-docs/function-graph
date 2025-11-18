:original_name: functiongraph_06_0109.html

.. _functiongraph_06_0109:

Deleting a Function or Function Version
=======================================

Function
--------

This API is used to delete a function or a non-latest version of a function.

If the URN contains a function version or alias, the function version or the version corresponding to the specified alias as well as associated triggers will be deleted.

If the URN does not contain a function version or alias, the entire function (including all of its versions, aliases, and triggers) will be deleted.

URI
---

DELETE /v2/{project_id}/fgs/functions/{function_urn}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`.                                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | function_urn    | Yes             | String          | Function URN. For details, see the function model descriptions.                                                                                     |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The latest version of a function cannot be deleted. To delete a function and all its versions, provide a URN without any version or alias. Example: |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | urn:fss:xxxxxxxx:7aad83af3e8d42e99ac194e8419e2c9b:function:default:test.                                                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

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

**Status code: 401**

.. table:: **Table 3** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Delete a function or a function version.

.. code-block:: text

   DELETE https://{Endpoint}/v2/{project_id}/fgs/functions/{func_urn}

Example Responses
-----------------

None

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
204         No Content
401         Unauthorized.
403         Forbidden.
404         Not found.
500         Internal server error.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
