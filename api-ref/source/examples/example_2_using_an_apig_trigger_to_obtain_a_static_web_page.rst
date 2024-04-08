:original_name: functiongraph_06_0203.html

.. _functiongraph_06_0203:

Example 2: Using an APIG Trigger to Obtain a Static Web Page
============================================================

Scenario
--------

This example guides you through the procedure for creating a Python 2.7 function and associating an APIG trigger with it to obtain a static web page.

For details about how to call APIs, see :ref:`Calling APIs <functiongraph_06_0200>`.

Prerequisites
-------------

You have created an API group in APIG, and have recorded the ID and subdomain name of the API group.

General Procedure
-----------------

Create a FunctionGraph function and associate an APIG trigger with it to obtain a static web page. The procedure is as follows:

#. :ref:`Creating a Function <functiongraph_06_0108>`: Create a function to return a static web page.
#. :ref:`Creating a Trigger <functiongraph_06_0122>`: Create an APIG trigger.
#. Call the API of the APIG trigger to obtain a static page.

.. _functiongraph_06_0203__section5121646125111:

Step 1: Create a Function to Return a Static Web Page
-----------------------------------------------------

URI: **POST /v2/**\ *{project_id}*\ **/fgs/functions**

For details, see :ref:`Creating a Function <functiongraph_06_0108>`.

-  Sample request

   .. code-block:: text

      POST  https://{Endpoint}/v2/{project_id}/fgs/functions
      {
       "code_filename": "index.zip",
       "code_type": "inline",
       "func_code": {
        "file": "UEsDBAoAAAAIABY7vFD7lxPkAgMAALoHAAAIAAAAaW5kZXgucHndVdtu00AQfc9XrMKDExQ7zqW50VYqFZRKIFUQhFBVobU9iU1tr9mdbRKqSHwNH8aXMLtxrgoS8ISIosg7c+bszNnjzRPmPnVZKKIkn440TtyBCVQcx6mMY2ATkaZiRjmWKMZzdnFzfcXgAXJkYsI4UzwrUoLpPMRE5B77KDQLCYigkGFMVescCxZMQQq0IDokcl4kruVyEYiGI5TU66VXqTxWGKvGiMUbwFhE1RGrXr0YVxsmXHCMTaBpNmvGQK1uEzdc8gwQpCKIYTFxKeYLU7HCUnBp8V80yMU7lNTYsbKcIqaKfjclMfBoDzR3FfKpxZl2bCMUfiXomWIz7GU5tNXw3oM5hBrBpfE9rdwZod22xzP+VeR8prxQZOvq9wqkezElTQxHqrkrCb1wjSBN32v5rPZa8zrLp/NPlG22fN8fbJsMRGTH/fHtO31X2kigaRVeihxhjtv+j3Zfgq+t7lHU7XT6nV479NthP+r328Mh9Af9QSuAoBu01kU016qg2wq6J8A7bt8PTtxWC3pu0A8itzcMTjiHgEiGZbNL67gkK4QkZ6n102cl8vVzwBX0upVKBBMW8zxKQdasXRpkXztMfWQbKOgckTl02CEoxcoZ2ESKzFiOvCeT6RSkU7FwlItVnfmQvIXIFYwXBbCzlR1vnaP+cO5unV24c2dZYB5Cgb9kdKh9rlMsN08mBwBCxJilzpbALN+WGCJ43CTMx6FjQ60uRQTOiLV9v7GfTtRzK9uLnF5xiAgzlhoOQKWXndEBuT1NaxTzilJ7K3vM6V2jnp6xMOZSAZ7Za6O6V7o82MI4kfhXZ+gFvS7YhmrOqaE6P41b5x8gJecDQ8E0TfqyvDauJC/i0yYBTu225059y73ckRm1zK1hvEhnhart6lZfqQ3pMb1NzY7eZvkP6c2LIk1CbqRomtb+UufH6j3Yu+CBpxqqy99VcVeNjYoKtnKVfv7fHXqTAmXMTaNQ6hDtH5iWKZslGDN7QbBiczfsmezMEDT2Q0bWP/TzgdD1n1BLAQIeAwoAAAAIABY7vFD7lxPkAgMAALoHAAAIAAAAAAAAAAAAAADzAgAAAABpbmRleC5weVBLBQYAAAAAAQABADYAAAAoAwAAAAA="
       },
       "func_name": "get_html",
       "handler": "index.handler",
       "memory_size": 256,
       "package": "default",
       "runtime": "Python2.7",
       "timeout": 5
      }

-  Sample response

   .. code-block::

      {
       "func_urn": "urn:fss:{project_name}:{project_id}:function:default:get_html:latest",
       "func_name": "get_html",
       "domain_id": "89fexxxd636",
       "namespace": "{project_id}",
       "project_name": "xxx",
       "package": "default",
       "runtime": "Python2.7",
       "timeout": 5,
       "handler": "index.handler",
       "memory_size": 256,
       "cpu": 400,
       "code_type": "inline",
       "code_filename": "index.zip",
       "code_size": 884,
       "digest": "b08fef5e97dd130037978db07f0e9109aa43a191517cd1196bcab822f17dddcf37f7506a15691177962f9803ba6d170a1c87aafb4fa1b9f0d07f9415642b26d2",
       "version": "latest",
       "image_name": "latest-200604105808@we0qo",
       "last_modified": "2020-06-04T10:58:08+08:00",
       "strategy_config": {
        "concurrency": -1
       },
       "StrategyConfig": {},
       "enterprise_project_id": "0"
      }

   Record the URN of the function, that is, the value of **func_urn** in the response.

Step 2: Create an APIG Trigger
------------------------------

URI: **POST /v2/**\ *{project_id}*\ **/fgs/triggers/**\ *{function_urn}*

For details, see :ref:`Creating a Trigger <functiongraph_06_0122>`.

-  Sample request

   .. code-block:: text

      POST  https://{Endpoint}/v2/{project_id}/fgs/triggers/{function_urn}
      {
       "event_data": {
        "group_id": "a9ad0d5df4d7475c9bc35a7c17d89304",
        "env_id": "DEFAULT_ENVIRONMENT_RELEASE_ID",
        "auth": "NONE",
        "protocol": "HTTP",
        "name": "API_GetHtml",
        "path": "/test",
        "match_mode": "SWA",
        "req_method": "ANY",
        "backend_type": "FUNCTION",
        "sl_domain": "a9ad0d5df4d7475c9bc35a7c17d89304.apig.xxx.xxxapis.com",
        "type": 1,
        "env_name": "RELEASE"
       },
       "event_type_code": "APICreated",
       "trigger_status": "ACTIVE",
       "trigger_type_code": "APIG"
      }

   **function_urn** indicates the function URN recorded in :ref:`Step 1: Create a Function to Return a Static Web Page <functiongraph_06_0203__section5121646125111>`, **group_id** indicates an API group ID, and **sl_domain** indicates the subdomain name that APIG allocates to the API group.

-  Sample response

   .. code-block::

      {
       "trigger_id": "1b3ec74b86454aa39001a9f89cc70ee2",
       "trigger_type_code": "APIG",
       "trigger_status": "ACTIVE",
       "event_data": {
        "api_id": "cbc698153d1f4265bdd8384b5cf6e581",
        "api_name": "API_GetHtml",
        "auth": "NONE",
        "env_id": "",
        "env_name": "",
        "func_info": {
         "function_urn": "urn:fss:{project_name}:{project_id}:function:default:get_html",
         "invocation_type": "sync",
         "timeout": 5000,
         "version": "latest"
        },
        "group_id": "a9ad0d5df4d7475c9bc35a7c17d89304",
        "group_name": "APIGroup_gethtml",
        "invoke_url": "http://a9ad0d5df4d7475c9bc35a7c17d89304.apig.xxx.xxxapis.com/test",
        "match_mode": "SWA",
        "name": "API_GetHtml",
        "path": "/test",
        "protocol": "HTTP",
        "req_method": "ANY",
        "triggerid": "1b3ec74b86454aa39001a9f89cc70ee2",
        "type": 1
       },
       "last_updated_time": "2020-06-04T17:14:32+08:00",
       "created_time": "2020-06-04T17:14:32+08:00"
      }

   Record the value of **invoke_url**.

Step 3: Call the API of the APIG Trigger to Obtain a Static Web Page
--------------------------------------------------------------------

Enter the value of **invoke_url** in the address bar of a browser to obtain a static web page.


.. figure:: /_static/images/en-us_image_0000001483376169.png
   :alt: **Figure 1** Calling the API

   **Figure 1** Calling the API
