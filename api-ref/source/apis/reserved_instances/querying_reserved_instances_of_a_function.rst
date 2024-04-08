:original_name: functiongraph_06_0112_2.html

.. _functiongraph_06_0112_2:

Querying Reserved Instances of a Function
=========================================

Function
--------

This API is used to query reserved instances of a function.

URI
---

GET /v2/{project_id}/fgs/functions/reservedinstanceconfigs

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                         |
   +============+===========+========+=====================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                    |
   +=================+=================+=================+================================================================================+
   | function_urn    | No              | String          | Function URN. For details, see the function model descriptions.                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+
   | marker          | No              | String          | Start position of the current query. The default value is 0.                   |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | Default: **0**                                                                 |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | Minimum: **1**                                                                 |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | Maximum: **64**                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+
   | limit           | No              | String          | Maximum number of data records returned in a request. Max.: 500. Default: 100. |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | Default: **100**                                                               |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | Minimum: **1**                                                                 |
   |                 |                 |                 |                                                                                |
   |                 |                 |                 | Maximum: **64**                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+

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

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +--------------------+-------------------------------------------------------------------------------------------------------------+----------------------+
   | Parameter          | Type                                                                                                        | Description          |
   +====================+=============================================================================================================+======================+
   | reserved_instances | Array of :ref:`ReservedInstanceConfigs <functiongraph_06_0112_2__response_reservedinstanceconfigs>` objects | Reserved instances.  |
   +--------------------+-------------------------------------------------------------------------------------------------------------+----------------------+
   | page_info          | :ref:`PageInfo <functiongraph_06_0112_2__response_pageinfo>` object                                         |                      |
   +--------------------+-------------------------------------------------------------------------------------------------------------+----------------------+
   | count              | Long                                                                                                        | Number of functions. |
   +--------------------+-------------------------------------------------------------------------------------------------------------+----------------------+

.. _functiongraph_06_0112_2__response_reservedinstanceconfigs:

.. table:: **Table 5** ReservedInstanceConfigs

   +----------------+-------------------------------------------------------------------------------+--------------------------------------------+
   | Parameter      | Type                                                                          | Description                                |
   +================+===============================================================================+============================================+
   | function_urn   | String                                                                        | Function URN.                              |
   +----------------+-------------------------------------------------------------------------------+--------------------------------------------+
   | qualifier_type | String                                                                        | Limiting type. Options: version and alias. |
   +----------------+-------------------------------------------------------------------------------+--------------------------------------------+
   | qualifier_name | String                                                                        | Limit value.                               |
   +----------------+-------------------------------------------------------------------------------+--------------------------------------------+
   | min_count      | Integer                                                                       | Number of reserved instances.              |
   +----------------+-------------------------------------------------------------------------------+--------------------------------------------+
   | idle_mode      | Boolean                                                                       | Whether to enable the idle mode.           |
   +----------------+-------------------------------------------------------------------------------+--------------------------------------------+
   | tactics_config | :ref:`TacticsConfig <functiongraph_06_0112_2__response_tacticsconfig>` object |                                            |
   +----------------+-------------------------------------------------------------------------------+--------------------------------------------+

.. _functiongraph_06_0112_2__response_tacticsconfig:

.. table:: **Table 6** TacticsConfig

   +--------------+-----------------------------------------------------------------------------------+-------------------------------+
   | Parameter    | Type                                                                              | Description                   |
   +==============+===================================================================================+===============================+
   | cron_configs | Array of :ref:`CronConfig <functiongraph_06_0112_2__response_cronconfig>` objects | Scheduled configuration list. |
   +--------------+-----------------------------------------------------------------------------------+-------------------------------+

.. _functiongraph_06_0112_2__response_cronconfig:

.. table:: **Table 7** CronConfig

   ============ ======= =====================================
   Parameter    Type    Description
   ============ ======= =====================================
   name         String  Scheduled configuration name.
   cron         String  Cron expression.
   count        Integer Number of started reserved instances.
   start_time   Long    Start time (epoch format).
   expired_time Long    Expiry time (epoch format).
   ============ ======= =====================================

.. table:: **Table 8** MetricConfig

   +-----------------------+-----------------------+--------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                    |
   +=======================+=======================+================================================================================+
   | name                  | String                | Flow control configuration name.                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------+
   | type                  | String                | Flow control type. Currently, only reserved instance utilization is supported. |
   |                       |                       |                                                                                |
   |                       |                       | Enumeration values:                                                            |
   |                       |                       |                                                                                |
   |                       |                       | -  **Concurrency**                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------+
   | threshold             | Integer               | Flow control threshold.                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------+
   | min                   | Integer               | Minimum value.                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------+

.. _functiongraph_06_0112_2__response_pageinfo:

.. table:: **Table 9** PageInfo

   =============== ==== ====================================
   Parameter       Type Description
   =============== ==== ====================================
   next_marker     Long Next read location.
   previous_marker Long Previous read location.
   current_count   Long Number of items on the current page.
   =============== ==== ====================================

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

Query reserved instances of a function.

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/fgs/functions/reservedinstanceconfigs

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
       "reserved_instances": [
           {
               "function_urn": "urn:fss:{region}:46b6f338fc3445b8846c71dfb1fbxxxx:function:default:xxxxx:latest",
               "qualifier_type": "version",
               "qualifier_name": "latest",
               "min_count": 10,
               "idle_mode": false,
               "tactics_config": {
                   "cron_configs": [
                       {
                           "name": "cronConfig",
                           "cron": "0 1 * * * *",
                           "count": 15,
                           "start_time": 1658073600,
                           "expired_time": 1658160000
                       }
                   ]
               }
           }
       ],
       "page_info": {
           "next_marker": 1,
           "previous_marker": 0,
           "current_count": 1
       },
       "count": 1
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
