:original_name: functiongraph_06_0112_3.html

.. _functiongraph_06_0112_3:

Querying the Number of Reserved Instances
=========================================

Function
--------

This API is used to query the number of instances reserved for a function.

URI
---

GET /v2/{project_id}/fgs/functions/reservedinstances

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                         |
   +============+===========+========+=====================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <functiongraph_06_0260>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                               |
   +=================+=================+=================+===========================================================================================================+
   | marker          | No              | String          | Final record queried last time.                                                                           |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | Default: **0**                                                                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | limit           | No              | String          | Maximum number of functions to obtain in a request.                                                       |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | Maximum value: 400                                                                                        |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | The default value is 400, which is used when this parameter is not specified or is 0 or greater than 400. |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | If it is less than 0, an error is reported.                                                               |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | Default: **400**                                                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | urn             | No              | String          | URN of a function whose number of reserved instances is to be queried.                                    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+

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

   +-------------------+-------------------------------------------------------------------------------------------------------+----------------------+
   | Parameter         | Type                                                                                                  | Description          |
   +===================+=======================================================================================================+======================+
   | reservedinstances | Array of :ref:`FuncReservedInstance <functiongraph_06_0112_3__response_funcreservedinstance>` objects | Reserved instances.  |
   +-------------------+-------------------------------------------------------------------------------------------------------+----------------------+
   | page_info         | :ref:`PageInfo <functiongraph_06_0112_3__response_pageinfo>` object                                   |                      |
   +-------------------+-------------------------------------------------------------------------------------------------------+----------------------+
   | count             | Long                                                                                                  | Number of functions. |
   +-------------------+-------------------------------------------------------------------------------------------------------+----------------------+

.. _functiongraph_06_0112_3__response_funcreservedinstance:

.. table:: **Table 5** FuncReservedInstance

   ========= ====== =============================
   Parameter Type   Description
   ========= ====== =============================
   func_urn  String Function URN.
   count     Long   Number of reserved instances.
   ========= ====== =============================

.. _functiongraph_06_0112_3__response_pageinfo:

.. table:: **Table 6** PageInfo

   =============== ==== ====================================
   Parameter       Type Description
   =============== ==== ====================================
   next_marker     Long Next read location.
   previous_marker Long Previous read location.
   current_count   Long Number of items on the current page.
   =============== ==== ====================================

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

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

**Status code: 500**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Query reserved instances.

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/fgs/functions/reservedinstances

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "reservedinstances" : [ {
       "func_urn" : "urn:fss:xxxxx:46b6f338fc3445b8846c71dfb1fbxxxx:function:csharp:test2-0:latest",
       "count" : 2
     } ],
     "page_info" : {
       "next_marker" : 2,
       "previous_marker" : 0,
       "current_count" : 2
     }
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
