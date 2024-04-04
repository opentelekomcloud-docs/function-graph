:original_name: functiongraph_06_0108_1.html

.. _functiongraph_06_0108_1:

Exporting a Function
====================

Function
--------

This API is used to export a function.

URI
---

GET /v2/{project_id}/fgs/functions/{function_urn}/export

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                         |
   +==============+===========+========+=====================================================================================+
   | project_id   | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | function_urn | Yes       | String | Function URN. For details, see the function model description.                      |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================+
   | config          | No              | Boolean         | Whether to export function configuration. The default value is false. If the type parameter does not exist, at least one of code=true or config=true must be specified. |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | Default: **false**                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code            | No              | Boolean         | Whether to export function code. The default value is false. If the type parameter does not exist, at least one of code=true or config=true must be specified.          |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | Default: **false**                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | This parameter cannot be used with code or config. type=code indicates exporting the code, and type=config indicates exporting the configuration.                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

**Status code: 404**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

-  Export function code only.

   .. code-block:: text

      GET /v2/{project_id}/fgs/functions/{func_urn}/export?type=code

-  Export both function code and configuration.

   .. code-block:: text

      GET /v2/{project_id}/fgs/functions/{func_urn}/export?code=true&config=true

Example Responses
-----------------

**Status code: 404**

Not found.

.. code-block::

   {
     "error_code" : "FSS.1051",
     "error_msg" : "Not found the function"
   }

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
200         ok
404         Not found.
500         Internal server error.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
