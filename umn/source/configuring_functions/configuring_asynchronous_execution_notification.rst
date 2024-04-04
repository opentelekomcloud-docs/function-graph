:original_name: functiongraph_01_0390_03.html

.. _functiongraph_01_0390_03:

Configuring Asynchronous Execution Notification
===============================================

Overview
--------

Functions can be invoked synchronously or asynchronously. In asynchronous mode, FunctionGraph sends a response immediately after persisting a request. The request result cannot be known in real time. To retry when an asynchronous request fails or obtain asynchronous processing results, configure asynchronous settings.

Scenario
--------

-  Retry: By default, FunctionGraph does not retry if a function fails due to a code error. If your function needs retry, for example, if third-party services often fail to be invoked, configure retry to improve the success rate.
-  Result notifications: FunctionGraph automatically notifies downstream services of the asynchronous execution result of a function for further processing. For example, storing execution failure information in OBS for cause analysis, or pushing execution success information to DIS or triggering the function again.

Procedure
---------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Configure Async Notification**. On the displayed page, click **Edit** next to **Asynchronous Notification Policy**.


   .. figure:: /_static/images/en-us_image_0000001298786917.png
      :alt: **Figure 1** Configuring an asynchronous notification policy

      **Figure 1** Configuring an asynchronous notification policy

#. Set parameters by referring to :ref:`Table 1 <functiongraph_01_0390_03__en-us_topic_0000001298507437_table16541037131110>`. For example, specify **FunctionGraph** for **Target Service**.


   .. figure:: /_static/images/en-us_image_0000001702539580.png
      :alt: **Figure 2** Setting parameters

      **Figure 2** Setting parameters

   .. _functiongraph_01_0390_03__en-us_topic_0000001298507437_table16541037131110:

   .. table:: **Table 1** Parameter description

      +--------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                  | Description                                                                                                                |
      +============================================+============================================================================================================================+
      | Asynchronous Execution Notification Policy | -  **Max. Retries**: maximum number of retries when asynchronous invocation fails. Value range: 0-3. Default value: **1**. |
      |                                            | -  **Max. Validity Period (s)**: maximum lifetime of a message in seconds. Value range: 1-86,400.                          |
      +--------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Success Notification                       | **Target Service**: to which a notification will be sent if a function is executed successfully.                           |
      |                                            |                                                                                                                            |
      |                                            | a. FunctionGraph                                                                                                           |
      |                                            | b. OBS                                                                                                                     |
      |                                            | c. SMN                                                                                                                     |
      +--------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Failure Notification                       | **Target Service**: to which a notification will be sent if a function fails to be executed.                               |
      |                                            |                                                                                                                            |
      |                                            | a. FunctionGraph                                                                                                           |
      |                                            | b. OBS                                                                                                                     |
      |                                            | c. SMN                                                                                                                     |
      +--------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   .. note::

      a. Set an agency that allows FunctionGraph to access the target service.
      b. To avoid cyclic invocation, do not set two functions as asynchronous execution targets of each other.

Configuration Description
-------------------------

For details about how to set the target for asynchronous invocation, see :ref:`Table 2 <functiongraph_01_0390_03__en-us_topic_0000001298507437_table187072059205>`. The following shows an example:

.. code-block::

   {
           "timestamp": "2020-08-20T12:00:00.000Z+08:00",
       "request_context": {
               "request_id": "1167bf8c-87b0-43ab-8f5f-26b16c64f252",
               "function_urn": "urn:fss:xx-xxxx-x:xxxxxxx:function:xxxx:xxxx:latest",
               "condition": "",
               "approximate_invoke_count": 0
        },
           "request_payload": "",
           "response_context": {
               "status_code": 200,
               "function_error": ""
         },
        "response_payload": "hello world!"
   }

.. _functiongraph_01_0390_03__en-us_topic_0000001298507437_table187072059205:

.. table:: **Table 2** Parameter description

   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | Parameter                                 | Description                                                                                                   |
   +===========================================+===============================================================================================================+
   | timestamp                                 | Time when the invocation starts.                                                                              |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | request_context                           | Request context.                                                                                              |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | request_context.request_id                | ID of an asynchronous invocation request.                                                                     |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | request_context. function_urn             | URN of the function that is to be executed asynchronously.                                                    |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | request_context.condition                 | Invocation error type.                                                                                        |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | request_context. approximate_invoke_count | Number of asynchronous invocation times. If the value is greater than 1, function execution has been retried. |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | request_payload                           | Original request payload.                                                                                     |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | response_context                          | Response context.                                                                                             |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | response_context.statusCode               | Code returned after function invocation. If the code is not 200, a system error occurred.                     |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | response_context.function_error           | Invocation error information.                                                                                 |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | response_payload                          | Payload returned after function execution.                                                                    |
   +-------------------------------------------+---------------------------------------------------------------------------------------------------------------+
