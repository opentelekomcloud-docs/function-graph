:original_name: functiongraph_06_0145.html

.. _functiongraph_06_0145:

Querying the Log Group and Stream of a Function
===============================================

Function
--------

This API is used to query the LTS log group and stream settings of a function.

URI
---

GET /v2/{project_id}/fgs/functions/{function_urn}/lts-log-detail

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   =========== ====== ================
   Parameter   Type   Description
   =========== ====== ================
   group_name  String Log group name.
   group_id    String Log group ID.
   stream_id   String Log stream ID.
   stream_name String Log stream name.
   =========== ====== ================

**Status code: 403**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Query the LTS log group and stream settings of a function.

.. code-block:: text

   GET /v2/{project_id}/fgs/functions/{urn}/lts-log-detail

Example Responses
-----------------

**Status code: 200**

Ok

.. code-block::

   {
     "group_id" : "xxx",
     "stream_id" : "xxx",
     "stream_name" : "xxx"
   }

**Status code: 403**

FORBIDDEN

.. code-block::

   {
     "error_code" : "FSS.0403",
     "error_msg" : "invalid token"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         Ok
403         FORBIDDEN
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
