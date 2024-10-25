:original_name: functiongraph_06_0123.html

.. _functiongraph_06_0123:

Deleting a Trigger
==================

Function
--------

This API is used to delete a trigger.

URI
---

DELETE /v2/{project_id}/fgs/triggers/{function_urn}/{trigger_type_code}/{trigger_id}

.. table:: **Table 1** Path Parameters

   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                         |
   +===================+=================+=================+=====================================================================================+
   | project_id        | Yes             | String          | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
   | function_urn      | Yes             | String          | Function URN. For details, see the function model description.                      |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
   | trigger_type_code | Yes             | String          | Trigger type code.                                                                  |
   |                   |                 |                 |                                                                                     |
   |                   |                 |                 | Enumeration values:                                                                 |
   |                   |                 |                 |                                                                                     |
   |                   |                 |                 | -  **TIMER**                                                                        |
   |                   |                 |                 | -  **APIG**                                                                         |
   |                   |                 |                 | -  **CTS**                                                                          |
   |                   |                 |                 | -  **DDS**                                                                          |
   |                   |                 |                 | -  **DMS**                                                                          |
   |                   |                 |                 | -  **DIS**                                                                          |
   |                   |                 |                 | -  **LTS**                                                                          |
   |                   |                 |                 | -  **OBS**                                                                          |
   |                   |                 |                 | -  **SMN**                                                                          |
   |                   |                 |                 | -  **KAFKA**                                                                        |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
   | trigger_id        | Yes             | String          | Trigger ID.                                                                         |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------+

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
   |                 |                 |                 |                                                                                                                                               |
   |                 |                 |                 | Default: **application/json**                                                                                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

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

Delete a trigger.

.. code-block:: text

   DELETE https://{Endpoint}/v2/{project_id}/fgs/triggers/{function_urn}/{trigger_type_code}/{trigger_id}

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
