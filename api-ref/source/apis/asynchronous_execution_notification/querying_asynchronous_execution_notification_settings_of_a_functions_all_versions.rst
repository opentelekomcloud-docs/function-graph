:original_name: functiongraph_06_0143.html

.. _functiongraph_06_0143:

Querying Asynchronous Execution Notification Settings of a Function's All Versions
==================================================================================

Function
--------

This API is used to query the asynchronous execution notification settings of a function's all versions.

URI
---

GET /v2/{project_id}/fgs/functions/{function_urn}/async-invoke-configs

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                         |
   +==============+===========+========+=====================================================================================+
   | project_id   | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+
   | function_urn | Yes       | String | Function URN. For details, see the function model description.                      |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================================================================+
   | marker          | No              | String          | Final record queried last time.                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                              |
   |                 |                 |                 | Maximum: **64**                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String          | Number of items displayed on each page.                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                              |
   |                 |                 |                 | -  If this parameter is not specified or is set to 0, the default value 10 is used. The maximum value is 100. If you set this parameter to a value greater than 100, the value automatically changes to 100. |
   |                 |                 |                 | -  If it is less than 0, an error is reported.                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                              |
   |                 |                 |                 | Default: **10**                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter             | Type                                                                                                                              | Description                                   |
   +=======================+===================================================================================================================================+===============================================+
   | async_invoke_configs  | Array of :ref:`ListFunctionAsyncInvokeConfigResult <functiongraph_06_0143__response_listfunctionasyncinvokeconfigresult>` objects | Asynchronous execution notification settings. |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | count                 | Long                                                                                                                              | Total number of items.                        |
   |                       |                                                                                                                                   |                                               |
   |                       |                                                                                                                                   | Minimum: **0**                                |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | page_info             | :ref:`PageInfo <functiongraph_06_0143__response_pageinfo>` object                                                                 |                                               |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _functiongraph_06_0143__response_listfunctionasyncinvokeconfigresult:

.. table:: **Table 5** ListFunctionAsyncInvokeConfigResult

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
   | destination_config             | :ref:`FuncAsyncDestinationConfig <functiongraph_06_0143__response_funcasyncdestinationconfig>` object | Asynchronous invocation target.                                                                                   |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | created_time                   | String                                                                                                | Time when asynchronous execution notification was configured.                                                     |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | last_modified                  | String                                                                                                | Time when the asynchronous execution notification settings were last modified.                                    |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | enable_async_status_log        | Boolean                                                                                               | Whether to enable asynchronous invocation status persistence.                                                     |
   +--------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+

.. _functiongraph_06_0143__response_funcasyncdestinationconfig:

.. table:: **Table 6** FuncAsyncDestinationConfig

   +------------+---------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                                                        | Description                                                                                           |
   +============+=============================================================================================+=======================================================================================================+
   | on_success | :ref:`FuncDestinationConfig <functiongraph_06_0143__response_funcdestinationconfig>` object | Target to be invoked when a function is successfully executed.                                        |
   +------------+---------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | on_failure | :ref:`FuncDestinationConfig <functiongraph_06_0143__response_funcdestinationconfig>` object | Target to be invoked when a function fails to be executed due to a system error or an internal error. |
   +------------+---------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _functiongraph_06_0143__response_funcdestinationconfig:

.. table:: **Table 7** FuncDestinationConfig

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

.. _functiongraph_06_0143__response_pageinfo:

.. table:: **Table 8** PageInfo

   =============== ==== ====================================
   Parameter       Type Description
   =============== ==== ====================================
   next_marker     Long Next read location.
   previous_marker Long Previous read location.
   current_count   Long Number of items on the current page.
   =============== ==== ====================================

Example Requests
----------------

Query the asynchronous execution notification settings of a function's all versions.

.. code-block:: text

   GET /v2/{project_id}/fgs/functions/{function_urn}/async-invoke-configs

Example Responses
-----------------

**Status code: 200**

Ok

.. code-block::

   {
     "async_invoke_configs" : [ {
       "func_urn" : "urn:fss:{region}:5691ba790e2b46ceb38316xxxxxxxxxx:function:default:test_async:latest",
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
     } ],
     "count" : 2,
     "page_info" : {
       "next_marker" : 2,
       "previous_marker" : 0,
       "current_count" : 2
     }
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         Ok
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
