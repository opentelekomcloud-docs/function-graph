:original_name: functiongraph_23_1031_03.html

.. _functiongraph_23_1031_03:

Querying the Available ServiceBridge Version
============================================

Function
--------

This API is used to query the available ServiceBridge version.

URI
---

GET /v2/{project_id}/fgs/servicebridge/version

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                         |
   +============+===========+========+=====================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+----------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                              |
   +===========+===========+========+==========================================================+
   | type      | Yes       | String | ServiceBridge type. The value can be rds, mqs, or cache. |
   +-----------+-----------+--------+----------------------------------------------------------+

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

   +-----------+--------------------------------------------------------------------------------------------------------+-------------+
   | Parameter | Type                                                                                                   | Description |
   +===========+========================================================================================================+=============+
   | [items]   | Array of :ref:`ServiceBridgeVersion <functiongraph_23_1031_03__response_servicebridgeversion>` objects |             |
   +-----------+--------------------------------------------------------------------------------------------------------+-------------+

.. _functiongraph_23_1031_03__response_servicebridgeversion:

.. table:: **Table 5** ServiceBridgeVersion

   ========= ====== ==================================
   Parameter Type   Description
   ========= ====== ==================================
   name      String Code package name.
   version   String Code version.
   code_url  String OBS path where the code is stored.
   ========= ====== ==================================

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

Query the available version of the ServiceBridge function of the rds type.

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/fgs/servicebridge/version?type=rds

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   [ {
     "name" : "xxx",
     "version" : "xxx",
     "code_url" : "xxx"
   } ]

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
200         ok
400         Bad request.
401         Unauthorized.
403         Forbidden.
500         Internal server error.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
