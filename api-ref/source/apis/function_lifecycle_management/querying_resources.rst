:original_name: functiongraph_06_1021.html

.. _functiongraph_06_1021:

Querying Resources
==================

Function
--------

This API is used to query resources.

URI
---

POST /v2/{project_id}/{resource_type}/resource-instances/{action}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                         |
   +=================+=================+=================+=====================================================================================+
   | project_id      | Yes             | String          | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
   | resource_type   | Yes             | String          | Resource type. Enter functions here.                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
   | action          | Yes             | String          | Filter or count.                                                                    |
   |                 |                 |                 |                                                                                     |
   |                 |                 |                 | Enumeration values:                                                                 |
   |                 |                 |                 |                                                                                     |
   |                 |                 |                 | -  **filter**                                                                       |
   |                 |                 |                 |                                                                                     |
   |                 |                 |                 | -  **count**                                                                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------+

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

   +-----------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                     | Description                               |
   +=================+=================+==========================================================================+===========================================+
   | without_any_tag | No              | Boolean                                                                  | Whether to use tag-based filtering.       |
   +-----------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------+
   | limit           | No              | String                                                                   | Number of records displayed on each page. |
   +-----------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------+
   | offset          | No              | String                                                                   | Query offset.                             |
   +-----------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------+
   | action          | No              | String                                                                   | Query an action.                          |
   |                 |                 |                                                                          |                                           |
   |                 |                 |                                                                          | Enumeration values:                       |
   |                 |                 |                                                                          |                                           |
   |                 |                 |                                                                          | -  **count**                              |
   |                 |                 |                                                                          |                                           |
   |                 |                 |                                                                          | -  **filter**                             |
   +-----------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------+
   | matches         | No              | Array of :ref:`KvItem <functiongraph_06_1021__request_kvitem>` objects   | Query a key-value pair.                   |
   +-----------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------+
   | sys_tags        | No              | Array of :ref:`TagItem <functiongraph_06_1021__request_tagitem>` objects | Query system tags.                        |
   +-----------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------+

.. _functiongraph_06_1021__request_kvitem:

.. table:: **Table 4** KvItem

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   key       No        String Key.
   value     No        String Value.
   ========= ========= ====== ===========

.. _functiongraph_06_1021__request_tagitem:

.. table:: **Table 5** TagItem

   ========= ========= ================ ===========
   Parameter Mandatory Type             Description
   ========= ========= ================ ===========
   key       No        String           Key.
   values    No        Array of strings Value.
   ========= ========= ================ ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 6** Response body parameters

   +-------------+---------------------------------------------------------------------------------------------------------------------+----------------------+
   | Parameter   | Type                                                                                                                | Description          |
   +=============+=====================================================================================================================+======================+
   | resources   | Array of :ref:`ListEnterpriseResourceResult <functiongraph_06_1021__response_listenterpriseresourceresult>` objects | Enterprise projects. |
   +-------------+---------------------------------------------------------------------------------------------------------------------+----------------------+
   | total_count | Long                                                                                                                | Number of resources. |
   +-------------+---------------------------------------------------------------------------------------------------------------------+----------------------+

.. _functiongraph_06_1021__response_listenterpriseresourceresult:

.. table:: **Table 7** ListEnterpriseResourceResult

   +-----------------+-----------------------------------------------------------------------------------------------------------+----------------+
   | Parameter       | Type                                                                                                      | Description    |
   +=================+===========================================================================================================+================+
   | resource_id     | String                                                                                                    | Resource ID.   |
   +-----------------+-----------------------------------------------------------------------------------------------------------+----------------+
   | resource_detail | :ref:`ListEnterpriseResourceDetail <functiongraph_06_1021__response_listenterpriseresourcedetail>` object |                |
   +-----------------+-----------------------------------------------------------------------------------------------------------+----------------+
   | tags            | Array of :ref:`KvItem <functiongraph_06_1021__response_kvitem>` objects                                   | Tag list.      |
   +-----------------+-----------------------------------------------------------------------------------------------------------+----------------+
   | sys_tags        | Array of :ref:`KvItem <functiongraph_06_1021__response_kvitem>` objects                                   | System tags.   |
   +-----------------+-----------------------------------------------------------------------------------------------------------+----------------+
   | resource_name   | String                                                                                                    | Resource name. |
   +-----------------+-----------------------------------------------------------------------------------------------------------+----------------+

.. _functiongraph_06_1021__response_listenterpriseresourcedetail:

.. table:: **Table 8** ListEnterpriseResourceDetail

   ========= ====== =============
   Parameter Type   Description
   ========= ====== =============
   detailId  String Function URN.
   ========= ====== =============

.. _functiongraph_06_1021__response_kvitem:

.. table:: **Table 9** KvItem

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   key       String Key.
   value     String Value.
   ========= ====== ===========

**Status code: 400**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 12** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 13** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 14** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Query resources.

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/{resource_type}/resource-instances/{action}

   {
     "without_any_tag" : true,
     "limit" : 5,
     "matches" : [ {
       "key" : "resource_name",
       "value" : "test_function"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

ok

-  Example 1

   .. code-block::

      {
        "resources" : [ {
          "resource_id" : "34e4516e-e324-412b-914e-c4e568c7d813",
          "resource_detail" : {
            "detailId" : "urn:fss:{region-id}:xxxx:function:default:test_xxx:latest"
          },
          "tags" : [ ],
          "sys_tags" : [ {
            "key" : "_sys_enterprise_project_id",
            "value" : "df5edab8-c458-4a4c-b87b-a4d3b0a757ce"
          } ],
          "resource_name" : "test_v2_1"
        } ]
      }

-  Example 2

   .. code-block::

      1

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
