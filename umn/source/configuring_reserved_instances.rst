:original_name: functiongraph_01_1837.html

.. _functiongraph_01_1837:

Configuring Reserved Instances
==============================

Introduction
------------

FunctionGraph provides on-demand and reserved instances.

-  On-demand instances are created and released by FunctionGraph based on actual function usage. When receiving requests to call functions, FunctionGraph automatically allocates execution resources to the requests.

-  Reserved instances can be created and released by you as required. After you create reserved instances for a function, FunctionGraph preferentially forwards requests to the reserved instances. If the number of requests exceeds the processing capability of the reserved instances, FunctionGraph will forward the excessive requests to on-demand instances and automatically allocates execution resources to these requests.

   After reserved instances are created for a function, the code, dependencies, and initializer of the function are automatically loaded. Reserved instances are always alive in the execution environment, eliminating the influence of cold starts on your services. (Do not execute one-time services using the initializer of reserved instances.)

   You can configure :ref:`a fixed number of reserved instances <functiongraph_01_1837__en-us_topic_0000001356130857_en-us_topic_0241013219_section1064812184016>` or :ref:`scheduled scaling policies <functiongraph_01_1837__en-us_topic_0000001356130857_en-us_topic_0241013219_section516211925918>`.

.. _functiongraph_01_1837__en-us_topic_0000001356130857_en-us_topic_0241013219_section1064812184016:

Configuring a Fixed Number of Reserved Instances
------------------------------------------------

Ensure that the function for which you want to create reserved instances already exists on the FunctionGraph console.

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the target function to go to the details page.

#. Choose **Configuration** > **Concurrency**, and click **Add**.


   .. figure:: /_static/images/en-us_image_0000001356014693.png
      :alt: **Figure 1** Clicking Add

      **Figure 1** Clicking Add

#. Set parameters by referring to :ref:`Table 1 <functiongraph_01_1837__en-us_topic_0000001356130857_table133267395252>`.

   You can create a specified number of reserved instances for a function version or alias. This number cannot exceed the maximum number of requests per instance or the maximum number of instances per function.


   .. figure:: /_static/images/en-us_image_0000001631298906.png
      :alt: **Figure 2** Basic settings

      **Figure 2** Basic settings

   .. _functiongraph_01_1837__en-us_topic_0000001356130857_table133267395252:

   .. table:: **Table 1** Basic settings

      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter          | Description                                                                                                                                                                                            |
      +====================+========================================================================================================================================================================================================+
      | Function Name      | Name of the current function.                                                                                                                                                                          |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type               | Select **Version** or **Aliases**.                                                                                                                                                                     |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Version            | Set this parameter when you select **Version** for **Type**.                                                                                                                                           |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Alias              | Set this parameter when you select **Aliases** for **Type**.                                                                                                                                           |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Reserved Instances | Minimum number of instances. Max.: **1000**. FunctionGraph reserves the specified number of instances for the function. These instances will always run unless you change **Min. Instances** to **0**. |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Idle Mode          | This mode saves costs as CPU resources are not used when reserved instances are not invoked.                                                                                                           |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  Reserved instances cannot be configured for both a function alias and the corresponding version. For example, if the alias of the latest version is 1.0 and reserved instances have been configured for this version, no more instances can be configured for alias 1.0.
      -  After the idle mode is enabled, reserved instances are initialized and the mode change needs some time to take effect. You will still be billed at the price of reserved instances for non-idle mode in this period.
      -  If the function concurrency is greater than the number of reserved instances, the excess requests will be allocated to on-demand instances, which involve a cold start.

#. Click **OK**. The new policy is displayed in the reserved instance policy list.


   .. figure:: /_static/images/en-us_image_0000001302775168.png
      :alt: **Figure 3** Policy list

      **Figure 3** Policy list

.. _functiongraph_01_1837__en-us_topic_0000001356130857_en-us_topic_0241013219_section516211925918:

Configuring a Scheduled Scaling Policy
--------------------------------------

Configure the number of reserved instances that will run in a specified period and a cron expression. During this period, FunctionGraph adjusts the number of reserved instances based on the cron expression. When the period expires, the fixed number of instances will be reserved.

#. Configure the basic settings by referring to :ref:`Table 1 <functiongraph_01_1837__en-us_topic_0000001356130857_table133267395252>`, and then click **Add Policy**.


   .. figure:: /_static/images/en-us_image_0000001631299366.png
      :alt: **Figure 4** Clicking Add Policy

      **Figure 4** Clicking Add Policy

#. Set parameters by referring to :ref:`Table 2 <functiongraph_01_1837__en-us_topic_0000001356130857_table8405162215410>`.


   .. figure:: /_static/images/en-us_image_0000001303254576.png
      :alt: **Figure 5** Adding a policy

      **Figure 5** Adding a policy

   .. _functiongraph_01_1837__en-us_topic_0000001356130857_table8405162215410:

   .. table:: **Table 2** Scheduled scaling policy parameters

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                      |
      +===================================+==================================================================================================================================================+
      | Policy Name                       | Policy name.                                                                                                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cron Expression (UTC)             | Set this parameter by referring to :ref:`Cron Expressions for a Function Timer Trigger <functiongraph_01_0908>`.                                 |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Validity                          | Local time when the cron expression is effective.                                                                                                |
      |                                   |                                                                                                                                                  |
      |                                   | The scheduled scaling policy is effective only during this validity period. In other time, the **Min. Instances** in the basic settings is used. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Reserved Instances                | The number of reserved instances to be created when the policy is effective.                                                                     |
      |                                   |                                                                                                                                                  |
      |                                   | Set a number that meets your service requirements.                                                                                               |
      |                                   |                                                                                                                                                  |
      |                                   | .. note::                                                                                                                                        |
      |                                   |                                                                                                                                                  |
      |                                   |    The number must be greater than or equal to the **Min. Instances** in the basic settings.                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. The new policy is displayed in the reserved instance policy list.


   .. figure:: /_static/images/en-us_image_0000001356134133.png
      :alt: **Figure 6** Policy list

      **Figure 6** Policy list

#. To modify the reserved instance policy, click **Edit** in the **Operation** column. Then modify or add scheduled scaling policies.

#. To delete a reserved instance policy under a function version or alias, click **Delete** in the **Operation** column.

#. To view concurrent instances, click a quantifier in the reserved instance policy list, and click a scheduled scaling policy name.

   .. note::

      Multiple scheduled policies can be configured. For example, the number of reserved instances at 08:00 and 21:00 is updated to 100 and 10 respectively.
