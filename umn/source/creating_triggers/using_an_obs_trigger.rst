:original_name: functiongraph_01_0205.html

.. _functiongraph_01_0205:

Using an OBS Trigger
====================

For details about the OBS event source, see section "Supported Event Sources".

Constraints
-----------

-  Buckets created in different regions are different. Ensure that the OBS bucket and function are in the same region.

Prerequisites
-------------

Before creating a trigger, ensure that you have prepared the following:

-  You have created a function. For details, see :ref:`Creating a Function from Scratch <functiongraph_01_0153>`.
-  You have created an OBS bucket, for example, **obs_cff**. For details, see `Creating a Bucket <https://docs.otc.t-systems.com/object-storage-service/umn/obs_console_operation_guide/getting_started/creating_a_bucket.html#obs-03-0306>`__.

Creating an OBS Trigger
-----------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Triggers** and click **Create Trigger**.


   .. figure:: /_static/images/en-us_image_0000001679340817.png
      :alt: **Figure 1** Creating a trigger

      **Figure 1** Creating a trigger

#. Set the following parameters:

   -  **Trigger Type**: Select **Object Storage Service (OBS)**.
   -  **Bucket Name**: Specify the OBS bucket to be used as an event source, for example, **obs-cff**.
   -  **Events**: Select events that will trigger the function. In this example, select **Put**, **Post**, and **Delete**. When files in the **obs_cff** bucket are updated, uploaded, or deleted, the function is triggered.
   -  **Event Notification Name**: Specify the name of the event notification to be sent by SMN when an event occurs.
   -  **Prefix**: Enter a keyword for limiting notifications to those about objects whose names start with the matching characters. This limit can be used to filter the names of OBS objects.
   -  **Suffix**: Enter a keyword for limiting notifications to those about objects whose names end with the matching characters. This limit can be used to filter the names of OBS objects.

#. Click **OK**.

Triggering a Function
---------------------

On the OBS console, upload an image ZIP package to the **obs-cff** bucket. For details, see `Uploading a File <https://docs.otc.t-systems.com/object-storage-service/umn/obs_console_operation_guide/managing_objects/uploading_an_object.html#en-us-topic-0045853663>`__.

.. note::

   After the ZIP package is uploaded to the **obs-cff** bucket, the **HelloWorld** function is triggered.

Viewing the Execution Result
----------------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. Click a function to go to the function details page.
#. Choose **Monitoring** > **Logs** to query function running logs.
