:original_name: functiongraph_06_0114.html

.. _functiongraph_06_0114:

Creating an Alias for a Function Version
========================================

Function
--------

This API is used to create an alias for a function version.

URI
---

POST /v2/{project_id}/fgs/functions/{function_urn}/aliases

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

   +-----------------------------+-----------------+---------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter                   | Mandatory       | Type                                                                                  | Description                                                                                                              |
   +=============================+=================+=======================================================================================+==========================================================================================================================+
   | name                        | Yes             | String                                                                                | Alias.Max. 64 of letters, digits, hyphens (-), and underscores (_). Start with a letter, and end with a letter or digit. |
   |                             |                 |                                                                                       |                                                                                                                          |
   |                             |                 |                                                                                       | Minimum length: 1 character.                                                                                             |
   |                             |                 |                                                                                       |                                                                                                                          |
   |                             |                 |                                                                                       | Maximum length: 64 characters.                                                                                           |
   +-----------------------------+-----------------+---------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | version                     | Yes             | String                                                                                | Version corresponding to the alias.                                                                                      |
   +-----------------------------+-----------------+---------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | description                 | No              | String                                                                                | Description of the alias.                                                                                                |
   +-----------------------------+-----------------+---------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | additional_version_weights  | No              | Map<String,Integer>                                                                   | Traffic shifting by percentage.                                                                                          |
   +-----------------------------+-----------------+---------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | additional_version_strategy | No              | Map<String,\ :ref:`VersionStrategy <functiongraph_06_0114__request_versionstrategy>`> | Traffic shifting by rule.                                                                                                |
   +-----------------------------+-----------------+---------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+

.. _functiongraph_06_0114__request_versionstrategy:

.. table:: **Table 4** VersionStrategy

   +-----------------+-----------------+----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                               | Description                                                         |
   +=================+=================+====================================================================================================+=====================================================================+
   | rules           | No              | Array of :ref:`VersionStrategyRules <functiongraph_06_0114__request_versionstrategyrules>` objects | Rules.                                                              |
   +-----------------+-----------------+----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | combine_type    | No              | String                                                                                             | Rule aggregation mode. and: All rules are met. or: Any rule is met. |
   |                 |                 |                                                                                                    |                                                                     |
   |                 |                 |                                                                                                    | Enumeration values:                                                 |
   |                 |                 |                                                                                                    |                                                                     |
   |                 |                 |                                                                                                    | -  **and**                                                          |
   |                 |                 |                                                                                                    | -  **or**                                                           |
   +-----------------+-----------------+----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+

.. _functiongraph_06_0114__request_versionstrategyrules:

.. table:: **Table 5** VersionStrategyRules

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                          |
   +=================+=================+=================+======================================================================================================+
   | rule_type       | No              | String          | Parameter type.                                                                                      |
   |                 |                 |                 |                                                                                                      |
   |                 |                 |                 | Enumeration values:                                                                                  |
   |                 |                 |                 |                                                                                                      |
   |                 |                 |                 | -  **Header**                                                                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | param           | No              | String          | Rule parameter name, which can contain only letters, digits, underscores (_), and hyphens (-).       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | op              | No              | String          | Rule matching operator. Currently, only = and in are supported.                                      |
   |                 |                 |                 |                                                                                                      |
   |                 |                 |                 | Enumeration values:                                                                                  |
   |                 |                 |                 |                                                                                                      |
   |                 |                 |                 | -  **in**                                                                                            |
   |                 |                 |                 | -  **=**                                                                                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Rule value. If op is set to in, the value is a multi-value character string separated by commas (,). |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 6** Response body parameters

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
   | additional_version_strategy | Map<String,\ :ref:`VersionStrategy <functiongraph_06_0114__response_versionstrategy>`> | Traffic shifting by rule.              |
   +-----------------------------+----------------------------------------------------------------------------------------+----------------------------------------+

.. _functiongraph_06_0114__response_versionstrategy:

.. table:: **Table 7** VersionStrategy

   +-----------------------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | Parameter             | Type                                                                                                | Description                                                         |
   +=======================+=====================================================================================================+=====================================================================+
   | rules                 | Array of :ref:`VersionStrategyRules <functiongraph_06_0114__response_versionstrategyrules>` objects | Rules.                                                              |
   +-----------------------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | combine_type          | String                                                                                              | Rule aggregation mode. and: All rules are met. or: Any rule is met. |
   |                       |                                                                                                     |                                                                     |
   |                       |                                                                                                     | Enumeration values:                                                 |
   |                       |                                                                                                     |                                                                     |
   |                       |                                                                                                     | -  **and**                                                          |
   |                       |                                                                                                     | -  **or**                                                           |
   +-----------------------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+

.. _functiongraph_06_0114__response_versionstrategyrules:

.. table:: **Table 8** VersionStrategyRules

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                          |
   +=======================+=======================+======================================================================================================+
   | rule_type             | String                | Parameter type.                                                                                      |
   |                       |                       |                                                                                                      |
   |                       |                       | Enumeration values:                                                                                  |
   |                       |                       |                                                                                                      |
   |                       |                       | -  **Header**                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | param                 | String                | Rule parameter name, which can contain only letters, digits, underscores (_), and hyphens (-).       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | op                    | String                | Rule matching operator. Currently, only = and in are supported.                                      |
   |                       |                       |                                                                                                      |
   |                       |                       | Enumeration values:                                                                                  |
   |                       |                       |                                                                                                      |
   |                       |                       | -  **in**                                                                                            |
   |                       |                       | -  **=**                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | value                 | String                | Rule value. If op is set to in, the value is a multi-value character string separated by commas (,). |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 12** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 13** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

-  Create an alias named a1 for version v1 of a function.

   .. code-block:: text

      POST https://{Endpoint}/v2/{project_id}/fgs/functions/{function_urn}/aliases

      {
        "name" : "a1",
        "version" : "v1"
      }

-  Create an alias named a1 for version v1 of a function, enable Traffic Shifting, and set Weight of version v2 to 50%.

   .. code-block:: text

      POST https://{Endpoint}/v2/{project_id}/fgs/functions/{function_urn}/aliases

      {
        "name" : "a1",
        "version" : "v1",
        "additional_version_weights" : {
          "v2" : 50
        }
      }

-  Create an alias named a1 for version v1 of a function, enable Traffic Shifting, and set version v2 to shift traffic by Rule.

   .. code-block:: text

      POST https://{Endpoint}/v2/{project_id}/fgs/functions/{function_urn}/aliases

      {
        "name" : "a1",
        "version" : "v1",
        "additional_version_strategy" : {
          "v2" : {
            "combine_type" : "and",
            "rules" : [ {
              "rule_type" : "Header",
              "param" : "version",
              "op" : "=",
              "value" : "v1"
            } ]
          }
        }
      }

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "name" : "a1",
     "version" : "latest",
     "description" : "",
     "last_modified" : "2019-10-31 11:37:58",
     "alias_urn" : "urn:fss:{region}:46b6f338fc3445b8846c71dfb1fbxxxx:function:default:xxxxx:!a1"
   }

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
400         Bad request.
401         Unauthorized.
403         Forbidden.
404         Not found.
500         Internal server error.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
