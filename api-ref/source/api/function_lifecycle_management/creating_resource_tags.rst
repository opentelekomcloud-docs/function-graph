:original_name: functiongraph_06_1023.html

.. _functiongraph_06_1023:

Creating Resource Tags
======================

Function
--------

This API is used to create resource tags.

URI
---

POST /v2/{project_id}/{resource_type}/{resource_id}/tags/create

.. table:: **Table 1** Path Parameters

   +---------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                         |
   +===============+===========+========+=====================================================================================+
   | project_id    | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------+
   | resource_type | Yes       | String | Resource type. Enter functions here.                                                |
   +---------------+-----------+--------+-------------------------------------------------------------------------------------+
   | resource_id   | Yes       | String | Resource ID.                                                                        |
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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------------------------------------------------------------+---------------------+
   | Parameter       | Mandatory       | Type                                                                   | Description         |
   +=================+=================+========================================================================+=====================+
   | action          | No              | String                                                                 | Action name.        |
   |                 |                 |                                                                        |                     |
   |                 |                 |                                                                        | Enumeration values: |
   |                 |                 |                                                                        |                     |
   |                 |                 |                                                                        | -  **create**       |
   |                 |                 |                                                                        |                     |
   |                 |                 |                                                                        | -  **delete**       |
   +-----------------+-----------------+------------------------------------------------------------------------+---------------------+
   | tags            | No              | Array of :ref:`KvItem <functiongraph_06_1023__request_kvitem>` objects | Tag list.           |
   +-----------------+-----------------+------------------------------------------------------------------------+---------------------+
   | sys_tags        | No              | Array of :ref:`KvItem <functiongraph_06_1023__request_kvitem>` objects | System tags.        |
   +-----------------+-----------------+------------------------------------------------------------------------+---------------------+

.. _functiongraph_06_1023__request_kvitem:

.. table:: **Table 4** KvItem

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   key       No        String Key.
   value     No        String Value.
   ========= ========= ====== ===========

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Create resource tags testKey1:testValue1 and testKey2:testValue2.

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/{resource_type}/{resource_id}/tags/create

   {
     "tags" : [ {
       "key" : "testKey1",
       "value" : "testValue1"
     }, {
       "key" : "testKey2",
       "value" : "testValue2"
     } ],
     "action" : "create"
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ============
Status Code Description
=========== ============
204         No Content
400         Bad request.
=========== ============

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
