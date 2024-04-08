:original_name: functiongraph_01_1829.html

.. _functiongraph_01_1829:

Managing Aliases
================

Overview
--------

An alias points to a specific function version. Create an alias and expose it to clients, for example, bind a trigger to the alias instead of the corresponding version. Then your modification to the version for update or rollback will be imperceptible to the clients. An alias can point to up to two versions with different weights for dark launch.

Creating an Alias
-----------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the **Aliases** tab page, click **Create Alias**.


   .. figure:: /_static/images/en-us_image_0000001679192985.png
      :alt: **Figure 1** Creating an alias

      **Figure 1** Creating an alias

   -  **Alias**: Enter an alias.
   -  **Version**: Select a version to be associated with the alias.
   -  **Traffic Shifting**: Choose whether to enable traffic shifting. If this function is enabled, you can distribute a specific percentage of traffic to the additional version.
   -  **Additional Version**: Select an additional version to be associated. The latest version cannot be used as an additional version.
   -  **Weight**: Enter an integer from 0 to 100.
   -  **Description**: Enter a description for the alias.

#. Click **OK**.

   .. note::

      You can create up to 10 aliases for a function.

Modifying an Alias
------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the **Aliases** tab page of the latest version, select the alias to modify.


   .. figure:: /_static/images/en-us_image_0000001453780466.png
      :alt: **Figure 2** Modifying an alias

      **Figure 2** Modifying an alias

#. Modify the alias information, and click **OK**.

Deleting an Alias
-----------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the **Aliases** tab page of the latest version, select the alias to delete.


   .. figure:: /_static/images/en-us_image_0000001454100150.png
      :alt: **Figure 3** Deleting an alias

      **Figure 3** Deleting an alias

#. Click **OK** to delete the version.
