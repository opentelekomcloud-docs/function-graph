:original_name: functiongraph_01_0180.html

.. _functiongraph_01_0180:

Managing Versions
=================

Overview
--------

FunctionGraph allows you to publish one or more versions throughout the development, test, and production processes to manage your function code. The code and environment variables of each version are saved as a snapshot. After the function code is published, you can modify settings as required.

After a function is created, the default version is latest. Each function has the latest version. After the function code is published, you can modify the version configuration as required.

.. note::

   A version is a snapshot of a function and corresponds to a tag in code. Each version contains the configuration and code of the function. By default, no trigger is bound to a new version. After a version is published, the configuration (such as environment variables) and code of the version cannot be updated, to ensure stability and traceability.

Publishing a Version
--------------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the **Version** tab page, click **Publish new version**.


   .. figure:: /_static/images/en-us_image_0000001305505277.png
      :alt: **Figure 1** Parameters for publishing a new version

      **Figure 1** Parameters for publishing a new version

   -  **Version**: Enter a version number. If no version number is specified, the system automatically generates a version number based on the current date, for example, **v20220510-190658**.
   -  **Description**: Enter a description for the version. This parameter is optional.

#. Click **OK**. The system automatically publishes a version. Then you will be redirected to the new version.

   .. note::

      -  You can publish up to 20 versions for a function.
      -  For a function whose latest version has been configured with reserved instances, the function configuration can be modified. By default, non-latest versions do not have reserved instances.
      -  No disk is attached to a new version created based on latest. Environment variables cannot be set if no trigger has been bound to the version.

Deleting a Version
------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. On the **Version** tab page of the latest version, select the version to delete.


   .. figure:: /_static/images/en-us_image_0000001257625360.png
      :alt: **Figure 2** Deleting a version

      **Figure 2** Deleting a version

   .. note::

      -  The latest version of a function cannot be deleted.
      -  If a function version associated with aliases is deleted, the aliases will also be deleted.

#. Click **OK** to delete the version.

   .. warning::

      Deleting a version will permanently delete the associated code, configuration, alias, and event source mapping, but will not delete logs. Deleted versions cannot be recovered. Exercise caution when performing this operation.
