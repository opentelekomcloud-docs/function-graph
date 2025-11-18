:original_name: functiongraph_06_1022.html

.. _functiongraph_06_1022:

Querying Resource Tags
======================

Function
--------

This API is used to query resource tags.

URI
---

GET /v2/{project_id}/{resource_type}/tags

.. table:: **Table 1** Path Parameters

   +---------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                         |
   +===============+===========+========+=====================================================================================+
   | project_id    | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------+
   | resource_type | Yes       | String | Resource type. Enter "functions" here.                                              |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------+

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

   +-----------+---------------------------------------------------------------------------+--------------+
   | Parameter | Type                                                                      | Description  |
   +===========+===========================================================================+==============+
   | tags      | Array of :ref:`TagItem <functiongraph_06_1022__response_tagitem>` objects | Tag list.    |
   +-----------+---------------------------------------------------------------------------+--------------+
   | sys_tags  | Array of :ref:`TagItem <functiongraph_06_1022__response_tagitem>` objects | System tags. |
   +-----------+---------------------------------------------------------------------------+--------------+

.. _functiongraph_06_1022__response_tagitem:

.. table:: **Table 4** TagItem

   ========= ================ ===========
   Parameter Type             Description
   ========= ================ ===========
   key       String           Key.
   values    Array of strings Value.
   ========= ================ ===========

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

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Query resource tags.

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/{resource_type}/tags

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "tags" : [ {
       "key" : "xxx",
       "values" : [ "yyy", "zzz" ]
     } ],
     "sys_tags" : [ {
       "key" : "_sys_enterprise_project_id",
       "values" : [ "5aa119a8-d25b-45a7-8d1b-88e127885635" ]
     } ]
   }

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
