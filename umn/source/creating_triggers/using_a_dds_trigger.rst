:original_name: functiongraph_01_0210.html

.. _functiongraph_01_0210:

Using a DDS Trigger
===================

This section describes how to create a DDS trigger for a function, and invoke the function when a database table changes.

A function using a DDS trigger will be triggered every time a database table is updated. For details about the DDS event source, see section "Supported Event Sources".

Prerequisites
-------------

Before creating a trigger, ensure that you have prepared the following:

-  You have created a function. For details, see :ref:`Creating a Function from Scratch <functiongraph_01_0153>`.
-  You have enabled VPC access for the function. For details, see :ref:`Configuring the Network <functiongraph_01_0222>`.
-  You have created a DDS DB instance.
-  You have created a DDS database.

Creating a DDS Trigger
----------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Triggers** and click **Create Trigger**.


   .. figure:: /_static/images/en-us_image_0000001679340817.png
      :alt: **Figure 1** Creating a trigger

      **Figure 1** Creating a trigger

#. Set the following parameters:

   -  **Trigger Type**: Select **Document Database Service (DDS)**.
   -  **DB Instance**: Select a DDS DB instance.
   -  **Password**: Enter the password of DDS DB instance administrator **rwuser**.
   -  **Database**: Enter the name of a database. Note that **admin**, **local**, and **config** are reserved database names and cannot be used here.
   -  **Collection**: Enter the name of a database collection.
   -  **Batch Size**: Set the number of records to be read from the database at a time.

#. Click **OK**.

   .. note::

      After VPC access is enabled, you need to configure corresponding subnet permissions for the DDS security group. For details about how to configure VPC access, see :ref:`Configuring the Network <functiongraph_01_0222>`.

Configuring a DDS Event to Trigger the Function
-----------------------------------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the function details page, select a version, and click **Test**. The **Configure Test Event** dialog box is displayed.

#. Set the parameters described in :ref:`Table 1 <functiongraph_01_0210__en-us_topic_0000001251588444_table15199135171812>` and click **Save**.

   .. _functiongraph_01_0210__en-us_topic_0000001251588444_table15199135171812:

   .. table:: **Table 1** Test event information

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================+
      | Configure Test Event              | You can choose to create a test event or edit an existing one.                                                                                                                                               |
      |                                   |                                                                                                                                                                                                              |
      |                                   | Use the default option **Create new test event**.                                                                                                                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Template                    | Select **dds-event-template**.                                                                                                                                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Name                        | The event name can contain 1 to 25 characters and must start with a letter and end with a letter or digit. Only letters, digits, underscores (_), and hyphens (-) are allowed. For example, **dds-123test**. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event data                        | The system automatically loads the built-in DDS event template, which is used in this example without modifications.                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Test**. The function test result is displayed.
