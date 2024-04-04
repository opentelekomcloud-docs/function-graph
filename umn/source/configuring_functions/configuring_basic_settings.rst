:original_name: functiongraph_01_1828.html

.. _functiongraph_01_1828:

Configuring Basic Settings
==========================

Introduction
------------

After a function is created, **Memory (MB)**, **Handler**, and **Execution Timeout (s)** are automatically set based on your runtime. If needed, modify them based on this section.

Prerequisites
-------------

You have created a function.

Procedure
---------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Basic Settings** and configure parameters based on :ref:`Table 1 <functiongraph_01_1828__en-us_topic_0000001252083600_table17352446184813>`. Parameters marked with an asterisk (*) are mandatory.

   .. _functiongraph_01_1828__en-us_topic_0000001252083600_table17352446184813:

   .. table:: **Table 1** Basic settings

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================+
      | App                               | After a function is created, it is automatically categorized into the **default** app and cannot be switched to other apps.                                                       |
      |                                   |                                                                                                                                                                                   |
      |                                   | .. important::                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                   |
      |                                   |    NOTICE:                                                                                                                                                                        |
      |                                   |    An app acts like a folder. In the future, functions will be managed by label for better experience.                                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Handler                         | -  For a Node.js, Python, or PHP function, the handler must be named in the format of *[file name]*.\ *[function name]*, which must contain a period (.).                         |
      |                                   |                                                                                                                                                                                   |
      |                                   |    Example: **myfunction.handler**                                                                                                                                                |
      |                                   |                                                                                                                                                                                   |
      |                                   | -  For a Java function, the handler must be named in the format of *[package name]*.\ *[class name]*.\ *[execution function name]*.                                               |
      |                                   |                                                                                                                                                                                   |
      |                                   |    Example: **com.xxxxx.exp.Myfunction.myHandler**                                                                                                                                |
      |                                   |                                                                                                                                                                                   |
      |                                   | -  For a Go function, the handler name must be the same as the executable file name in the uploaded code package.                                                                 |
      |                                   |                                                                                                                                                                                   |
      |                                   |    Example: If the executable file is **handler**, set this parameter to **handler**.                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Enterprise Project              | Select a created enterprise project and add the function to it. By default, **default** is selected.                                                                              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Execution Timeout (s)           | Maximum duration the function can be executed. You can set this parameter on the **Configuration** tab page. If the execution takes longer than 90s, use asynchronous invocation. |
      |                                   |                                                                                                                                                                                   |
      |                                   | The value ranges from 3s to 259,200s.                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Memory (MB)                       | Memory of a function instance. Options: 128, 256, 512, 768, 1024, 1280, 1536, 1792, 2048, 2560, 3072, 3584, 4096, 8192, 10,240.                                                   |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the function, which cannot exceed 512 characters.                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Save**.
