:original_name: functiongraph_01_1062.html

.. _functiongraph_01_1062:

Asynchronous Invocation
=======================

When a client triggers a function, FunctionGraph persists the request and sends a response immediately to the client. The client proceeds without waiting for the execution result. You cannot know the result in real time. FunctionGraph queues the asynchronous requests and processes them when the server is idle. To obtain asynchronous processing results or to retry when an asynchronous request fails, :ref:`configure asynchronous settings <functiongraph_01_0390_03>`.

-  The following triggers are invoked asynchronously by default and the invocation mode cannot be changed.

   .. table:: **Table 1** Invocation mode

      ============= ===============
      Event Source  Invocation Mode
      ============= ===============
      SMN           Asynchronous
      OBS           Asynchronous
      Timer         Asynchronous
      LTS           Asynchronous
      CTS           Asynchronous
      DDS           Asynchronous
      DMS for Kafka Asynchronous
      ============= ===============

-  APIG (dedicated) triggers can be configured for asynchronous invocation on their console. You can also use the asynchronous execution API instead. In this scenario, the maximum execution duration of a function is 12 hours (configured in the whitelist).

   .. note::

      If the E2E function execution latency exceeds 90s, asynchronous invocation is recommended. If synchronous invocation is used, no responses can be received after 90s due to gateway restrictions.

**Example**

The following procedure uses the APIG trigger of a function as an example. For details about how to create an APIG trigger, see :ref:`Using an APIG (Dedicated) Trigger <functiongraph_01_0204>`.

#. Go to the function details page, and choose **Configuration** > **Triggers**.

#. Click the APIG trigger name to go to the APIG console.


   .. figure:: /_static/images/en-us_image_0000001352771114.png
      :alt: **Figure 1** Clicking a trigger name

      **Figure 1** Clicking a trigger name

#. Click **Modify** in the upper right.


   .. figure:: /_static/images/en-us_image_0000002357971441.png
      :alt: **Figure 2** Clicking Modify

      **Figure 2** Clicking Modify

#. Click **Next** until the **Backend Configuration** page is displayed. Then change **Invocation Mode** to **Asynchronous**.


   .. figure:: /_static/images/en-us_image_0000002357973433.png
      :alt: **Figure 3** Changing the invocation mode

      **Figure 3** Changing the invocation mode

#. Click **Finish** to save the settings.
