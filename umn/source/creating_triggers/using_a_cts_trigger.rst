:original_name: functiongraph_01_0209.html

.. _functiongraph_01_0209:

Using a CTS Trigger
===================

For details about the CTS event source, see section "Supported Event Sources".

Prerequisites
-------------

You have created an agency on IAM. For details, see :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.

Creating a CTS Trigger
----------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. On the **Function List** page, click **Create Function** in the upper right corner.

#. Set the following parameters:

   -  **Function Name**: Enter a function name, for example, **HelloWorld**.
   -  **Agency**: Select **Use no agency**.
   -  **Enterprise Project**: Select **default**.
   -  **Runtime**: Select **Python 2.7**.

#. Click **Create Function**.

#. On the **Code** tab page, copy the following code to the code window and click **Deploy**.

   .. code-block::

      # -*- coding:utf-8 -*-
      '''
      CTS trigger event:
      {
        "cts":  {
              "time": "",
              "user": {
                  "name": "userName",
                  "id": "",
                  "domain": {
                      "name": "domainName",
                      "id": ""
                  }
              },
              "request": {},
              "response": {},
              "code": 204,
              "service_type": "FunctionGraph",
              "resource_type": "",
              "resource_name": "",
              "resource_id": {},
              "trace_name": "",
              "trace_type": "ConsoleAction",
              "record_time": "",
              "trace_id": "",
              "trace_status": "normal"
          }
      }
      '''
      def handler (event, context):
          trace_name = event["cts"]["resource_name"]
          timeinfo = event["cts"]["time"]
          print(timeinfo+' '+trace_name)

#. Choose **Configuration** > **Triggers** and click **Create Trigger**.


   .. figure:: /_static/images/en-us_image_0000001679340817.png
      :alt: **Figure 1** Creating a trigger

      **Figure 1** Creating a trigger

#. Configure the trigger information.

   .. table:: **Table 1** Trigger information

      +-------------------------+---------------------------------------------------------------------------------------------------------+
      | Parameter               | Description                                                                                             |
      +=========================+=========================================================================================================+
      | Trigger Type            | Select **Cloud Trace Service (CTS)**.                                                                   |
      +-------------------------+---------------------------------------------------------------------------------------------------------+
      | Event Notification Name | Enter a notification name, for example, **Test**.                                                       |
      +-------------------------+---------------------------------------------------------------------------------------------------------+
      | Service Type            | Select **FunctionGraph**.                                                                               |
      +-------------------------+---------------------------------------------------------------------------------------------------------+
      | Resource Type           | Resource types supported by the selected service, such as triggers, instances, and functions.           |
      +-------------------------+---------------------------------------------------------------------------------------------------------+
      | Trace Name              | Operations that can be performed on the selected resource type, such as creating or deleting a trigger. |
      +-------------------------+---------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Configuring a CTS Event to Trigger the Function
-----------------------------------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the function details page, select a version, and click **Test**. The **Configure Test Event** dialog box is displayed.

#. Set the parameters described in :ref:`Table 2 <functiongraph_01_0209__en-us_topic_0000001298667437_table19101881852>` and click **Save**.

   .. _functiongraph_01_0209__en-us_topic_0000001298667437_table19101881852:

   .. table:: **Table 2** Test event information

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                         |
      +===================================+=====================================================================================================================+
      | Configure Test Event              | You can choose to create a test event or edit an existing one.                                                      |
      |                                   |                                                                                                                     |
      |                                   | Use the default option **Create new test event**.                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Event Template                    | Select **Cloud Trace Service (CTS)** and use the built-in CTS event template.                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Event Name                        | Enter an event name, for example, **cts-test**.                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Event data                        | The system automatically loads the event data in the CTS event template. You can modify the event data as required. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+

#. Click **Test**. The function test result is displayed.
