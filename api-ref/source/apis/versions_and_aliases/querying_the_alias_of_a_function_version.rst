:original_name: functiongraph_06_0117.html

.. _functiongraph_06_0117:

Querying the Alias of a Function Version
========================================

Function
--------

This API is used to query the alias of a function version.

URI
---

GET /v2/{project_id}/fgs/functions/{function_urn}/aliases/{alias_name}

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                         |
   +==============+===========+========+=====================================================================================+
   | project_id   | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | function_urn | Yes       | String | Function URN. For details, see the function model description.                      |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | alias_name   | Yes       | String | Alias to be queried.                                                                |
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

   +-----------------------------+----------------------------------------------------------------------------------------+----------------------------------------+
   | Parameter                   | Type                                                                                   | Description                            |
   +=============================+========================================================================================+========================================+
   | name                        | String                                                                                 | Alias to be queried.                   |
   +-----------------------------+----------------------------------------------------------------------------------------+----------------------------------------+
   | version                     | String                                                                                 | Version corresponding to the alias.    |
   +-----------------------------+----------------------------------------------------------------------------------------+----------------------------------------+
   | description                 | String                                                                                 | Description of the alias.              |
   +-----------------------------+----------------------------------------------------------------------------------------+----------------------------------------+
   | last_modified               | String                                                                                 | Time when the alias was last modified. |
   +-----------------------------+----------------------------------------------------------------------------------------+----------------------------------------+
   | alias_urn                   | String                                                                                 | URN of the alias.                      |
   +-----------------------------+----------------------------------------------------------------------------------------+----------------------------------------+
   | additional_version_weights  | Map<String,Integer>                                                                    | Traffic shifting by percentage.        |
   +-----------------------------+----------------------------------------------------------------------------------------+----------------------------------------+
   | additional_version_strategy | Map<String,\ :ref:`VersionStrategy <functiongraph_06_0117__response_versionstrategy>`> | Traffic shifting by rule.              |
   +-----------------------------+----------------------------------------------------------------------------------------+----------------------------------------+

.. _functiongraph_06_0117__response_versionstrategy:

.. table:: **Table 4** VersionStrategy

   +-----------------------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | Parameter             | Type                                                                                                | Description                                                         |
   +=======================+=====================================================================================================+=====================================================================+
   | rules                 | Array of :ref:`VersionStrategyRules <functiongraph_06_0117__response_versionstrategyrules>` objects | Rules.                                                              |
   +-----------------------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | combine_type          | String                                                                                              | Rule aggregation mode. and: All rules are met. or: Any rule is met. |
   |                       |                                                                                                     |                                                                     |
   |                       |                                                                                                     | Enumeration values:                                                 |
   |                       |                                                                                                     |                                                                     |
   |                       |                                                                                                     | -  **and**                                                          |
   |                       |                                                                                                     |                                                                     |
   |                       |                                                                                                     | -  **or**                                                           |
   +-----------------------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+

.. _functiongraph_06_0117__response_versionstrategyrules:

.. table:: **Table 5** VersionStrategyRules

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                          |
   +=======================+=======================+======================================================================================================+
   | rule_type             | String                | Parameter type.                                                                                      |
   |                       |                       |                                                                                                      |
   |                       |                       | Enumeration values:                                                                                  |
   |                       |                       |                                                                                                      |
   |                       |                       | -  **header**                                                                                        |
   |                       |                       |                                                                                                      |
   |                       |                       | -  **cookie**                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | param                 | String                | Rule parameter name, which can contain only letters, digits, underscores (_), and hyphens (-).       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | op                    | String                | Rule matching operator. Currently, only = and in are supported.                                      |
   |                       |                       |                                                                                                      |
   |                       |                       | Enumeration values:                                                                                  |
   |                       |                       |                                                                                                      |
   |                       |                       | -  **in**                                                                                            |
   |                       |                       |                                                                                                      |
   |                       |                       | -  **=**                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | value                 | String                | Rule value. If op is set to in, the value is a multi-value character string separated by commas (,). |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+

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

Query the alias of a function version.

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/fgs/functions/{function_urn}/aliases/{alias_name}

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "name" : "dev",
     "version" : "latest",
     "description" : "my dev version",
     "last_modified" : "2019-10-31 11:37:58",
     "alias_urn" : "urn:fss:xxxxxxxxxx: 7aad83af3e8d42e99ac194e8419e2c9b:function:default:test:!dev",
     "additional_version_weights" : {
       "v1" : 10
     }
   }

**Status code: 401**

Unauthorized.

.. code-block::

   {
     "error_code" : "FSS.1053",
     "error_msg" : "Not found the function alias"
   }

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
200         OK
401         Unauthorized.
403         Forbidden.
404         Not found.
500         Internal server error.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
