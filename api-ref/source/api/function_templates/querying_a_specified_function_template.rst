:original_name: functiongraph_23_1031_06.html

.. _functiongraph_23_1031_06:

Querying a Specified Function Template
======================================

Function
--------

This API is used to query a specified function template.

URI
---

GET /v2/{project_id}/fgs/templates/{template_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                         |
   +=============+===========+========+=====================================================================================+
   | project_id  | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------+
   | template_id | Yes       | String | Template ID.                                                                        |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------+

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

   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                 | Description                                                              |
   +=======================+======================================================================================================+==========================================================================+
   | id                    | String                                                                                               | Template ID.                                                             |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | type                  | Integer                                                                                              | Template type.                                                           |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | title                 | String                                                                                               | Template title.                                                          |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | template_name         | String                                                                                               | Template name.                                                           |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | description           | String                                                                                               | Template description.                                                    |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | runtime               | String                                                                                               | Template runtime.                                                        |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | handler               | String                                                                                               | Template handler.                                                        |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | code_type             | String                                                                                               | Code type.                                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | code                  | String                                                                                               | Code file.                                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | timeout               | Integer                                                                                              | Maximum duration the function can be executed. Value range: 3s-259,200s. |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | memory_size           | Integer                                                                                              | Memory size.                                                             |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | trigger_metadata_list | Array of :ref:`TriggerMetadataList <functiongraph_23_1031_06__response_triggermetadatalist>` objects | Trigger information.                                                     |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | temp_detail           | :ref:`TempDetail <functiongraph_23_1031_06__response_tempdetail>` object                             |                                                                          |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | user_data             | String                                                                                               | User data.                                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | encrypted_user_data   | String                                                                                               | Encrypted user data.                                                     |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | dependencies          | Array of strings                                                                                     | Dependencies required by the template.                                   |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | scene                 | String                                                                                               | Template application scenarios.                                          |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | service               | String                                                                                               | Cloud service associated with the template.                              |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+

.. _functiongraph_23_1031_06__response_triggermetadatalist:

.. table:: **Table 4** TriggerMetadataList

   ============ ====== =============
   Parameter    Type   Description
   ============ ====== =============
   trigger_name String Trigger name.
   trigger_type String Trigger type.
   event_type   String Event type.
   event_data   String Event data.
   ============ ====== =============

.. _functiongraph_23_1031_06__response_tempdetail:

.. table:: **Table 5** TempDetail

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   input     String Template input.
   output    String Template output.
   warning   String Warning.
   ========= ====== ================

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

**Status code: 404**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Query a specified function template.

.. code-block:: text

   GET /v2/{project_id}/fgs/templates/{template_id}

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "id" : "d3aa6e4c-xxxx-xxxx-9c09-5c50c4xxxxxx",
     "type" : 1,
     "title" : "access-service-with-http",
     "template_name" : "access-service-with-http-php",
     "description" : "access service with http.",
     "runtime" : "PHP7.3",
     "handler" : "index.handler",
     "code_type" : "inline",
     "code" : "xxxxx",
     "timeout" : 30,
     "memory_size" : 256,
     "trigger_metadata_list" : [ ],
     "temp_detail" : {
       "input" : "None",
       "output" : "execution succeed: Return to access service information through http/https,",
       "warning" : "1. configure the serveraddress environment variables."
     },
     "user_data" : "",
     "encrypted_user_data" : "",
     "dependencies" : [ ],
     "scene" : "basic_function_usage",
     "service" : "FunctionGraph"
   }

**Status code: 404**

Not found.

.. code-block::

   {
     "error_code" : "FSS.1059",
     "error_msg" : "The function template does not exist."
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
