:original_name: functiongraph_01_0207.html

.. _functiongraph_01_0207:

Using a Timer Trigger
=====================

Prerequisites
-------------

You have created a function. For details, see :ref:`Creating a Function from Scratch <functiongraph_01_0153>`.

Creating a Timer Trigger
------------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Triggers** and click **Create Trigger**.


   .. figure:: /_static/images/en-us_image_0000001679340817.png
      :alt: **Figure 1** Creating a trigger

      **Figure 1** Creating a trigger

#. Set the following parameters:

   -  **Trigger Type**: Select **Timer**.
   -  **Timer Name**: Enter a timer name, for example, **Timer**.
   -  **Rule**: Set a fixed rate or a cron expression.

      -  **Fixed rate**: The function is triggered at a fixed rate of minutes, hours, or days. You can set a fixed rate from 1 to 60 minutes, 1 to 24 hours, or 1 to 30 days.
      -  **Cron expression**: The function is triggered based on a complex rule. For example, you can set a function to be executed at 08:30:00 from Monday to Friday. For more information, see :ref:`Cron Expressions for a Function Timer Trigger <functiongraph_01_0908>`.

   -  **Enable Trigger**: Choose whether to enable the timer trigger.
   -  **Additional Information**: The additional information you configure will be put into the **user_event** field of the timer event source.

#. Click **OK**.

Viewing the Execution Result
----------------------------

After the timer trigger is created, the function is executed every 1 minute. To view the function running logs, perform the following steps:

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. Click a function to go to the function details page.
#. Choose **Monitoring** > **Logs** to query function running logs.
