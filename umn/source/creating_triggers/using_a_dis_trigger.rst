:original_name: functiongraph_01_0206.html

.. _functiongraph_01_0206:

Using a DIS Trigger
===================

For details about the DIS event source, see section "Supported Event Sources".

Prerequisites
-------------

Before creating a trigger, ensure that you have prepared the following:

-  You have created a function. For details, see :ref:`Creating a Function from Scratch <functiongraph_01_0153>`.
-  You have created a DIS stream, for example, **dis-function**. For details, see `Creating a DIS Stream <https://docs.otc.t-systems.com/data-ingestion-service/umn/getting_started/step_1_creating_a_dis_stream.html#dis-01-0601>`__.

Setting an Agency
-----------------

Before creating a DIS trigger, set an agency to delegate FunctionGraph to access DIS. For details on how to create an agency, see :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.

Since you did not specify an agency while creating the **HelloWorld** function, specify one first.

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. Click the function to be configured to go to the function details page.
#. Choose **Configuration** > **Permissions**, and change the agency to **serverless-trust** created in :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.
#. Click **Save**.

Creating a DIS Trigger
----------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. Click the function to be configured to go to the function details page.
#. Choose **Configuration** > **Triggers** and click **Create Trigger**.
#. Set the following parameters:

   -  **Trigger Type**: Select **Data Ingestion Service (DIS)**.
   -  **Stream Name**: Select a DIS stream, for example, **dis-function**.
   -  **Max. Fetch Bytes**: Maximum volume of data that can be fetched in each request. Only the records smaller than this value will be fetched. The value ranges from 0 KB to 4 MB.
   -  **Starting Position**: Specify a position in the specified stream from which to start reading data.

      -  **TRIM_HORIZON**: Data is read from the earliest valid records that are stored in the partition.
      -  **LATEST**: Data is read just after the most recent record in the partition. This setting ensures that you always read the latest data.

   -  **Pull Period**: Set a period for pulling data from the stream.
   -  **Serial Data Processing**: If this option is selected, FunctionGraph pulls data from the stream only after previous data is processed. If this option is not selected, FunctionGraph pulls data from the stream as long as the pull period ends.

#. Click **OK**.

Configuring a DIS Event to Trigger the Function
-----------------------------------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the function details page, select a version.

#. On the **Code** tab page, click **Test**. The **Configure Test Event** dialog box is displayed.

#. Set the parameters described in :ref:`Table 1 <functiongraph_01_0206__en-us_topic_0000001251907940_table187784018405>` and click **Save**.

   .. _functiongraph_01_0206__en-us_topic_0000001251907940_table187784018405:

   .. table:: **Table 1** Test event information

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================+
      | Configure Test Event              | You can choose to create a test event or edit an existing one.                                                                                                                                               |
      |                                   |                                                                                                                                                                                                              |
      |                                   | Use the default option **Create new test event**.                                                                                                                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Template                    | Select **Data Ingestion Service (DIS)** to use the built-in DIS event template.                                                                                                                              |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Name                        | The event name can contain 1 to 25 characters and must start with a letter and end with a letter or digit. Only letters, digits, underscores (_), and hyphens (-) are allowed. For example, **dis-123test**. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event data                        | The system automatically loads the built-in DIS event template, which is used in this example without modifications.                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Test**. The function test result is displayed.
