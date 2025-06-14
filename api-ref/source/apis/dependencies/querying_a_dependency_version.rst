:original_name: functiongraph_06_0154.html

.. _functiongraph_06_0154:

Querying a Dependency Version
=============================

Function
--------

This API is used to query the details about a dependency version.

URI
---

GET /v2/{project_id}/fgs/dependencies/{depend_id}/version/{version}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                         |
   +============+===========+========+=====================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | depend_id  | Yes       | String | Dependency ID.                                                                      |
   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | version    | Yes       | String | Dependence version.                                                                 |
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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================================================================================================================================================================+
   | id                    | String                | Dependency version ID.                                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | owner                 | String                | Dependency owner.                                                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | link                  | String                | URL of the dependency in OBS.                                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | runtime               | String                | Environment for executing a function. Options: Python2.7 Python 3.6 Python 3.9 Python 3.10 Go 1.x Java 8 Java 11 Node.js 6.10 Node.js 8.10 Node.js 10.16 Node.js 12.13 Node.js 14.18 Node.js 16.17 Node.js 18.15 C# (.NET Core 2.1) C# (.NET Core 3.1) Custom PHP 7.3 HTTP Custom image-based functions |
   |                       |                       |                                                                                                                                                                                                                                                                                                         |
   |                       |                       | Enumeration values:                                                                                                                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                                                         |
   |                       |                       | -  **Java8**                                                                                                                                                                                                                                                                                            |
   |                       |                       | -  **Java11**                                                                                                                                                                                                                                                                                           |
   |                       |                       | -  **Node.js6.10**                                                                                                                                                                                                                                                                                      |
   |                       |                       | -  **Node.js8.10**                                                                                                                                                                                                                                                                                      |
   |                       |                       | -  **Node.js10.16**                                                                                                                                                                                                                                                                                     |
   |                       |                       | -  **Node.js12.13**                                                                                                                                                                                                                                                                                     |
   |                       |                       | -  **Node.js14.18**                                                                                                                                                                                                                                                                                     |
   |                       |                       | -  **Node.js16.17**                                                                                                                                                                                                                                                                                     |
   |                       |                       | -  **Node.js18.15**                                                                                                                                                                                                                                                                                     |
   |                       |                       | -  **Python2.7**                                                                                                                                                                                                                                                                                        |
   |                       |                       | -  **Python3.6**                                                                                                                                                                                                                                                                                        |
   |                       |                       | -  **Python3.10**                                                                                                                                                                                                                                                                                       |
   |                       |                       | -  **Go1.x**                                                                                                                                                                                                                                                                                            |
   |                       |                       | -  **C#(.NET Core 2.1)**                                                                                                                                                                                                                                                                                |
   |                       |                       | -  **C#(.NET Core 3.1)**                                                                                                                                                                                                                                                                                |
   |                       |                       | -  **Custom**                                                                                                                                                                                                                                                                                           |
   |                       |                       | -  **PHP7.3**                                                                                                                                                                                                                                                                                           |
   |                       |                       | -  **Python3.9**                                                                                                                                                                                                                                                                                        |
   |                       |                       | -  **http**                                                                                                                                                                                                                                                                                             |
   |                       |                       | -  **Custom Image**                                                                                                                                                                                                                                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | etag                  | String                | Unique identifier of the dependency (MD5 verification value).                                                                                                                                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                  | Long                  | Dependency size.                                                                                                                                                                                                                                                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Dependency name.                                                                                                                                                                                                                                                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Dependency description.                                                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | file_name             | String                | Dependency file name.                                                                                                                                                                                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version               | Long                  | Dependency version.                                                                                                                                                                                                                                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | last_modified         | Long                  | Time when the dependency was last updated.                                                                                                                                                                                                                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dep_id                | String                | Dependency ID.                                                                                                                                                                                                                                                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | download_link         | String                | Temporary download link of a dependency file.                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_shared             | Boolean               | Whether to share the dependency version. (discarded)                                                                                                                                                                                                                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

Query dependencies of the current tenant.

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/fgs/dependencies/{depend_id}/version/{version}

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "id" : "4f4ae4eb-dcdc-4dd3-bffd-79600bd972b3",
     "owner" : "*****",
     "link" : "https://{bucket}.{obs_endpoint}/depends/****/4f4ae4eb-dcdc-4dd3-bffd-79600bd972b3.zip",
     "runtime" : "Python3.6",
     "etag" : "83863be4b6c3a86aef995dbc83aae68f",
     "size" : 577118,
     "name" : "python-kafka",
     "description" : "Python library for Kafka operations.",
     "file_name" : "python-kafka.zip",
     "version" : 0,
     "last_modified" : 1660029887
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
