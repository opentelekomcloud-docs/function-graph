:original_name: functiongraph_01_0320.html

.. _functiongraph_01_0320:

Managing Functions
==================

Overview
--------

Function is a combination of code, runtime, resources, and settings required to achieve a specific purpose. It is the minimum unit that can run independently. A function can be triggered by triggers and automatically schedule required resources and environments to achieve expected results.

Exporting a Function
--------------------

You can export the functions that you created.

#. Log in to the FunctionGraph console, and choose **Functions** > **Function List** in the navigation pane.
#. Click a function name.
#. On the displayed function details page, choose **Operation** > **Export Function** in the upper right corner.

   .. note::

      -  A user can export only one function at a time.
      -  The exported function resource package cannot exceed 50 MB.
      -  The name of the exported function resource package is in the format of *function name*\ +\ *MD5 value of function code*.zip.
      -  The exported function resource package does not include alias information.
      -  If a function is disabled or enabled, all versions of the function will be disabled or enabled.

Disabling a Function
--------------------

Disabled functions can no longer be executed.

#. Return to the FunctionGraph console, and choose **Functions** > **Function List** in the navigation pane.
#. Click the name of the function you want to disable.
#. On the displayed function details page, click **Disable Function** in the upper right corner.
#. On the displayed page, click **Yes**. The function is disabled.

   .. note::

      -  Only functions of the latest version can be disabled.
      -  Versions published based on the disabled latest version of a function are also disabled and can never be enabled.
      -  After disabling a function, you can modify its code but cannot execute the function.

Enabling a Function
-------------------

Disabled functions can be enabled again as required.

#. Return to the FunctionGraph console, and choose **Functions** > **Function List** in the navigation pane.
#. Click the name of the function you want to enable.
#. On the displayed function details page, click **Enable Function** in the upper right corner.

Deleting a Function
-------------------

You can delete unused functions to release resources.

#. Return to the FunctionGraph console, and choose **Functions** > **Function List** in the navigation pane.
#. In the **Function List**, locate the row that contains the target function and click **Delete** in the operation column. In the displayed dialog box, enter **DELETE** and click **OK**.
