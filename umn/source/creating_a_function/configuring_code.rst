:original_name: functiongraph_01_0152.html

.. _functiongraph_01_0152:

Configuring Code
================

To create a function, you must create a deployment package which includes your code and all dependencies. You can create a deployment package locally or edit code on the FunctionGraph console. If you edit code inline, FunctionGraph automatically creates and uploads a deployment package for your function. FunctionGraph allows you to edit function code in the same way as managing a project. You can create and edit files and folders. After you upload a ZIP code package, you can view and edit the code on the console.

.. note::

   -  After programming, simply package your code into a ZIP file (Java, Node.js, Python, and Go) or JAR file (Java), and upload the file to FunctionGraph for execution.
   -  When creating a ZIP file, place the handler file under the **root** directory to ensure that your code can run normally after being decompressed.
   -  If you edit code in Go, zip the compiled file, and ensure that the name of the dynamic library file is consistent with the plug-in name of the handler. For example, if the name of the dynamic library file is **testplugin.so**, set the handler name to **testplugin.Handler**.
   -  Java is a compiled language, which does not support editing code inline. If your function does not use any third-party dependencies, you can upload a function JAR file. If your function uses third-party dependencies, compress the dependencies and the function JAR file into a ZIP file, and then upload the ZIP file.

:ref:`Table 1 <functiongraph_01_0152__en-us_topic_0000001251588476_table35034283164337>` lists the code entry modes supported by FunctionGraph for each runtime.

.. _functiongraph_01_0152__en-us_topic_0000001251588476_table35034283164337:

.. table:: **Table 1** Code entry modes

   +-------------------------------------------------------------------------------------------------+---------------------+----------------------+----------------------+-------------------------------+
   | Runtime                                                                                         | Editing Code Inline | Uploading a ZIP File | Uploading a JAR File | Uploading a ZIP File from OBS |
   +=================================================================================================+=====================+======================+======================+===============================+
   | :ref:`Node.js <functiongraph_01_0152__en-us_topic_0000001251588476_section19628123822418>`      | Supported           | Supported            | Not supported        | Supported                     |
   +-------------------------------------------------------------------------------------------------+---------------------+----------------------+----------------------+-------------------------------+
   | :ref:`Python <functiongraph_01_0152__en-us_topic_0000001251588476_section4865310182816>`        | Supported           | Supported            | Not supported        | Supported                     |
   +-------------------------------------------------------------------------------------------------+---------------------+----------------------+----------------------+-------------------------------+
   | :ref:`Java <functiongraph_01_0152__en-us_topic_0000001251588476_section14790124217354>`         | Not supported       | Supported            | Supported            | Supported                     |
   +-------------------------------------------------------------------------------------------------+---------------------+----------------------+----------------------+-------------------------------+
   | :ref:`Go <functiongraph_01_0152__en-us_topic_0000001251588476_section1980313817362>`            | Not supported       | Supported            | Not supported        | Supported                     |
   +-------------------------------------------------------------------------------------------------+---------------------+----------------------+----------------------+-------------------------------+
   | :ref:`C# <functiongraph_01_0152__en-us_topic_0000001251588476_section5575103419499>`            | Not supported       | Supported            | Not supported        | Supported                     |
   +-------------------------------------------------------------------------------------------------+---------------------+----------------------+----------------------+-------------------------------+
   | :ref:`PHP <functiongraph_01_0152__en-us_topic_0000001251588476_section1016816117271>`           | Supported           | Supported            | Not supported        | Supported                     |
   +-------------------------------------------------------------------------------------------------+---------------------+----------------------+----------------------+-------------------------------+
   | :ref:`Custom runtime <functiongraph_01_0152__en-us_topic_0000001251588476_section166121748658>` | Supported           | Supported            | Not supported        | Supported                     |
   +-------------------------------------------------------------------------------------------------+---------------------+----------------------+----------------------+-------------------------------+

.. important::

   If the code to be uploaded contains sensitive information (such as account passwords), encrypt the sensitive information to prevent leakage.

.. table:: **Table 2** Code entry modes

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Code Entry Mode                   | Description                                                                                                                                                                                                                                   |
   +===================================+===============================================================================================================================================================================================================================================+
   | Edit code inline                  | FunctionGraph allows you to edit function code in the same way as managing a project. You can create and edit files and folders. After you upload a ZIP code package, you can edit the code on the **Code** tab of the function details page. |
   |                                   |                                                                                                                                                                                                                                               |
   |                                   | -  **File**: Create files and folders, save changes, and close all files.                                                                                                                                                                     |
   |                                   | -  **Edit**: Undo/redo typing; cut, copy, and paste code; find and replace content.                                                                                                                                                           |
   |                                   | -  **Settings**: Set the font size, auto formatting, and theme color.                                                                                                                                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Upload ZIP file                   | #. On the **Code** tab of the function details page, choose **Upload** > **Local ZIP**.                                                                                                                                                       |
   |                                   | #. Click **Select File** and upload a local code package to FunctionGraph. The size of the ZIP file cannot exceed 40 MB. For a larger file, upload it through OBS.                                                                            |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Upload file from OBS              | #. On the **Code** tab of the function details page, choose **Upload** > **OBS ZIP**.                                                                                                                                                         |
   |                                   | #. Click **Select File** and upload a local code package to FunctionGraph.                                                                                                                                                                    |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _functiongraph_01_0152__en-us_topic_0000001251588476_section19628123822418:

Node.js
-------

**Editing Code Inline**

FunctionGraph provides an SDK for editing code in Node.js. If your custom code uses only the SDK library, you can edit code using the inline editor on the FunctionGraph console. After you edit code inline and upload it to FunctionGraph, the console compresses your code and the related configurations into a deployment package that FunctionGraph can run.

**Uploading a Deployment Package**

If your code uses other resources, such as a graphic library for image processing, first create a deployment package, and then upload the package to the FunctionGraph console. You can upload a Node.js deployment package in two ways.

.. important::

   -  When creating a ZIP file, place the handler file under the **root** directory to ensure that your code can run normally after being decompressed.
   -  The size of the decompressed source code cannot exceed 1.5 GB. If the code is too large, contact the customer service.

-  Directly uploading a local deployment package

   After creating a ZIP deployment package, upload it to the FunctionGraph console. If the package size exceeds 40 MB, upload the package from OBS.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

-  Uploading a deployment package using an OBS bucket

   After creating a ZIP deployment package, upload it to an OBS bucket in the same region as your FunctionGraph, and then paste the link URL of the OBS bucket into the function. The maximum size of the ZIP file that can be uploaded to OBS is 300 MB.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

.. _functiongraph_01_0152__en-us_topic_0000001251588476_section4865310182816:

Python
------

**Editing Code Inline**

FunctionGraph provides an SDK for editing code in Python. If your custom code uses only the SDK library, you can edit code using the inline editor on the FunctionGraph console. After you edit code inline and upload it to FunctionGraph, the console compresses your code and the related configurations into a deployment package that FunctionGraph can run.

**Uploading a Deployment Package**

If your code uses other resources, such as a graphic library for image processing, first create a deployment package, and then upload the package to the FunctionGraph console. You can upload a Python deployment package in two ways.

.. important::

   -  When creating a ZIP file, place the handler file under the **root** directory to ensure that your code can run normally after being decompressed.
   -  The size of the decompressed source code cannot exceed 1.5 GB. If the code is too large, contact the customer service.
   -  When you write code in Python, do not name your package with the same suffix as a standard Python library, such as **json**, **lib**, and **os**. Otherwise, an error indicating a module loading failure will be reported.

-  Directly uploading a local deployment package

   After creating a ZIP deployment package, upload it to the FunctionGraph console. If the package size exceeds 40 MB, upload the package from OBS.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

-  Uploading a deployment package using an OBS bucket

   After creating a ZIP deployment package, upload it to an OBS bucket in the same region as your FunctionGraph, and then paste the link URL of the OBS bucket into the function. The maximum size of the ZIP file that can be uploaded to OBS is 300 MB.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

.. _functiongraph_01_0152__en-us_topic_0000001251588476_section14790124217354:

Java
----

Java is a compiled language, which does not support editing code inline. You can only upload a local deployment package, which can be a ZIP or JAR file.

**Uploading a JAR File**

-  If your function does not use any dependencies, directly upload a JAR file.
-  If your function uses dependencies, upload them to an OBS bucket, set them during function creation, and upload the JAR file.

**Uploading a ZIP File**

If your function uses third-party dependencies, compress the dependencies and the function JAR file into a ZIP file, and then upload the ZIP file.

You can upload a Java deployment package in two ways.

.. important::

   -  When creating a ZIP file, place the handler file under the **root** directory to ensure that your code can run normally after being decompressed.
   -  The size of the decompressed source code cannot exceed 1.5 GB. If the code is too large, contact the customer service.

-  Directly uploading a local deployment package

   After creating a ZIP deployment package, upload it to the FunctionGraph console. If the package size exceeds 40 MB, upload the package from OBS.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

-  Uploading a deployment package using an OBS bucket

   After creating a ZIP deployment package, upload it to an OBS bucket in the same region as your FunctionGraph, and then paste the link URL of the OBS bucket into the function. The maximum size of the ZIP file that can be uploaded to OBS is 300 MB.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

.. _functiongraph_01_0152__en-us_topic_0000001251588476_section1980313817362:

Go
--

**Uploading a Deployment Package**

You can only upload a Go deployment package in ZIP format. There are two ways to upload it.

.. important::

   -  When creating a ZIP file, place the handler file under the **root** directory to ensure that your code can run normally after being decompressed.
   -  The size of the decompressed source code cannot exceed 1.5 GB. If the code is too large, contact the customer service.

-  Directly uploading a local deployment package

   After creating a ZIP deployment package, upload it to the FunctionGraph console. If the package size exceeds 40 MB, upload the package from OBS.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

-  Uploading a deployment package using an OBS bucket

   After creating a ZIP deployment package, upload it to an OBS bucket in the same region as your FunctionGraph, and then paste the link URL of the OBS bucket into the function. The maximum size of the ZIP file that can be uploaded to OBS is 300 MB.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

.. _functiongraph_01_0152__en-us_topic_0000001251588476_section5575103419499:

C#
--

**Uploading a Deployment Package**

You can only upload a C# deployment package in ZIP format. There are two ways to upload it.

.. important::

   -  When creating a ZIP file, place the handler file under the **root** directory to ensure that your code can run normally after being decompressed.
   -  The size of the decompressed source code cannot exceed 1.5 GB. If the code is too large, contact the customer service.

-  Directly uploading a local deployment package

   After creating a ZIP deployment package, upload it to the FunctionGraph console. If the package size exceeds 40 MB, upload the package from OBS.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

-  Uploading a deployment package using an OBS bucket

   After creating a ZIP deployment package, upload it to an OBS bucket in the same region as your FunctionGraph, and then paste the link URL of the OBS bucket into the function. The maximum size of the ZIP file that can be uploaded to OBS is 300 MB.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

.. _functiongraph_01_0152__en-us_topic_0000001251588476_section1016816117271:

PHP
---

**Editing Code Inline**

FunctionGraph provides an SDK for editing code in PHP. If your custom code uses only the SDK library, you can edit code using the inline editor on the FunctionGraph console. After you edit code inline and upload it to FunctionGraph, the console compresses your code and the related configurations into a deployment package that FunctionGraph can run.

**Uploading a Deployment Package**

If your code uses other resources, such as a graphic library for image processing, first create a deployment package, and then upload the package to the FunctionGraph console. You can upload a PHP deployment package in two ways.

.. important::

   -  When creating a ZIP file, place the handler file under the **root** directory to ensure that your code can run normally after being decompressed.
   -  The size of the decompressed source code cannot exceed 1.5 GB. If the code is too large, contact the customer service.

-  Directly uploading a local deployment package

   After creating a ZIP deployment package, upload it to the FunctionGraph console. If the package size exceeds 40 MB, upload the package from OBS.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

-  Uploading a deployment package using an OBS bucket

   After creating a ZIP deployment package, upload it to an OBS bucket in the same region as your FunctionGraph, and then paste the link URL of the OBS bucket into the function. The maximum size of the ZIP file that can be uploaded to OBS is 300 MB.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

.. _functiongraph_01_0152__en-us_topic_0000001251588476_section166121748658:

Custom Runtime
--------------

**Editing Code Inline**

After you edit code inline and upload it to FunctionGraph, the console compresses your code and the related configurations into a deployment package that FunctionGraph can run.

**Uploading a Deployment Package**

If your code uses other resources, such as a graphic library for image processing, first create a deployment package, and then upload the package to the FunctionGraph console. You can upload a deployment package for a custom runtime in two ways.

.. important::

   -  When creating a ZIP file, place the handler file under the **root** directory to ensure that your code can run normally after being decompressed.
   -  The size of the decompressed source code cannot exceed 1.5 GB. If the code is too large, contact the customer service.

-  Directly uploading a local deployment package

   After creating a ZIP deployment package, upload it to the FunctionGraph console. If the package size exceeds 40 MB, upload the package from OBS.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

-  Uploading a deployment package using an OBS bucket

   After creating a ZIP deployment package, upload it to an OBS bucket in the same region as your FunctionGraph, and then paste the link URL of the OBS bucket into the function. The maximum size of the ZIP file that can be uploaded to OBS is 300 MB.

   For details about function resource restrictions, see :ref:`Notes and Constraints <functiongraph_01_0150>`.
