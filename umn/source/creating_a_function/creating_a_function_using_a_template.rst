:original_name: functiongraph_01_0401.html

.. _functiongraph_01_0401:

Creating a Function Using a Template
====================================

Overview
--------

FunctionGraph provides templates to automatically complete code, and running environment configurations when you create a function, helping you quickly build applications.

Creating a Function
-------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Templates**.
#. On the page that is displayed, select the **FunctionGraph** service, select the **context-class-introduction** template for Python 2.7, and click **Configure**.

   .. note::

      The **context-class-introduction** template for Python 2.7 is used as an example. You can also select other templates.

#. After you select a function template, the built-in code and configurations of the template are automatically loaded. The **Create Function** page is displayed.
#. Set **Function Name** to **context**, select a created agency, retain default values for other parameters, and click **Create Function**.

   .. note::

      If no agency is configured, the following message will be displayed when the function is triggered:

      .. code-block::

         Failed to access other services because no temporary AK, SK, or token has been obtained. Please set an agency.

#. Set the parameters based for your service requirements.

Triggering a Function
---------------------

#. On the **Code** tab page of the **context** function, click **Test** in the upper right corner.
#. In the **Configure Test Event** dialog box, select **Blank Template** and click **Create**.
#. Click **Test**. After the test is complete, view the test result.
