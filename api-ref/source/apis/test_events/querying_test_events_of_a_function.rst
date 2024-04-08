:original_name: functiongraph_06_0132.html

.. _functiongraph_06_0132:

Querying Test Events of a Function
==================================

Function
--------

This API is used to query the test events of a function.

URI
---

GET /v2/{project_id}/fgs/functions/{function_urn}/events

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

   +-------------+---------------------------------------------------------------------------------------------+------------------------------+
   | Parameter   | Type                                                                                        | Description                  |
   +=============+=============================================================================================+==============================+
   | count       | Integer                                                                                     | Total number of test events. |
   +-------------+---------------------------------------------------------------------------------------------+------------------------------+
   | events      | Array of :ref:`ListEventsResult <functiongraph_06_0132__response_listeventsresult>` objects | Test event list.             |
   +-------------+---------------------------------------------------------------------------------------------+------------------------------+
   | next_marker | Long                                                                                        | Next read location.          |
   +-------------+---------------------------------------------------------------------------------------------+------------------------------+

.. _functiongraph_06_0132__response_listeventsresult:

.. table:: **Table 4** ListEventsResult

   ============= ====== =================
   Parameter     Type   Description
   ============= ====== =================
   id            String Test event ID.
   last_modified Number Last update time.
   name          String Test event name.
   ============= ====== =================

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

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

Query the test event list.

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/fgs/functions/{function_urn}/events

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "events" : [ {
       "id" : "3b659dc0-12fc-40dc-aa05-a321d9424cb3",
       "name" : "event-k9r3",
       "last_modified" : 1597374286
     } ],
     "next_marker" : 1,
     "count" : 1
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
