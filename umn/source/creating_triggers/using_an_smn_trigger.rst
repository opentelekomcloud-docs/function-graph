:original_name: functiongraph_01_0202.html

.. _functiongraph_01_0202:

Using an SMN Trigger
====================

This section describes how to create an SMN trigger and publish a message to trigger a function.

For details about the SMN event source, see section "Supported Event Sources".

Prerequisites
-------------

-  You have created an SMN topic, for example, **smn-test**. For details, see `Creating a Topic <https://docs.otc.t-systems.com/simple-message-notification/umn/topic_management/creating_a_topic.html#en-us-topic-0043961401>`__.
-  You have created a function. For details, see :ref:`Creating a Function from Scratch <functiongraph_01_0153>`.

Creating an SMN Trigger
-----------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Triggers** and click **Create Trigger**.


   .. figure:: /_static/images/en-us_image_0000001679340817.png
      :alt: **Figure 1** Creating a trigger

      **Figure 1** Creating a trigger

#. Set the following parameters:

   -  **Trigger Type**: Select **Simple Message Notification (SMN)**.
   -  **Topic Name**: Select a topic, for example, **smn-test**.

#. Click **OK**.

   .. note::

      After the SMN trigger is created, a subscription is generated for the corresponding topic on the SMN console.

Publishing a Message to Trigger the Function
--------------------------------------------

On the SMN console, publish a message to the **smn-test** topic. For details, see `Publishing a Text Message <https://docs.otc.t-systems.com/simple-message-notification/umn/topic_management/publishing_a_message/publishing_a_text_message.html#en-us-topic-0043961403>`__.

:ref:`Table 1 <functiongraph_01_0202__en-us_topic_0000001298547977_table833644511032>` describes the parameters required for publishing a message.

.. _functiongraph_01_0202__en-us_topic_0000001298547977_table833644511032:

.. table:: **Table 1** Parameters required for publishing a message

   ============== ==============================
   Parameter      Description
   ============== ==============================
   Subject        Enter **SMN-Test**.
   Message Format Select **Text**.
   Message        Enter **{"message":"hello"}**.
   ============== ==============================

.. note::

   After a message is published, the function is triggered automatically. For details about example events, see section "Supported Event Sources".

Viewing the Execution Result
----------------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. Click a function to go to the function details page.
#. Choose **Monitoring** > **Logs** to query function running logs.
