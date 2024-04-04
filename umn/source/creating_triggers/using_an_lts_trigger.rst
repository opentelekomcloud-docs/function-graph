:original_name: functiongraph_01_0208.html

.. _functiongraph_01_0208:

Using an LTS Trigger
====================

For details about the timer event source, see section "Supported Event Sources".

Prerequisites
-------------

-  You have created a function. For details, see :ref:`Creating a Function from Scratch <functiongraph_01_0153>`.
-  You have created an agency with the **LTS FullAccess** permission. For details about how to create an agency, see :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.
-  You have created a log group, for example, **LogGroup1**. For details, see `Creating a Log Group <https://docs.otc.t-systems.com/log-tank-service/umn/log_management/managing_log_groups.html#lts-04-0003>`__.
-  You have created a log stream, for example, **LogTopic1**. For details, see `Creating a Log Stream <https://docs.otc.t-systems.com/log-tank-service/umn/log_management/managing_log_streams.html>`__.

Creating an LTS Trigger
-----------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Triggers** and click **Create Trigger**.


   .. figure:: /_static/images/en-us_image_0000001679340817.png
      :alt: **Figure 1** Creating a trigger

      **Figure 1** Creating a trigger

#. Set the following parameters:

   -  **Trigger Type**: Select **Log Tank Service (LTS)**.
   -  **Log Group**: Select a log group, for example, **LogGroup1**.
   -  **Log Stream**: Select a log stream, for example, **LogStream1**.

#. Click **OK**.

Configuring an LTS Event to Trigger the Function
------------------------------------------------

.. note::

   When the size of an LTS event message exceeds 75 KB, it will be split into multiple messages by 75 KB to trigger the function.

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the function details page, select a version.

#. On the **Code** tab page, click **Test**. The **Configure Test Event** dialog box is displayed.

#. Set the parameters described in :ref:`Table 1 <functiongraph_01_0208__en-us_topic_0000001298667461_table15199135171812>` and click **Save**.

   .. _functiongraph_01_0208__en-us_topic_0000001298667461_table15199135171812:

   .. table:: **Table 1** Test event information

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================+
      | Configure Test Event              | You can choose to create a test event or edit an existing one.                                                                                                                                               |
      |                                   |                                                                                                                                                                                                              |
      |                                   | Use the default option **Create new test event**.                                                                                                                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Template                    | Select **lts-event-template**.                                                                                                                                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Name                        | The event name can contain 1 to 25 characters and must start with a letter and end with a letter or digit. Only letters, digits, underscores (_), and hyphens (-) are allowed. For example, **lts-123test**. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event data                        | The system automatically loads the built-in LTS event template, which is used in this example without modifications.                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Test**. The function test result is displayed.
