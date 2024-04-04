:original_name: functiongraph_01_0204.html

.. _functiongraph_01_0204:

Using an APIG (Dedicated) Trigger
=================================

Prerequisites
-------------

You have created an API group, for example, **APIGroup_test**. For details, see `Creating an API Group <https://docs.otc.t-systems.com/api-gateway/umn/api_opening/api_group_management/creating_an_api_group.html#apig-en-ug-180307015>`__.

Creating an APIG Trigger
------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. On the **Function List** page, click **Create Function** in the upper right corner.

#. Set the following parameters:

   -  **Function Name**: Enter a function name, for example, **apig**.
   -  **Agency**: Select **Use no agency**.
   -  **Enterprise Project**: Select **default**.
   -  **Runtime**: Select **Python 2.7**.

#. Click **Create**.

#. On the **Code** tab page, copy the following code to the code window and click **Deploy**.

   .. code-block::

      # -*- coding:utf-8 -*-
      import json
      def handler (event, context):
          body = "<html><title>Functiongraph Demo</title><body><p>Hello, FunctionGraph!</p></body></html>"
          print(body)
          return {
              "statusCode":200,
              "body":body,
              "headers": {
                  "Content-Type": "text/html",
              },
              "isBase64Encoded": False
          }

#. Choose **Configuration** > **Triggers** and click **Create Trigger**.


   .. figure:: /_static/images/en-us_image_0000001679340817.png
      :alt: **Figure 1** Creating a trigger

      **Figure 1** Creating a trigger

#. Configure the trigger information.

   .. table:: **Table 1** Trigger information

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================+
      | Trigger Type                      | Select **API Gateway (Dedicated Gateway)**.                                                                                                                                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | API Instance                      | Select an instance. If no instance is available, click **Create Instance**.                                                                                                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | API Name                          | Enter an API name, for example, **API_apig**.                                                                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | API Group                         | An API group is a collection of APIs. You can manage APIs by API group.                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                        |
      |                                   | Select **APIGroup_test**.                                                                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Environment                       | An API can be called in different environments, such as production, test, and development environments. APIG supports environment management, which allows you to define different request paths for an API in different environments. |
      |                                   |                                                                                                                                                                                                                                        |
      |                                   | To ensure that the API can be called, select **RELEASE**.                                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Authentication           | There are three authentication modes:                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                        |
      |                                   | -  **App**: AppKey and AppSecret authentication. This mode is of high security and is recommended.                                                                                                                                     |
      |                                   | -  **IAM**: IAM authentication. This mode grants access permissions to IAM users only and is of medium security.                                                                                                                       |
      |                                   | -  **None**: No authentication. This mode grants access permissions to all users.                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                        |
      |                                   | Select **None**.                                                                                                                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol                          | There are two types of protocols:                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                        |
      |                                   | -  HTTP                                                                                                                                                                                                                                |
      |                                   | -  HTTPS                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                        |
      |                                   | Select **HTTPS**.                                                                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Timeout (ms)                      | Enter **5000**.                                                                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.


   .. figure:: /_static/images/en-us_image_0000001455081958.png
      :alt: **Figure 2** Creating a trigger

      **Figure 2** Creating a trigger

   .. note::

      a. **URL** indicates the calling address of the APIG trigger.
      b. After the APIG trigger is created, an API named **API_apig** is generated on the APIG console. You can click the API name in the trigger list to go to the APIG console.

Invoking the Function
---------------------

#. Enter the URL of the APIG trigger in the address bar of a browser, and press **Enter**.

#. View the execution result, as shown in :ref:`Figure 3 <functiongraph_01_0204__en-us_topic_0000001251588440_fig640414181488>`.

   .. _functiongraph_01_0204__en-us_topic_0000001251588440_fig640414181488:

   .. figure:: /_static/images/en-us_image_0000001504921529.png
      :alt: **Figure 3** Returned result

      **Figure 3** Returned result

   .. note::

      a. The input for APIG invocation comes from an event template provided by the function. For details, see :ref:`Table 2 <functiongraph_01_0302__en-us_topic_0000001252067188_table52979501006>`.
      b. The function response for APIG invocation is encapsulated and must contain **body(String)**, **statusCode(int)**, **headers(Map)**, and **isBase64Encoded(boolean)**.

Viewing the Execution Result
----------------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. Click a function to go to the function details page.
#. Choose **Monitoring** > **Logs** to query function running logs.
