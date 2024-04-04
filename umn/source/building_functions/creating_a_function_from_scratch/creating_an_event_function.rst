:original_name: functiongraph_01_1441.html

.. _functiongraph_01_1441:

Creating an Event Function
==========================

Overview
--------

A function is customized code for processing events. You can create a function from scratch and configure the function based on site requirements.

FunctionGraph manages the compute resources required for function execution. After editing code for your function, configure compute resources on the FunctionGraph console.

You can create a function from scratch or by using :ref:`a template <functiongraph_01_0401>` or :ref:`container image <functiongraph_01_1047>`.

.. note::

   When creating a function from scratch, configure the basic and code information based on :ref:`Table 1 <functiongraph_01_1441__en-us_topic_0000001251907924_table11741142114328>`. The parameters marked with an asterisk (``*``) are mandatory.

   Each FunctionGraph function runs in its own environment and has its own resources and file system.

Prerequisites
-------------

#. You must be familiar with the programming languages supported by FunctionGraph. For details, see :ref:`Supported Programming Languages <functiongraph_01_0151>`.
#. You have created a deployment package. For details, see :ref:`Creating a Deployment Package <functiongraph_01_0152>`.
#. (Optional) You have created an agency. For details, see :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.

Procedure
---------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. On the **Function List** page, click **Create Function** in the upper right corner.

#. Click **Create from scratch** and configure the function information by referring to :ref:`Table 1 <functiongraph_01_1441__en-us_topic_0000001251907924_table11741142114328>`. The parameters marked with an asterisk (*) are mandatory.


   .. figure:: /_static/images/en-us_image_0000001678732229.png
      :alt: **Figure 1** Creating a function from scratch

      **Figure 1** Creating a function from scratch

   .. _functiongraph_01_1441__en-us_topic_0000001251907924_table11741142114328:

   .. table:: **Table 1** Basic information

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================+
      | \* Function Type                  | -  Event functions: triggered by triggers.                                                                                                                                                                |
      |                                   | -  HTTP functions: triggered once HTTP requests are sent to specific URLs.                                                                                                                                |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    .. note::                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                           |
      |                                   |       -  HTTP functions do not distinguish between programming languages. The handler must be set in the **bootstrap** file. You can directly write the startup command, and allow access over port 8000. |
      |                                   |       -  HTTP functions support APIG and APIC triggers only.                                                                                                                                              |
      |                                   |       -  For details about how to use HTTP functions, see :ref:`Creating an HTTP Function <functiongraph_01_1442>`.                                                                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Region                          | Select a region where you will deploy your code.                                                                                                                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Function Name                   | Name of the function, which must meet the following requirements:                                                                                                                                         |
      |                                   |                                                                                                                                                                                                           |
      |                                   | -  Consists of 1 to 60 characters, and can contain letters, digits, hyphens (-), and underscores (_).                                                                                                     |
      |                                   | -  Starts with a letter and ends with a letter or digit.                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agency                            | An agency is required if FunctionGraph accesses other cloud services. For details on how to create an agency, see :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.                          |
      |                                   |                                                                                                                                                                                                           |
      |                                   | No agency is required if FunctionGraph does not access any cloud services.                                                                                                                                |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Enterprise Project              | Select a created enterprise project and add the function to it. By default, **default** is selected.                                                                                                      |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Runtime                           | Select a runtime to compile the function.                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                           |
      |                                   | .. important::                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                           |
      |                                   |    NOTICE:                                                                                                                                                                                                |
      |                                   |    CloudIDE supports Node.js and Python only.                                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create Function**. On the displayed **Code** tab page, continue to configure the code.

Configuring Code
----------------

#. You can deploy the code based on the runtime you select. For details, see :ref:`Creating a Deployment Package <functiongraph_01_0152>`. After the deployment is complete, click **Deploy**.

   As shown in the following example, to deploy code in Node.js 10.16, you can edit code inline, upload a local ZIP file, or upload a ZIP file from OBS.


   .. figure:: /_static/images/en-us_image_0000001387236998.png
      :alt: **Figure 2** Deploying code

      **Figure 2** Deploying code


   .. figure:: /_static/images/en-us_image_0000001630136520.png
      :alt: **Figure 3** Deploying code

      **Figure 3** Deploying code

#. You can modify the code and click **Deploy** to deploy the code again.

Viewing Code Information
------------------------

#. View code attributes.

   Code attributes show the code size and the time the code was modified.


   .. figure:: /_static/images/en-us_image_0000001629978216.png
      :alt: **Figure 4** Viewing code attributes

      **Figure 4** Viewing code attributes

#. View basic information.

   :ref:`Configuring Basic Settings <functiongraph_01_1828>` shows the default memory and execution timeout in each runtime. You can click **Edit** to switch to the **Basic Settings** page and modify **Handler**, **Memory (MB)**, and **Execution Timeout (s)** as required. For details, see :ref:`Figure 5 <functiongraph_01_1441__en-us_topic_0000001251907924_fig11561614250>`.

   .. _functiongraph_01_1441__en-us_topic_0000001251907924_fig11561614250:

   .. figure:: /_static/images/en-us_image_0000001678858881.png
      :alt: **Figure 5** Editing basic information

      **Figure 5** Editing basic information

   .. important::

      Once a function is created, the runtime cannot be changed.

   .. table:: **Table 2** Default basic information of each runtime

      +-----------------------------------+-----------------------------------------+
      | Runtime                           | Default Basic Information               |
      +===================================+=========================================+
      | Java                              | Memory (MB): 512                        |
      |                                   |                                         |
      |                                   | Handler: com.demo.TriggerTests.apigTest |
      |                                   |                                         |
      |                                   | Execution Timeout (s): 15               |
      +-----------------------------------+-----------------------------------------+
      | Node.js                           | Memory (MB): 128                        |
      |                                   |                                         |
      |                                   | Handler: index.handler                  |
      |                                   |                                         |
      |                                   | Execution Timeout (s): 3                |
      +-----------------------------------+-----------------------------------------+
      | Custom                            | Memory (MB): 128                        |
      |                                   |                                         |
      |                                   | Handler: bootstrap                      |
      |                                   |                                         |
      |                                   | Execution Timeout (s): 3                |
      +-----------------------------------+-----------------------------------------+
      | Python                            | Memory (MB): 128                        |
      |                                   |                                         |
      |                                   | Handler: index.handler                  |
      |                                   |                                         |
      |                                   | Execution Timeout (s): 3                |
      +-----------------------------------+-----------------------------------------+
      | Go 1.x                            | Memory (MB): 128                        |
      |                                   |                                         |
      |                                   | Handler: handler                        |
      |                                   |                                         |
      |                                   | Execution Timeout (s): 3                |
      +-----------------------------------+-----------------------------------------+
