:original_name: functiongraph_06_0133.html

.. _functiongraph_06_0133:

Creating a Test Event
=====================

Function
--------

This API is used to create a test event.

URI
---

POST /v2/{project_id}/fgs/functions/{function_urn}/events

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

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================+
   | name            | Yes             | String          | Test event name. Max. 25 of letters, digits, hyphens (-), and underscores (_). Start with a letter, and end with a letter or digit. |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | Minimum length: 1 character.                                                                                                        |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | Maximum length: 25 characters.                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | content         | Yes             | String          | Test event content, which is a Base64-encoded JSON character string.                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   id        String Test event ID.
   name      String Test event name.
   ========= ====== ================

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

Example Requests
----------------

Create a test event named event-xx with content {"k":"v"}.

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/fgs/functions/{function_urn}/events

   {
     "name" : "event-xx",
     "content" : "eyJrIjoidiJ9"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "id" : "3b659dc0-12fc-40dc-aa05-a321d9424cb3",
     "name" : "event-k9r3"
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
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
