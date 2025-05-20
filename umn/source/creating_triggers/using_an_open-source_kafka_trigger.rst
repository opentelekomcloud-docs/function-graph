:original_name: functiongraph_01_1838.html

.. _functiongraph_01_1838:

Using an Open-Source Kafka Trigger
==================================

This section describes how to create an open-source Kafka trigger and configure an event to trigger a function.

If you use an open-source Kafka trigger for a function, FunctionGraph periodically polls messages from a specific topic in Kafka and passes the messages as an input parameter to invoke the function.

.. note::

   -  For details about the differences between DMS for Kafka and open-source Kafka, see `Comparing DMS for Kafka and Open-Source Kafka <https://docs.otc.t-systems.com/distributed-message-service/umn/service_overview/comparing_dms_for_kafka_and_open-source_kafka.html#kafka-pd-200720001>`__.
   -  In cases of Kafka data processing failure, the Kafka trigger will discard records that are larger than 6 MB.

Prerequisites
-------------

Before creating a trigger, ensure that you have prepared the following:

-  You have created a function.
-  You have enabled VPC access for the function. For details, see :ref:`Configuring the Network <functiongraph_01_0222>`.

Creating an Open-Source Kafka Trigger
-------------------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Triggers** and click **Create Trigger**.


   .. figure:: /_static/images/en-us_image_0000001630743710.png
      :alt: **Figure 1** Creating a trigger

      **Figure 1** Creating a trigger

#. Set the following parameters:

   -  **Trigger Type**: Select **Kafka (OPENSOURCEKAFKA)**.
   -  **Connection Address**: Addresses of brokers running Kafka. Separate the addresses with commas (,).
   -  **Topic**: Enter one or more topics.
   -  **Batch Size**: Maximum number of data records that can be processed by the function at a time.

#. Click **OK**.

   .. note::

      The network configuration must be the same as that of the ECS where Kafka is deployed, including the VPC and subnet.

Enabling a Kafka Trigger
------------------------

By default, open-source Kafka triggers are disabled. To use such a trigger, click **Enable** on the **Trigger** page.

.. note::

   If a trigger cannot be disabled, contact technical support.

Configuring a Kafka Event to Trigger the Function
-------------------------------------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the function details page, select a version.

#. On the **Code** tab page, click **Test**. The **Configure Test Event** dialog box is displayed.

#. Set the parameters described in :ref:`Table 1 <functiongraph_01_1838__en-us_topic_0000001510377965__table15199135171812>` and click **Save**.

   .. _functiongraph_01_1838__en-us_topic_0000001510377965__table15199135171812:

   .. table:: **Table 1** Test event information

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================================+
      | Configure Test Event              | You can choose to create a test event or edit an existing one.                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                |
      |                                   | Use the default option **Create new test event**.                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Template                    | Select **Kafka (OPENSOURCEKAFKA)** to use the built-in Kafka event template.                                                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Name                        | The event name can contain 1 to 25 characters and must start with a letter and end with a letter or digit. Only letters, digits, underscores (_), and hyphens (-) are allowed. For example, **kafka-123test**. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event data                        | The system automatically loads the built-in Kafka event template, which is used in this example without modifications.                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Test**. The function test result is displayed.
