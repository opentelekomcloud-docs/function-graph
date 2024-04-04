:original_name: functiongraph_04_0101.html

.. _functiongraph_04_0101:

Creating a Function from Scratch
================================

Introduction
------------

This section describes how to quickly create and test a HelloWorld function on the FunctionGraph console.

Step 1: Prepare the Environment
-------------------------------

To perform the operations described in this section, ensure that you have the **FunctionGraph FullAccess** permissions, that is, all permissions for FunctionGraph. For more information, see section "Permissions Management".

Step 2: Create a Function
-------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. Click **Create Function** in the upper right corner and choose **Create from scratch**.
#. On the displayed page, set **Function Name** to **HelloWorld**, retain the default values for other parameters, and click **Create Function**. For details, see :ref:`Figure 1 <functiongraph_04_0101__fig290685013818>`.

.. _functiongraph_04_0101__fig290685013818:

.. figure:: /_static/images/en-us_image_0000001679464913.png
   :alt: **Figure 1** Configuring basic information

   **Figure 1** Configuring basic information

4. Configure the code source, copy the following code to the code window, and click **Deploy**.

   The sample code enables you to obtain test events and print test event information.

   .. code-block::

      exports.handler = function (event, context, callback) {
          const error = null;
          const output = `Hello message: ${JSON.stringify(event)}`;
          callback(error, output);
      }

Step 3: Test the Function
-------------------------

#. On the function details page, click **Test**. In the displayed dialog box, create a test event.

#. Select **blank-template**, set **Event Name** to **test**, modify the test event as follows, and click **Create**.

   .. code-block::

      {
          "hello": "function"
      }


   .. figure:: /_static/images/en-us_image_0000001631465770.png
      :alt: **Figure 2** Configuring a test event

      **Figure 2** Configuring a test event

Step 4: View the Execution Result
---------------------------------

Click **Test** and view the execution result on the right.

-  **Function Output**: displays the return result of the function.

-  **Log Output**: displays the execution logs of the function.

-  **Summary**: displays key information of the logs.


   .. figure:: /_static/images/en-us_image_0000001261803038.png
      :alt: **Figure 3** Viewing the execution result

      **Figure 3** Viewing the execution result

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
