:original_name: functiongraph_04_0102.html

.. _functiongraph_04_0102:

Creating a Function Using a Template and Executing the Function
===============================================================

FunctionGraph provides multiple templates to automatically complete code and running environment configurations when you create a function, helping you quickly build applications. This section uses **context-class-introduction** as an example.

Prerequisites
-------------

#. Grant the FunctionGraph operation permissions to the user.

   To perform the operations described in this section, ensure that you have the **FunctionGraph FullAccess** permissions, that is, all permissions for FunctionGraph. For more information, see section **"Permissions Management"**.

Step 1: Create a Function
-------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click **Create Function** in the upper right corner and choose **Select template**.

#. Select the template shown in :ref:`Figure 1 <functiongraph_04_0102__fig1910584114193>` and click **Configure**.

   .. _functiongraph_04_0102__fig1910584114193:

   .. figure:: /_static/images/en-us_image_0000001679586377.png
      :alt: **Figure 1** Selecting a template

      **Figure 1** Selecting a template

4. On the displayed page, set function parameters and click **Create Function**.

   -  **Templates**: name of the selected template. To change the template, click **Reselect** on the right.

   -  **Region**: The default value is used. You can select other regions.

      **Regions are geographic areas isolated from each other. Resources are region-specific and cannot be used across regions through internal network connections. For low network latency and quick resource access, select the nearest region.**

   -  **Function Name**: enter **context**.

   -  **Enterprise Project**: The default value is **default**. You can select the created enterprise project.

      Enterprise projects let you manage cloud resources and users by project.

   -  **Agency**: By default, no agency is used. You can select an existing agency.

      Specify an agency if you want to delegate FunctionGraph to access other cloud services, such as LTS and VPC.

   -  **Runtime**: Select a runtime to compile the function. Default: **Python 3.6**. You can select another runtime.


   .. figure:: /_static/images/en-us_image_0000001679586957.png
      :alt: **Figure 2** Setting basic information

      **Figure 2** Setting basic information

Step 2: Test the Function
-------------------------

#. On the function details page, click **Test**. In the displayed dialog box, create a test event.

#. Select **blank-template**, set **Event Name** to **test**, and click **Create**.


   .. figure:: /_static/images/en-us_image_0000001679467421.png
      :alt: **Figure 3** Configuring a test event

      **Figure 3** Configuring a test event

Step 3: View the Execution Result
---------------------------------

Click **Test** and view the execution result on the right.

-  **Function Output**: displays the return result of the function.
-  **Log Output**: displays the execution logs of the function.
-  **Summary**: displays key information of the logs.

.. note::

   A maximum of 2 KB logs can be displayed. For more log information, see :ref:`Querying Function Logs <functiongraph_01_0170>`.
