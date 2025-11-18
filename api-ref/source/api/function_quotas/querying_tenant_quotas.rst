:original_name: functiongraph_06_0137.html

.. _functiongraph_06_0137:

Querying Tenant Quotas
======================

Function
--------

This API is used to query tenant quotas.

URI
---

GET /v2/{project_id}/fgs/quotas

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                         |
   +============+===========+========+=====================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
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
   | Content-Type    | Yes             | String          | Message body type (format).                                                                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+-----------------------------------------------------------------------------------+--------------------+
   | Parameter | Type                                                                              | Description        |
   +===========+===================================================================================+====================+
   | quotas    | :ref:`ListQuotasResult <functiongraph_06_0137__response_listquotasresult>` object | Quota information. |
   +-----------+-----------------------------------------------------------------------------------+--------------------+

.. _functiongraph_06_0137__response_listquotasresult:

.. table:: **Table 4** ListQuotasResult

   +-----------+-------------------------------------------------------------------------------+-------------+
   | Parameter | Type                                                                          | Description |
   +===========+===============================================================================+=============+
   | resources | Array of :ref:`Resources <functiongraph_06_0137__response_resources>` objects | Quota list. |
   +-----------+-------------------------------------------------------------------------------+-------------+

.. _functiongraph_06_0137__response_resources:

.. table:: **Table 5** Resources

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================+
   | quota                 | Integer               | Function quota.                                                                                                                                  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | used                  | Integer               | Used quota.                                                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Resource type.                                                                                                                                   |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | Enumeration values:                                                                                                                              |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | -  **fgs_func_scale_down_timeout**:Release time of idle function instances in FunctionGraph v1.                                                  |
   |                       |                       | -  **fgs_func_occurs**:Indicates instance quota for functions in FunctionGraph v1 and reserved instance quota for functions in FunctionGraph v2. |
   |                       |                       | -  **fgs_func_pat_idle_time**:Release time of idle PAT in VPC function.                                                                          |
   |                       |                       | -  **fgs_func_num**:User function quantity quota.                                                                                                |
   |                       |                       | -  **fgs_func_code_size**:Total code size quota of user functions.                                                                               |
   |                       |                       | -  **fgs_workflow_num**:Function flow quantity quota.                                                                                            |
   |                       |                       | -  **fgs_on_demand_instance_limit**:Maximum number of instances per function in FunctionGraph v2.                                                |
   |                       |                       | -  **fgs_func_qos_limit**:Instance quantity quota of user functions.                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | unit                  | String                | Resource unit. For fgs_func_code_size, the unit is MB. In other scenarios, there is no unit.                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

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

Query quotas.

.. code-block:: text

   GET /v2/{project_id}/fgs/quotas

Example Responses
-----------------

**Status code: 200**

Query successful.

.. code-block::

   {
     "quotas" : {
       "resources" : [ {
         "quota" : 60,
         "used" : 3,
         "type" : "fgs_func_scale_down_timeout"
       }, {
         "quota" : 100,
         "used" : 22,
         "type" : "fgs_func_occurs"
       }, {
         "quota" : 100,
         "used" : 22,
         "type" : "fgs_func_pat_idle_time"
       }, {
         "quota" : 100,
         "used" : 22,
         "type" : "fgs_func_num"
       }, {
         "quota" : 10240,
         "used" : 22,
         "type" : "fgs_func_code_size",
         "unit" : "MB"
       }, {
         "quota" : 512,
         "used" : 22,
         "type" : "fgs_workflow_num"
       } ]
     }
   }

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
200         Query successful.
400         Bad request.
401         Unauthorized.
403         Forbidden.
500         Internal server error.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
