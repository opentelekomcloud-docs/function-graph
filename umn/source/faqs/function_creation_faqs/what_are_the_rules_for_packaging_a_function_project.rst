:original_name: functiongraph_03_0280.html

.. _functiongraph_03_0280:

What Are the Rules for Packaging a Function Project?
====================================================

In addition to inline code editing, you can create a function by uploading a ZIP or JAR file, or uploading a ZIP file from OBS. For details, see :ref:`Packaging Rules <functiongraph_03_0280__section1314181003718>` and :ref:`Example ZIP Project Packages <functiongraph_03_0280__section237534633713>`.

.. _functiongraph_03_0280__section1314181003718:

Packaging Rules
---------------

In addition to inline code editing, you can create a function by uploading a local ZIP file or JAR file, or uploading a ZIP file from Object Storage Service (OBS). For details, see . :ref:`Table 1 <functiongraph_03_0280__en-us_topic_0000001212904604_table12861932162314>` describes the rules for packaging a function project.

.. _functiongraph_03_0280__en-us_topic_0000001212904604_table12861932162314:

.. table:: **Table 1** Function project packaging rules

   +-----------------+---------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Runtime         | JAR File                                                                                                            | ZIP File                                                                                                                                                                                                                                                       | ZIP File on OBS                                                        |
   +=================+=====================================================================================================================+================================================================================================================================================================================================================================================================+========================================================================+
   | Node.js         | Not supported.                                                                                                      | -  If the function project files are saved under the **~/Code/** directory, select and package all files under this directory to ensure that the function handler is under the root directory after the ZIP file is decompressed.                              | Compress project files into a ZIP file and upload it to an OBS bucket. |
   |                 |                                                                                                                     | -  If the function project uses third-party dependencies, package the dependencies into a ZIP file, and import the ZIP file on the function code page. Alternatively, package the third-party dependencies and the function project files together.            |                                                                        |
   +-----------------+---------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | PHP             | Not supported.                                                                                                      | -  If the function project files are saved under the **~/Code/** directory, select and package all files under this directory to ensure that the function handler is under the root directory after the ZIP file is decompressed.                              | Compress project files into a ZIP file and upload it to an OBS bucket. |
   |                 |                                                                                                                     | -  If the function project uses third-party dependencies, package the dependencies into a ZIP file, and import the ZIP file on the function code page. Alternatively, package the third-party dependencies and the function project files together.            |                                                                        |
   +-----------------+---------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Python          | Not supported.                                                                                                      | -  If the function project files are saved under the **~/Code/** directory, select and package all files under this directory to ensure that the function handler is under the root directory after the ZIP file is decompressed.                              | Compress project files into a ZIP file and upload it to an OBS bucket. |
   |                 |                                                                                                                     | -  If the function project uses third-party dependencies, package the dependencies into a ZIP file, and import the ZIP file on the function code page. Alternatively, package the third-party dependencies and the function project files together.            |                                                                        |
   +-----------------+---------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Java            | If the function does not reference third-party components, compile only the function project files into a JAR file. | If the function references third-party components, compile the function project files into a JAR file, and compress all third-party components and the function JAR file into a ZIP file.                                                                      | Compress project files into a ZIP file and upload it to an OBS bucket. |
   +-----------------+---------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Go 1.x          | Not supported.                                                                                                      | Zip the compiled file and ensure that the name of the binary file is consistent with that of the handler. For example, if the name of the binary file is **Handler**, set the name of the handler to **Handler**.                                              | Compress project files into a ZIP file and upload it to an OBS bucket. |
   +-----------------+---------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | C#              | Not supported.                                                                                                      | Compress project files into a ZIP file. The ZIP file must contain the following files: *Project_name*\ **.deps.json**, *Project_name*\ **.dll**, *Project_name*\ **.runtimeconfig.json**, *Project_name*\ **.pdb**, and **HC.Serverless.Function.Common.dll**. | Compress project files into a ZIP file and upload it to an OBS bucket. |
   +-----------------+---------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Custom          | Not supported.                                                                                                      | Compress project files into a ZIP file. The ZIP file must contain a bootstrap file.                                                                                                                                                                            | Compress project files into a ZIP file and upload it to an OBS bucket. |
   +-----------------+---------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+

.. _functiongraph_03_0280__section237534633713:

Example ZIP Project Packages
----------------------------

-  Example directory of a Nods.js project package

   .. code-block:: text

      Example.zip                            Example project package
      |--- lib                               Service file directory
      |--- node_modules                      NPM third-party component directory
      |--- index.js                          .js handler file (mandatory)
      |--- package.json                      NPM project management file

-  Example directory of a PHP project package

   .. code-block:: text

      Example.zip                            Example project package
      |--- ext                               Extension library directory
      |--- pear                              PHP extension and application repository
      |--- index.php                         PHP handler file

-  Example directory of a Python project package

   .. code-block:: text

      Example.zip                            Example project package
      |--- com                               Service file directory
      |--- PLI                               Third-party dependency PLI directory
      |--- index.py                          .py handler file (mandatory)
      |--- watermark.py                      .py file for image watermarking
      |--- watermark.png                     Watermarked image

-  Example directory of a Java project package

   .. code-block:: text

      Example.zip                            Example project package
      |--- obstest.jar                       Service function JAR file
      |--- esdk-obs-java-3.20.2.jar          Third-party dependency JAR file
      |--- jackson-core-2.10.0.jar           Third-party dependency JAR file
      |--- jackson-databind-2.10.0.jar       Third-party dependency JAR file
      |--- log4j-api-2.12.0.jar              Third-party dependency JAR file
      |--- log4j-core-2.12.0.jar             Third-party dependency JAR file
      |--- okhttp-3.14.2.jar                 Third-party dependency JAR file
      |--- okio-1.17.2.jar                   Third-party dependency JAR file

-  Example directory of a Go project package

   .. code-block:: text

      Example.zip                            Example project package
      |--- testplugin.so                     Service function package

-  Example directory of a C# project package

   .. code-block:: text

      Example.zip                                   Example project package
      |--- fssExampleCsharp2.0.deps.json            File generated after project compilation
      |--- fssExampleCsharp2.0.dll                  File generated after project compilation
      |--- fssExampleCsharp2.0.pdb                  File generated after project compilation
      |--- fssExampleCsharp2.0.runtimeconfig.json   File generated after project compilation
      |--- Handler                                  Help file, which can be directly used
      |--- HC.Serverless.Function.Common.dll        .dll file provided by FunctionGraph

-  Custom

   .. code-block:: text

      Example.zip                                   Example project package
      |--- bootstrap                                Executable boot file
