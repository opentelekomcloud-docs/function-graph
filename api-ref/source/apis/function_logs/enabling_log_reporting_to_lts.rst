:original_name: functiongraph_06_0112_01.html

.. _functiongraph_06_0112_01:

Enabling Log Reporting to LTS
=============================

Function
--------

This API is used to enable log reporting to LTS.

URI
---

POST /v2/{project_id}/fgs/functions/enable-lts-logs

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                         |
   +============+===========+========+=====================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
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

**Status code: 429**

.. table:: **Table 3** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Enable log reporting to LTS.

.. code-block:: text

   POST /v2/{project_id}/fgs/functions/enable-lts-logs

Example Responses
-----------------

**Status code: 429**

Too many requests.

.. code-block::

   {
     "error_code" : "FSS.0429",
     "error_msg" : "api is busy now"
   }

Status Codes
------------

=========== ==================
Status Code Description
=========== ==================
200         ok
429         Too many requests.
=========== ==================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
