:original_name: functiongraph_01_0201.html

.. _functiongraph_01_0201:

Configuring Initialization
==========================

Overview
--------

The initializer of a function is executed after an instance is started. The instance starts to process requests only after the initializer is executed. The initializer is executed only once during the lifecycle of a function instance.

Scenario
--------

The service logic shared by multiple requests can be implemented in the initializer to reduce the latency. For example, the logic of loading a deep learning model with large specifications or building a connection pool for databases.

Prerequisites
-------------

You have created a function.

Initializing a Function
-----------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Lifecycle** and enable **Initialization**.


   .. figure:: /_static/images/en-us_image_0000001678920797.png
      :alt: **Figure 1** Enabling initialization

      **Figure 1** Enabling initialization

   .. table:: **Table 1** Parameter configuration

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================================================================================================+
      | Initialization                    | Enable initialization if needed.                                                                                                                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Initialization Timeout (s)        | Maximum duration the function can be initialized. Set this parameter if you enable function initialization.                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                   |
      |                                   | The value ranges from 1s to 300s.                                                                                                                                                                                                                                                 |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Initializer                       | You can enable function initialization on the **Configuration** tab page. The initializer must be named in the same way as the handler. For example, for a Node.js or Python function, set an initializer name in the format of *[file name]*.\ *[initialization function name]*. |
      |                                   |                                                                                                                                                                                                                                                                                   |
      |                                   | .. note::                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                   |
      |                                   |    -  This parameter is not required if function initialization is disabled.                                                                                                                                                                                                      |
      |                                   |    -  Ensure that the function initializer and handler are in the same file.                                                                                                                                                                                                      |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  Set the initializer in the same way as the handler. For example, for a Node.js or Python function, set an initializer name in the format of *[file name]*.\ *[initialization function name]*.
      -  For details about the function code configuration, see :ref:`Configuring Code <functiongraph_01_0152>`.
