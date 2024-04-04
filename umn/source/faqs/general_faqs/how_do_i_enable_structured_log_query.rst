:original_name: functiongraph_03_0884.html

.. _functiongraph_03_0884:

How Do I Enable Structured Log Query?
=====================================

Scenario
--------

To check the status of asynchronous invocation requests, view the records by choosing **Configuration** > **Configure Async Notification** on the function details page, as shown in :ref:`Figure 1 <functiongraph_03_0884__fig1760293323818>`.

.. _functiongraph_03_0884__fig1760293323818:

.. figure:: /_static/images/en-us_image_0000001680007009.png
   :alt: **Figure 1** Asynchronous invocation records

   **Figure 1** Asynchronous invocation records

Prerequisites
-------------

You have enabled asynchronous invocation status persistence.

Procedure
---------

#. Contact customer service to add your account to the whitelist of this feature.

#. On the **Configure Async Notification** page, click **Enable LTS**.

#. Click **Edit** next to **Asynchronous Notification Policy**, and enable **Asynchronous Invocation Status Persistence**, as shown in :ref:`Figure 2 <functiongraph_03_0884__fig113751514015>` and :ref:`Figure 3 <functiongraph_03_0884__fig94071959424>`.

   .. _functiongraph_03_0884__fig113751514015:

   .. figure:: /_static/images/en-us_image_0000001680495569.png
      :alt: **Figure 2** Configuring asynchronous notification policy

      **Figure 2** Configuring asynchronous notification policy

   .. _functiongraph_03_0884__fig94071959424:

   .. figure:: /_static/images/en-us_image_0000001631816488.png
      :alt: **Figure 3** Enabling asynchronous invocation status persistence

      **Figure 3** Enabling asynchronous invocation status persistence

#. Configure structured query on the LTS console.

   a. On the function details page, view the log group and log stream. Press **F12**, choose **Network**, enter filter **async-status-log-detail**, and obtain the log group ID and log stream ID, as shown in :ref:`Figure 4 <functiongraph_03_0884__fig5665103123612>`.

      .. _functiongraph_03_0884__fig5665103123612:

      .. figure:: /_static/images/en-us_image_0000001560650613.png
         :alt: **Figure 4** Obtaining log group ID and log stream ID

         **Figure 4** Obtaining log group ID and log stream ID

   b. On the LTS console, locate the log group and log stream by their IDs.

   c. On the log stream details page, click the gear icon in the upper right.

   d. Configure log structuring.

   e. Click **Intelligent Extraction**.

   f. Click |image1| to modify the field definition as follows:

      #. Change **field1** to **function_urn** and its type to **string**.
      #. Change **field2** to **request_id** and its type to **string**.
      #. Change **field3** to **seq_status** and its type to **long**.
      #. Change **field4** to **operation_timestamp** and its type to **long**.
      #. Change **field5** to **error_code** and its type to **long**.
      #. Change **field6** to **error_message** and its type to **string**.

      Enable **Quick Analysis**.

   g. Click **Save**.

.. |image1| image:: /_static/images/en-us_image_0000001509972086.png
