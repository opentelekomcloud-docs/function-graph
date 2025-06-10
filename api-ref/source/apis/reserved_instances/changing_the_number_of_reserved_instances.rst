:original_name: functiongraph_06_0112_1.html

.. _functiongraph_06_0112_1:

Changing the Number of Reserved Instances
=========================================

Function
--------

This API is used to change the number of reserved instances.

URI
---

PUT /v2/{project_id}/fgs/functions/{function_urn}/reservedinstances

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

   ========= ========= ======= ================================
   Parameter Mandatory Type    Description
   ========= ========= ======= ================================
   count     Yes       Integer Number of reserved instances.
   idle_mode No        Boolean Whether to enable the idle mode.
   ========= ========= ======= ================================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ========= ======= =============================
   Parameter Type    Description
   ========= ======= =============================
   count     Integer Number of reserved instances.
   idle_mode Boolean Whether to enable idle mode.
   ========= ======= =============================

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

Update the number of a function's reserved instances to 3.

.. code-block:: text

   PUT https://{Endpoint}/v2/{project_id}/fgs/functions/{function_urn}/reservedinstances

   {
     "count" : 3
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "count" : 2
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
