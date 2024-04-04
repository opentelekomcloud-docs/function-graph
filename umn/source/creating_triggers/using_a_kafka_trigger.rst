:original_name: functiongraph_01_0214.html

.. _functiongraph_01_0214:

Using a Kafka Trigger
=====================

This section describes how to create a Kafka trigger and configure a Kafka event to trigger a function.

After a Kafka trigger is used, FunctionGraph periodically polls for new messages in a specific topic in a Kafka instance and passes the messages as input parameters to invoke functions. For details about the DMS for Kafka event source, see section "Supported Event Sources".

.. note::

   For details about the differences between DMS for Kafka and open-source Kafka, see `Comparing DMS for Kafka and Open-Source Kafka <https://docs.otc.t-systems.com/distributed-message-service/umn/service_overview/comparing_dms_for_kafka_and_open-source_kafka.html#kafka-pd-200720001>`__.

Prerequisites
-------------

Before creating a trigger, ensure that you have prepared the following:

-  You have created a function. For details, see :ref:`Creating a Function from Scratch <functiongraph_01_0153>`.
-  You have enabled VPC access for the function. For details, see :ref:`Configuring the Network <functiongraph_01_0222>`.
-  You have created a Kafka instance. For details, see "Creating an Instance" in the *Distributed Message Service for Kafka User Guide*.
-  You have created a topic under a Kafka instance. For details, see section "Creating a Topic" in the *Distributed Message Service for Kafka User Guide*.

Creating a Kafka Trigger
------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Triggers** and click **Create Trigger**.


   .. figure:: /_static/images/en-us_image_0000001679340817.png
      :alt: **Figure 1** Creating a trigger

      **Figure 1** Creating a trigger

#. Set the following parameters:

   -  **Trigger Type**: Select **DMS (for Kafka)**.
   -  **Instance**: Select a Kafka premium instance.
   -  **Topic**: Select a topic of the Kafka premium instance.
   -  **Batch Size**: Set the number of messages to be retrieved from a topic each time.
   -  **Username**: Enter the username of the instance if SSL has been enabled for it.
   -  **Password**: Enter the password of the instance if SSL has been enabled for it.

#. Click **OK**.

   .. note::

      -  After VPC access is enabled, you need to configure corresponding subnet permissions for the Kafka security group. For details about how to configure VPC access, see :ref:`Configuring the Network <functiongraph_01_0222>`.

      -  You can create a Kafka trigger with multiple topics. You do not need to create one such trigger for each topic in the same instance.


         .. figure:: /_static/images/en-us_image_0000001659754612.png
            :alt: **Figure 2** Selecting multiple topics

            **Figure 2** Selecting multiple topics

Configuring a Kafka Event to Trigger the Function
-------------------------------------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the function details page, select a version.

#. On the **Code** tab page, click **Test**. The **Configure Test Event** dialog box is displayed.

#. Set the parameters described in :ref:`Table 1 <functiongraph_01_0214__en-us_topic_0000001298667457_table15199135171812>` and click **Save**.

   .. _functiongraph_01_0214__en-us_topic_0000001298667457_table15199135171812:

   .. table:: **Table 1** Test event information

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================================+
      | Configure Test Event              | You can choose to create a test event or edit an existing one.                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                |
      |                                   | Use the default option **Create new test event**.                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Template                    | Select **DMS (for Kafka)** to use the built-in Kafka event template.                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Name                        | The event name can contain 1 to 25 characters and must start with a letter and end with a letter or digit. Only letters, digits, underscores (_), and hyphens (-) are allowed. For example, **kafka-123test**. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event data                        | The system automatically loads the built-in Kafka event template, which is used in this example without modifications.                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Test**. The function test result is displayed.
