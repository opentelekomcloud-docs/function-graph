:original_name: functiongraph_01_0394.html

.. _functiongraph_01_0394:

Using a RocketMQ Trigger
========================

This section describes how to create a RocketMQ trigger and configure a RocketMQ event to trigger a function. When a DMS (for RocketMQ) trigger is used, FunctionGraph periodically polls for new messages in a specific topic bound to the exchange of a RocketMQ instance and passes the messages as input parameters to invoke functions.

Prerequisites
-------------

-  You have created a function. For details, see :ref:`Creating a Function from Scratch <functiongraph_01_0153>`.
-  An agency with VPC management permissions has been configured for the function. For details about how to create an agency, see :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.
-  You have enabled VPC access. For details, see :ref:`Configuring Public Access or VPC Access <functiongraph_01_0222>`.
-  A RocketMQ instance has been created..
-  The rules of the security group of the instance have been correctly configured.

   #. In the **Network** section on the **Basic Information** tab page, click the name of the security group.
   #. Click the **Inbound Rules** tab to view the inbound rules of the security group.

      a. ACL disabled

         For intra-VPC access, inbound access through port **8100** must be allowed.

         For public access, inbound access through port **8100** must be allowed.

      b. ACL enabled

         For intra-VPC access, inbound access through port **8100** must be allowed.

         For public access, inbound access through port **8200** must be allowed.

-  A topic has been created for the RocketMQ instance..

.. note::

   When **VPC Access** is enabled for FunctionGraph, ensure that the VPC selected is the same as the VPC selected when the RocketMQ instance is created.

Creating a RocketMQ Trigger
---------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Triggers** and click **Create Trigger**.


   .. figure:: /_static/images/en-us_image_0000001679340817.png
      :alt: **Figure 1** Creating a trigger

      **Figure 1** Creating a trigger

4. Set the following parameters:

   -  **Trigger Type**: Select **Distributed Message Service (DMS) for RocketMQ**.
   -  **Instance**: Select a RocketMQ instance.
   -  **Topic**: Select a topic you created from the drop-down list.
   -  **Batch Size**: Maximum number of data records that can be obtained a time. Range: 1-1,000.

5. Click **OK**.

.. note::

   -  After VPC access is enabled, you need to configure corresponding subnet permissions for the RocketMQ security group. For details about how to configure VPC access, see :ref:`Configuring the Network <functiongraph_01_0222>`.
   -  A newly created RocketMQ trigger is disabled by default. To use it, click **Enable**.

Configuring a RocketMQ Event to Trigger the Function
----------------------------------------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the function details page, select a version.

#. On the **Code** tab page, click **Test**. The **Configure Test Event** dialog box is displayed.

#. Set the parameters described in :ref:`Table 1 <functiongraph_01_0394__en-us_topic_0000001896474261_table1255753935319>` and click **Save**.

   .. _functiongraph_01_0394__en-us_topic_0000001896474261_table1255753935319:

   .. table:: **Table 1** Test event information

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================================+
      | Configure Test Event              | You can choose to create a test event or edit an existing one.                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                |
      |                                   | Use the default option **Create new test event**.                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Template                    | Select **Distributed Message Service (DMS) for RocketMQ** and use the built-in event template.                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Name                        | The event name can contain 1 to 25 characters and must start with a letter and end with a letter or digit. Only letters, digits, underscores (_), and hyphens (-) are allowed. For example, **kafka-123test**. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event data                        | The system automatically loads the built-in RocketMQ event template, which is used in this example without modifications.                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

6. Click **Test**. The function test result is displayed.
