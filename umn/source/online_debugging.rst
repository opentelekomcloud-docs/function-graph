:original_name: functiongraph_01_0302.html

.. _functiongraph_01_0302:

Online Debugging
================

Precautions
-----------

Event data is passed to the handler of your function as an input. After configuration, event data is persisted for later use. Each function can have a maximum of 10 test events.

Creating a Test Event
---------------------

#. Log in to the FunctionGraph console, and choose **Functions** > **Function List** in the navigation pane.

#. Click the name of the desired function.

#. On the function details page, select a version, and click **Test**.

#. In the **Configure Test Event** dialog box, configure the test event information according to :ref:`Table 1 <functiongraph_01_0302__en-us_topic_0000001252067188_table187784018405>`. The parameter marked with an asterisk (*) is mandatory.

   .. _functiongraph_01_0302__en-us_topic_0000001252067188_table187784018405:

   .. table:: **Table 1** Test event information

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================+
      | Configure Test Event              | You can choose to create a test event or edit an existing one.                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                               |
      |                                   | Use the default option **Create new test event**.                                                                                                                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Template                    | If you select **blank-template**, you can create a test event from scratch.                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                               |
      |                                   | If you select a template, the corresponding test event in the template is automatically loaded. For details about event templates, see :ref:`Table 2 <functiongraph_01_0302__en-us_topic_0000001252067188_table52979501006>`. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Event Name                      | The event name can contain 1 to 25 characters and must start with a letter and end with a letter or digit. Only letters, digits, underscores (_), and hyphens (-) are allowed. For example, **even-123test.**                 |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event data                        | Enter a test event.                                                                                                                                                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _functiongraph_01_0302__en-us_topic_0000001252067188_table52979501006:

   .. table:: **Table 2** Event template description

      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Template Name                                  | Description                                                                              |
      +================================================+==========================================================================================+
      | API Gateway (Dedicated Gateway)                | Simulates a dedicated APIG event to trigger your function.                               |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Cloud Trace Service (CTS)                      | Simulates a CTS event to trigger your function.                                          |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Document Database Service (DDS)                | Simulates a DDS event to trigger your function.                                          |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Data Ingestion Service (DIS)                   | Simulates a DIS event to trigger your function.                                          |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Log Tank Service (LTS)                         | Simulates an LTS event to trigger your function.                                         |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Object Storage Service (OBS)                   | Simulates an OBS event to trigger your function.                                         |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Simple Message Notification (SMN)              | Simulates an SMN event to trigger your function.                                         |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Timer                                          | Simulates a timer event to trigger your function.                                        |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | DMS (for Kafka)                                | Simulates a Kafka event to trigger your function.                                        |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Kafka (OPENSOURCEKAFKA)                        | Simulates an open-source Kafka event to trigger your function.                           |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Distributed Message Service (DMS) for RocketMQ | Simulates a RocketMQ event to trigger your function.                                     |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Blank Template                                 | The event is **{"key": "value"}**, which can be changed based on requirements.           |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Login Security Analysis                        | Serves as an input for the **loginSecurity-realtime-analysis-python** function template. |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Image Classification                           | Serves as an input for the **image-tag** function template.                              |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Pornographic Image Analysis                    | Serves as an input for the **porn-image-analysis** function template.                    |
      +------------------------------------------------+------------------------------------------------------------------------------------------+
      | Speech Recognition                             | Serves as an input for the **voice-analysis** function template.                         |
      +------------------------------------------------+------------------------------------------------------------------------------------------+

#. Click **Create**.

Testing a Function
------------------

After creating a function, you can test it online to check whether it can run properly as expected.

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the name of the desired function.

#. On the displayed function details page, select a version and test event, and click **Test**.


   .. figure:: /_static/images/en-us_image_0000001630402136.png
      :alt: **Figure 1** Selecting a test event

      **Figure 1** Selecting a test event

#. Click **Test**. The function test result is displayed.

   .. note::

      The **Log Output** area displays a maximum of 2 KB logs. To view more logs, see :ref:`Managing Function Logs <functiongraph_01_1834>`.

Modifying a Test Event
----------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the name of the desired function.

#. On the displayed function details page, select a version and click **Configure Test Event**. The **Configure Test Event** dialog box is displayed.

#. In the **Configure Test Event** dialog box, modify the test event information according to :ref:`Table 3 <functiongraph_01_0302__en-us_topic_0000001252067188_table182575018295>`.

   .. _functiongraph_01_0302__en-us_topic_0000001252067188_table182575018295:

   .. table:: **Table 3** Test event information

      ===================== ==============================
      Parameter             Description
      ===================== ==============================
      Create new test event Create a test event.
      Edit saved test event Modify an existing test event.
      Event data            Modify the test event code.
      ===================== ==============================

#. Click **Save**.

Deleting a Test Event
---------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the name of the desired function.

#. On the function details page that is displayed, select a version, as shown in :ref:`Figure 2 <functiongraph_01_0302__en-us_topic_0000001252067188_fig18682352790>`.

   .. _functiongraph_01_0302__en-us_topic_0000001252067188_fig18682352790:

   .. figure:: /_static/images/en-us_image_0000001765546397.png
      :alt: **Figure 2** Selecting a FunctionGraph version

      **Figure 2** Selecting a FunctionGraph version

#. On the **Code** tab page, click **Configure Test Event**. The editing page is displayed, as shown in :ref:`Figure 3 <functiongraph_01_0302__en-us_topic_0000001252067188_fig1279018461619>`.

   .. _functiongraph_01_0302__en-us_topic_0000001252067188_fig1279018461619:

   .. figure:: /_static/images/en-us_image_0000001765392049.png
      :alt: **Figure 3** Selecting Configure Test Event

      **Figure 3** Selecting Configure Test Event

#. On the **Configure Test Event** page, select **Edit saved test event**. In the **Saved Test Events** list on the left, select the event to be deleted and click **Delete**.


   .. figure:: /_static/images/en-us_image_0000001717922440.png
      :alt: **Figure 4** Deleting a test event

      **Figure 4** Deleting a test event

   .. table:: **Table 4** Configuring test event information

      ===================== =========================================
      Parameter             Description
      ===================== =========================================
      Create new test event Select a test event template.
      Edit saved test event Select the test event you want to delete.
      ===================== =========================================
