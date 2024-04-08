:original_name: functiongraph_04_0102.html

.. _functiongraph_04_0102:

Creating a Function Using a Template
====================================

Introduction
------------

FunctionGraph provides templates to automatically complete code and running environment configurations when you create a function, helping you quickly build applications.

Step 1: Prepare the Environment
-------------------------------

To perform the operations described in this section, ensure that you have the **FunctionGraph FullAccess** permissions, that is, all permissions for FunctionGraph. For more information, see section "Permissions Management".

Step 2: Create a Function
-------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click **Create Function** in the upper right corner and choose **Select template**.

#. Select the template shown in :ref:`Figure 1 <functiongraph_04_0102__fig1910584114193>` and click **Configure**.

   .. _functiongraph_04_0102__fig1910584114193:

   .. figure:: /_static/images/en-us_image_0000001679586377.png
      :alt: **Figure 1** Selecting a template

      **Figure 1** Selecting a template

4. Set **Function Name** to **context**, select any agency from the **Agency** drop-down list, retain default values for other parameters, and click **Create Function**.

   .. note::

      -  If no agency is configured, the following message will be displayed when the function is triggered:

         .. code-block::

            Failed to access other services because no temporary AK, SK, or token has been obtained. Please set an agency.


   .. figure:: /_static/images/en-us_image_0000001679586957.png
      :alt: **Figure 2** Setting basic information

      **Figure 2** Setting basic information

Step 3: Test the Function
-------------------------

#. On the function details page, click **Test**. In the displayed dialog box, create a test event.

#. Select **blank-template**, set **Event Name** to **test**, and click **Create**.


   .. figure:: /_static/images/en-us_image_0000001679467421.png
      :alt: **Figure 3** Configuring a test event

      **Figure 3** Configuring a test event

Step 4: View the Execution Result
---------------------------------

Click **Test** and view the execution result on the right.

-  **Function Output**: displays the return result of the function.
-  **Log Output**: displays the execution logs of the function.
-  **Summary**: displays key information of the logs.

.. note::

   A maximum of 2 KB logs can be displayed. For more log information, see section "Querying Function Logs".

Step 5: View Monitoring Metrics
-------------------------------

On the function details page, click the **Monitoring** tab.

-  On the **Monitoring** tab page, choose **Metrics**, and select a time range (such as 5 minutes, 15 minutes, or 1 hour) to query the function.
-  The following metrics are displayed: invocations, errors, duration (including the maximum, average, and minimum durations), and throttles.

Step 6: Delete a Function
-------------------------

#. On the function details page, choose **Operation** > **Delete Function** in the upper right corner.
#. In the confirmation dialog box, enter **DELETE** and click **OK** to release resources in a timely manner.
