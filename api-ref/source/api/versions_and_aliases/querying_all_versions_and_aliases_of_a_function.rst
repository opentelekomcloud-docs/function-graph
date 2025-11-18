:original_name: functiongraph_06_0118.html

.. _functiongraph_06_0118:

Querying All Versions and Aliases of a Function
===============================================

Function
--------

This API is used to query the versions and aliases of a function.

URI
---

GET /v2/{project_id}/fgs/functions/{function_urn}/aliases

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

   +-----------+---------------------------------------------------------------------------------------------------------+--------------------------------+
   | Parameter | Type                                                                                                    | Description                    |
   +===========+=========================================================================================================+================================+
   | [items]   | Array of :ref:`ListVersionAliasResult <functiongraph_06_0118__response_listversionaliasresult>` objects | Function versions and aliases. |
   +-----------+---------------------------------------------------------------------------------------------------------+--------------------------------+

.. _functiongraph_06_0118__response_listversionaliasresult:

.. table:: **Table 4** ListVersionAliasResult

   +----------------------------+---------------------+----------------------------------------+
   | Parameter                  | Type                | Description                            |
   +============================+=====================+========================================+
   | name                       | String              | Alias to be queried.                   |
   +----------------------------+---------------------+----------------------------------------+
   | version                    | String              | Version corresponding to the alias.    |
   +----------------------------+---------------------+----------------------------------------+
   | description                | String              | Description of the alias.              |
   +----------------------------+---------------------+----------------------------------------+
   | last_modified              | String              | Time when the alias was last modified. |
   +----------------------------+---------------------+----------------------------------------+
   | alias_urn                  | String              | URN of the alias.                      |
   +----------------------------+---------------------+----------------------------------------+
   | additional_version_weights | Map<String,Integer> | Dark launch information.               |
   +----------------------------+---------------------+----------------------------------------+

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

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

**Status code: 503**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Query aliases of a function.

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/fgs/functions/{function_urn}/aliases

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   [ {
     "name" : "a1",
     "version" : "latest",
     "description" : "",
     "last_modified" : "2019-10-31 11:37:58",
     "alias_urn" : "urn:fss:{region}:46b6f338fc3445b8846c71dfb1fbxxxx:function:default:xxxxx:!a1",
     "additional_version_weights" : {
       "v1" : 10
     }
   } ]

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
503         Service unavailable.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
