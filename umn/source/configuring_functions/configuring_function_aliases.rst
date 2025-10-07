:original_name: functiongraph_01_1829.html

.. _functiongraph_01_1829:

Configuring Function Aliases
============================

Overview
--------

An alias points to a specific function version. Create an alias and expose it to clients, for example, bind a trigger to the alias instead of the corresponding version. Then your modification to the version for update or rollback will be imperceptible to the clients. An alias can point to up to two versions with different weights for dark launch.

Constraints
-----------

You can create up to 10 aliases for a function.

Creating an Alias
-----------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the **Aliases** tab page, click **Create Alias**.


   .. figure:: /_static/images/en-us_image_0000002262516774.png
      :alt: **Figure 1** Creating an alias

      **Figure 1** Creating an alias

   -  **Alias**: Enter an alias.
   -  **Version**: Select a version to be associated with the alias.
   -  **Traffic Shifting**: Choose whether to enable traffic shifting. If this function is enabled, you can distribute a specific percentage of traffic to the additional version.

      -  **Additional Version**: Select an additional version to be associated. The latest version cannot be used as an additional version.

      -  **Shift By**: You can shift requests to the additional version by **Percentage** or **Rule**.

         .. table:: **Table 1** Shifting mode

            +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Shift By                          | Description                                                                                                                                                                                                                                                                                           |
            +===================================+=======================================================================================================================================================================================================================================================================================================+
            | Percentage                        | Set a weight to shift the corresponding percentage of requests to the additional version. For example, if you set the percentage to 5%, FunctionGraph will forward 5% of requests to the additional version and the remaining to the main version. The weight value must be an integer from 0 to 100. |
            +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Rule                              | Available only for HTTP functions or functions with APIG triggers. The following parameters need to be configured:                                                                                                                                                                                    |
            |                                   |                                                                                                                                                                                                                                                                                                       |
            |                                   | -  **Rule Type**: Select **All rules met** or **Any rule met** to forward requests with specified headers to the additional version.                                                                                                                                                                  |
            |                                   | -  **Rules**: Set the header rule conditions. For details, see :ref:`Table 2 <functiongraph_01_1829__en-us_topic_0000001486742762_en-us_topic_0000001454100106_table11953714450>`.                                                                                                                    |
            +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

         .. _functiongraph_01_1829__en-us_topic_0000001486742762_en-us_topic_0000001454100106_table11953714450:

         .. table:: **Table 2** Rule list

            +-------------------------------------+-----------------------------------------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Parameter Type                      | Parameter                               | Condition                 | Value                                                                                                                                                                                                           |
            +=====================================+=========================================+===========================+=================================================================================================================================================================================================================+
            | Header, which is unique by default. | Header name, which is case-insensitive. | Options: **=** and **in** | Header value, which is a character string. If the condition is **in**, you can set multiple values and separate them with commas (,), indicating that the traffic can be shifted when one of the values is met. |
            +-------------------------------------+-----------------------------------------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

         For example, if you set **Alias** to **alias1**, **Version** to **version1**, **Additional Version** to **version2**, **Rule Type** to **All rules met**, **Header** to **aaa**, **Condition** to **=**, and **Value** to **123**, the function of **version2** will be executed for the request with function alias **alias1** and header parameter **aaa** with value **123**. If the request header does not meet the rule conditions, the function of **version1** will be executed.

   -  **Description**: Enter a description for the alias.

#. Click **OK**.

Modifying an Alias
------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the **Aliases** tab page of the latest version, select the alias to modify.


   .. figure:: /_static/images/en-us_image_0000002297116837.png
      :alt: **Figure 2** Modifying an alias

      **Figure 2** Modifying an alias

#. Modify the alias information, and click **OK**.

Deleting an Alias
-----------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the **Aliases** tab page of the latest version, select the alias to delete.


   .. figure:: /_static/images/en-us_image_0000002262459860.png
      :alt: **Figure 3** Deleting an alias

      **Figure 3** Deleting an alias

#. Click **OK** to delete the version.
