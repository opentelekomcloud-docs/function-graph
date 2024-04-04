:original_name: functiongraph_06_0142.html

.. _functiongraph_06_0142:

Configuring Asynchronous Execution Notification
===============================================

Function
--------

This API is used to configure asynchronous execution notification for a function.

URI
---

PUT /v2/{project_id}/fgs/functions/{function_urn}/async-invoke-config

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

   +--------------------------------+-----------------+------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter                      | Mandatory       | Type                                                                                                 | Description                                                                                                       |
   +================================+=================+======================================================================================================+===================================================================================================================+
   | max_async_event_age_in_seconds | No              | Integer                                                                                              | Maximum validity period of a message. Value range: 1s to 86,400s. Default value: 3600s.                           |
   |                                |                 |                                                                                                      |                                                                                                                   |
   |                                |                 |                                                                                                      | Minimum: **1**                                                                                                    |
   |                                |                 |                                                                                                      |                                                                                                                   |
   |                                |                 |                                                                                                      | Maximum: **86400**                                                                                                |
   +--------------------------------+-----------------+------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | max_async_retry_attempts       | No              | Integer                                                                                              | Maximum number of retry attempts to be made if asynchronous invocation fails. Default value: 1. Value range: 0-3. |
   |                                |                 |                                                                                                      |                                                                                                                   |
   |                                |                 |                                                                                                      | Minimum: **0**                                                                                                    |
   |                                |                 |                                                                                                      |                                                                                                                   |
   |                                |                 |                                                                                                      | Maximum: **3**                                                                                                    |
   +--------------------------------+-----------------+------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | destination_config             | No              | :ref:`FuncAsyncDestinationConfig <functiongraph_06_0142__request_funcasyncdestinationconfig>` object | Asynchronous invocation target.                                                                                   |
   +--------------------------------+-----------------+------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | enable_async_status_log        | No              | Boolean                                                                                              | Whether to enable asynchronous invocation status persistence.                                                     |
   +--------------------------------+-----------------+------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+

.. _functiongraph_06_0142__request_funcasyncdestinationconfig:

.. table:: **Table 4** FuncAsyncDestinationConfig

   +------------+-----------+--------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type                                                                                       | Description                                                                                           |
   +============+===========+============================================================================================+=======================================================================================================+
   | on_success | No        | :ref:`FuncDestinationConfig <functiongraph_06_0142__request_funcdestinationconfig>` object | Target to be invoked when a function is successfully executed.                                        |
   +------------+-----------+--------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | on_failure | No        | :ref:`FuncDestinationConfig <functiongraph_06_0142__request_funcdestinationconfig>` object | Target to be invoked when a function fails to be executed due to a system error or an internal error. |
   +------------+-----------+--------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _functiongraph_06_0142__request_funcdestinationconfig:

.. table:: **Table 5** FuncDestinationConfig

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================================================================================+
   | destination     | No              | String          | Object type.                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                       |
   |                 |                 |                 | -  OBS                                                                                                                                                                                                                |
   |                 |                 |                 | -  SMN                                                                                                                                                                                                                |
   |                 |                 |                 | -  FunctionGraph                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                       |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                       |
   |                 |                 |                 | -  **OBS**                                                                                                                                                                                                            |
   |                 |                 |                 | -  **SMN**                                                                                                                                                                                                            |
   |                 |                 |                 | -  **FunctionGraph**                                                                                                                                                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | param           | No              | String          | Parameters (in JSON format) corresponding to the target service.                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                       |
   |                 |                 |                 | -  OBS: Parameters related to the bucket name, object directory prefix, and object expiration time are included. The object expiration time ranges from 0 to 365 days. If the value is 0, the object will not expire. |
   |                 |                 |                 | -  SMN: The topic_urn parameter is included.                                                                                                                                                                          |
   |                 |                 |                 | -  FunctionGraph: The func_urn parameter is included.                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 6** Response body parameters

   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter                      | Type                                                                                                  | Description                                                                                                       |
   +================================+=======================================================================================================+===================================================================================================================+
   | func_urn                       | String                                                                                                | Function URN.                                                                                                     |
   |                                |                                                                                                       |                                                                                                                   |
   |                                |                                                                                                       | Minimum: **1**                                                                                                    |
   |                                |                                                                                                       |                                                                                                                   |
   |                                |                                                                                                       | Maximum: **269**                                                                                                  |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | max_async_event_age_in_seconds | Integer                                                                                               | Maximum validity period of a message. Value range: 60-86,400. Unit: second.                                       |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | max_async_retry_attempts       | Integer                                                                                               | Maximum number of retry attempts to be made if asynchronous invocation fails. Default value: 3. Value range: 0-8. |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | destination_config             | :ref:`FuncAsyncDestinationConfig <functiongraph_06_0142__response_funcasyncdestinationconfig>` object | Asynchronous invocation target.                                                                                   |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | created_time                   | String                                                                                                | Time when asynchronous execution notification was configured.                                                     |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | last_modified                  | String                                                                                                | Time when the asynchronous execution notification settings were last modified.                                    |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | enable_async_status_log        | Boolean                                                                                               | Whether to enable asynchronous invocation status persistence.                                                     |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+

.. _functiongraph_06_0142__response_funcasyncdestinationconfig:

.. table:: **Table 7** FuncAsyncDestinationConfig

   +------------+---------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                                                        | Description                                                                                           |
   +============+=============================================================================================+=======================================================================================================+
   | on_success | :ref:`FuncDestinationConfig <functiongraph_06_0142__response_funcdestinationconfig>` object | Target to be invoked when a function is successfully executed.                                        |
   +------------+---------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | on_failure | :ref:`FuncDestinationConfig <functiongraph_06_0142__response_funcdestinationconfig>` object | Target to be invoked when a function fails to be executed due to a system error or an internal error. |
   +------------+---------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _functiongraph_06_0142__response_funcdestinationconfig:

.. table:: **Table 8** FuncDestinationConfig

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                           |
   +=======================+=======================+=======================================================================================================================================================================================================================+
   | destination           | String                | Object type.                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                       |
   |                       |                       | -  OBS                                                                                                                                                                                                                |
   |                       |                       | -  SMN                                                                                                                                                                                                                |
   |                       |                       | -  FunctionGraph                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                       |
   |                       |                       | Enumeration values:                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                       |
   |                       |                       | -  **OBS**                                                                                                                                                                                                            |
   |                       |                       | -  **SMN**                                                                                                                                                                                                            |
   |                       |                       | -  **FunctionGraph**                                                                                                                                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | param                 | String                | Parameters (in JSON format) corresponding to the target service.                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                       |
   |                       |                       | -  OBS: Parameters related to the bucket name, object directory prefix, and object expiration time are included. The object expiration time ranges from 0 to 365 days. If the value is 0, the object will not expire. |
   |                       |                       | -  SMN: The topic_urn parameter is included.                                                                                                                                                                          |
   |                       |                       | -  FunctionGraph: The func_urn parameter is included.                                                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Configure asynchronous execution notification for a function with max. validity period of 10s and max. retries of 3, and enable asynchronous invocation status persistence.

.. code-block:: text

   PUT /v2/{project_id}/fgs/functions/{function_urn}/async-invoke-config

   {
     "max_async_event_age_in_seconds" : 10,
     "max_async_retry_attempts" : 3,
     "enable_async_status_log" : true
   }

Example Responses
-----------------

**Status code: 200**

Ok

.. code-block::

   {
     "func_urn" : "urn:fss:xxxxxxxxx:7aad83af3e8d42e99ac194xxxxxxxxxx:function:default:test:latest",
     "max_async_event_age_in_seconds" : 60,
     "max_async_retry_attempts" : 1,
     "destination_config" : {
       "on_success" : {
         "destination" : "FunctionGraph",
         "param" : "{\"func_urn\":\"urn:fss:{region}:5691ba790e2b46ceb38316xxxxxxxxxx:function:default:testPython:latest\"}"
       },
       "on_failure" : {
         "destination" : "FunctionGraph",
         "param" : "{\"func_urn\":\"urn:fss:{region}:5691ba790e2b46ceb38316xxxxxxxxxx:function:default:testPython:latest\"}"
       }
     },
     "created_time" : "2021-03-04T14:50:02+08:00",
     "last_modified" : "2021-03-04 14:50:02"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         Ok
400         Bad Request
404         Not Found
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
