:original_name: functiongraph_01_0418.html

.. _functiongraph_01_0418:

Configuring Class Isolation and Pre-stop for Java Functions
===========================================================

Class isolation is used to load your code and dependencies using an independent class loader if they conflict with the runtime dependencies.

Pre-stop is used to call a callback function before FunctionGraph stops the current function instance.

Constraints
-----------

Only Java functions can be configured with class isolation and pre-stop.

Configuring Class Isolation for a Java Function
-----------------------------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. Click the name of a function.
#. Choose **Configuration** > **Advanced Settings**.
#. Enable **Class Isolation** and click **Save**.

Configuring Pre-stop for a Java Function
----------------------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. Click the name of a function.
#. On the **Configuration** tab, click **Lifecycle**.
#. Enable **Pre-stop** and set the related parameters.

   .. table:: **Table 1** Pre-stop configuration

      +----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter            | Description                                                                                                                                               |
      +======================+===========================================================================================================================================================+
      | Pre-stop Timeout (s) | Timeout for executing the callback function before the current function instance is stopped. The value is an integer ranging from 1 to 90.                |
      +----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Pre-stop Handler     | Handler of the callback function, which can contain a maximum of 128 characters in the format of "[package name].[class name].[execution function name]". |
      +----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Save**.
