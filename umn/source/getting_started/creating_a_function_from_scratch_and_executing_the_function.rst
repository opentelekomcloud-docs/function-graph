:original_name: functiongraph_04_0101.html

.. _functiongraph_04_0101:

Creating a Function from Scratch and Executing the Function
===========================================================

This section describes how to quickly create and test a HelloWorld function on the FunctionGraph console.

Prerequisites
-------------

#. Grant the FunctionGraph operation permissions to the user.

   To perform the operations described in this section, ensure that you have the **FunctionGraph FullAccess** permissions, that is, all permissions for FunctionGraph. For more information, see :ref:`Permissions Management <functiongraph_01_0160_0>`.

Step 1: Create a Function
-------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click **Create Function** in the upper right corner and choose **Create from scratch**.

#. On the displayed page, enter **HelloWorld** for **Function Name** and retain the default values for other parameters by referring to :ref:`Figure 1 <functiongraph_04_0101__fig290685013818>`, and click **Create Function**. The following describes the parameters.

   -  **Function Type**: Select **Event Function**.

   -  **Region**: The default value is used. You can select other regions.

      **Regions are geographic areas isolated from each other. Resources are region-specific and cannot be used across regions through internal network connections. For low network latency and quick resource access, select the nearest region.**

   -  **Function Name**: enter **HelloWorld**.

   -  **Enterprise Project**: The default value is **default**. You can select the created enterprise project.

      Enterprise projects let you manage cloud resources and users by project.

   -  **Agency**: By default, no agency is used. You can select an existing agency.

      Specify an agency if you want to delegate FunctionGraph to access other cloud services, such as LTS and VPC.

   -  **Runtime**: Select a runtime to compile the function. Default: **Node.js 16.17**. You can select another runtime.

   -  **Advanced Settings**: **Collect Logs** is disabled by default. If it is enabled, function execution logs will be reported to Log Tank Service (LTS). You will be billed for log management on a pay-per-use basis.

      .. table:: **Table 1** Parameters for configuring Collect Logs

         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                    |
         +===================================+================================================================================================================================+
         | Log Configuration                 | You can select **Auto** or **Custom**.                                                                                         |
         |                                   |                                                                                                                                |
         |                                   | -  **Auto**: Use the default log group and log stream. Log groups prefixed with "functiongraph.log.group" are filtered out.    |
         |                                   | -  **Custom**: Select a custom log group and log stream. Log streams that are in the same enterprise project as your function. |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
         | Log Tag                           | You can use these tags to filter function logs in LTS. You can add 10 more tags.                                               |
         |                                   |                                                                                                                                |
         |                                   | Tag key/value: Enter a maximum of 64 characters. Only digits, letters, underscores (_), and hyphens (-) are allowed.           |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

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

Step 2: Test the Function
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

Step 3: View the Execution Result
---------------------------------

Click **Test** and view the execution result on the right.

-  **Function Output**: displays the return result of the function.

-  **Log Output**: displays the execution logs of the function.

-  **Summary**: displays key information of the logs.


   .. figure:: /_static/images/en-us_image_0000001261803038.png
      :alt: **Figure 3** Viewing the execution result

      **Figure 3** Viewing the execution result

.. note::

   A maximum of 2 KB logs can be displayed. For more log information, see :ref:`Querying Function Logs <functiongraph_01_0170>`.
