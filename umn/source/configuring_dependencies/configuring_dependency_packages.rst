:original_name: functiongraph_01_2119.html

.. _functiongraph_01_2119:

Configuring Dependency Packages
===============================

Overview
--------

Generally, the code of a function consists of public libraries and service logic. The public libraries can be packaged as a dependency and shared among functions, reducing the size of the function code package for easy deployment and update.

FunctionGraph also provides some public dependencies, which are cached internally for quick loading. These dependencies are recommended.

FunctionGraph enables you to manage dependencies in a unified manner. You can upload dependencies from a local path, or through OBS if they are too large, and specify names for them. Dependencies can be iterated. Each dependency can have multiple versions.

For details, see section "How Do I Create Function Dependencies?"

.. note::

   -  The name of each file in the dependency package cannot end with a tilde (~).
   -  A dependency package can contain up to 30,000 files.
   -  If your function uses a large private dependency, increase the execution timeout by choosing **Configuration** > **Basic Settings** on the function details page.

Creating a Dependency
---------------------

#. Log in to the FunctionGraph console, and choose **Functions** > **Dependencies** in the navigation pane.
#. Click **Create Dependency**.
#. Set the following parameters:

   .. table:: **Table 1** Dependency configuration parameters

      +-----------------------------------+------------------------------------------------------------+
      | Parameter                         | Description                                                |
      +===================================+============================================================+
      | Name                              | Dependency name.                                           |
      +-----------------------------------+------------------------------------------------------------+
      | Code Entry Mode                   | You can upload a ZIP file or upload a file from OBS.       |
      |                                   |                                                            |
      |                                   | -  **Upload ZIP**: Click **Select File** to upload one.    |
      |                                   | -  **Upload from OBS**: Specify an OBS link URL.           |
      +-----------------------------------+------------------------------------------------------------+
      | Runtime                           | Select a runtime.                                          |
      +-----------------------------------+------------------------------------------------------------+
      | Description                       | Description of the dependency. This parameter is optional. |
      +-----------------------------------+------------------------------------------------------------+

#. Click **OK**. By default, a new dependency is version **1**.
#. Click the dependency name, and view all versions and related information on the displayed page. Each dependency can have multiple versions.

   -  To create a dependency version, click **Create Version** in the upper right corner of the page.

   -  To view the address of a version, click the version.

   -  To delete a version, click the delete icon in the same row.


      .. figure:: /_static/images/en-us_image_0000001709193044.png
         :alt: **Figure 1** Deleting a dependency version

         **Figure 1** Deleting a dependency version

Configuring Dependencies for a Function
---------------------------------------

#. Return to the FunctionGraph console, and choose **Functions** > **Function List** in the navigation pane.
#. Click the name of the desired function.
#. On the displayed function details page, click the **Code** tab, click **Add** in the **Dependencies** area.
#. On the displayed **Select Dependency** dialog box, select dependencies and click **OK**.

   .. table:: **Table 2** Dependency configuration

      ========= ===============================================
      Parameter Description
      ========= ===============================================
      Runtime   Runtime of this function. It cannot be changed.
      Type      Add a **Public** or **Private** dependency.
      Name      Select a dependency.
      Version   Select a version to be added.
      ========= ===============================================

   .. note::

      -  You can add a maximum of 20 dependencies for a function.
      -  Except your private dependencies, FunctionGraph provides some public dependencies, which you can choose when creating a function.

Deleting a Dependency
---------------------

To delete a dependency, delete all of its versions.

#. Return to the FunctionGraph console, and choose **Functions** > **Dependencies** in the navigation pane.

#. Click the name of the target dependency to go to the **Versions** page.

#. Click the delete icon in the row of a version. Repeat this operation if the dependency has multiple versions.


   .. figure:: /_static/images/en-us_image_0000001757072025.png
      :alt: **Figure 2** Deleting a dependency version

      **Figure 2** Deleting a dependency version

   .. note::

      Dependencies referenced by functions cannot be deleted.
