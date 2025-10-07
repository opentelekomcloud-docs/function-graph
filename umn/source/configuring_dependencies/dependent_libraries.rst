:original_name: functiongraph_01_2102.html

.. _functiongraph_01_2102:

Dependent Libraries
===================

**Supported Dependent Libraries**

FunctionGraph supports both standard and third-party libraries.

-  Standard libraries

   When using standard libraries, you can import them to your inline code or package and upload them to FunctionGraph.

-  Supported non-standard libraries

   FunctionGraph provides built-in third-party components listed in :ref:`Table 1 <functiongraph_01_2102__en-us_topic_0000001532946444_table143351951242>` and :ref:`Table 2 <functiongraph_01_2102__en-us_topic_0000001532946444_table39721459145614>`. You can import these libraries to your inline code in the same way as you import standard libraries.

   .. _functiongraph_01_2102__en-us_topic_0000001532946444_table143351951242:

   .. table:: **Table 1** Third-party components integrated with the Node.js runtime

      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | Name            | Usage                                                                                                                                                                                                                                                  | Version |
      +=================+========================================================================================================================================================================================================================================================+=========+
      | q               | Asynchronous method encapsulation                                                                                                                                                                                                                      | 1.5.1   |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | co              | Asynchronous process control                                                                                                                                                                                                                           | 4.6.0   |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | lodash          | Common tool and method library                                                                                                                                                                                                                         | 4.17.10 |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | esdk-obs-nodejs | OBS sdk                                                                                                                                                                                                                                                | 2.1.5   |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | express         | Simplified web-based application development framework                                                                                                                                                                                                 | 4.16.4  |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | fgs-express     | Provides a Node.js application framework for FunctionGraph and APIG to run serverless applications and REST APIs. This component provides an example of using the Express framework to build serverless web applications or services and RESTful APIs. | 1.0.1   |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | request         | Simplifies HTTP invocation and supports HTTPS and redirection.                                                                                                                                                                                         | 2.88.0  |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+

   .. _functiongraph_01_2102__en-us_topic_0000001532946444_table39721459145614:

   .. table:: **Table 2** Non-standard libraries supported by the Python runtime

      +-----------------------+--------------------------+------------------------------+
      | Module                | Usage                    | Version                      |
      +=======================+==========================+==============================+
      | dateutil              | Date and time processing | 2.6.0                        |
      +-----------------------+--------------------------+------------------------------+
      | requests              | HTTP library             | 2.7.0                        |
      +-----------------------+--------------------------+------------------------------+
      | httplib2              | httpclient               | 0.10.3                       |
      +-----------------------+--------------------------+------------------------------+
      | numpy                 | Mathematical computing   | For pip 2.7, numpy==1.16.6.  |
      |                       |                          |                              |
      |                       |                          | For pip 3.10, numpy==1.24.2. |
      |                       |                          |                              |
      |                       |                          | For pip 3.9, numpy==1.18.5.  |
      |                       |                          |                              |
      |                       |                          | For pip 3.6, numpy==1.18.5.  |
      +-----------------------+--------------------------+------------------------------+
      | redis                 | Redis client             | 2.10.5                       |
      +-----------------------+--------------------------+------------------------------+
      | obsclient             | OBS client               | 3.0.3                        |
      +-----------------------+--------------------------+------------------------------+
      | smnsdk                | SMN access               | 1.0.1                        |
      +-----------------------+--------------------------+------------------------------+

-  Other third-party libraries (FunctionGraph has no built-in non-standard third-party libraries except those listed in the preceding table.)

   Package the dependency third-party libraries and upload them to an OBS bucket or on the function details page. These libraries will then be used in your function code.

**Importing Dependent Libraries**

Importing a dependency for Python:

.. code-block::

   from com.obs.client.obs_client import ObsClient

Importing a dependency for Node.js:

.. code-block::

   const ObsClient = require('esdk-obs-nodejs');

For standard libraries and supported non-standard libraries, you can directly use them in your function.

For non-standard third-party libraries that are not provided by FunctionGraph, you can use them by performing the following steps:

#. Package the dependent libraries into a ZIP file, upload the ZIP file to an OBS bucket, and obtain the OBS link URL.

#. Log in to the FunctionGraph console, and choose **Functions** > **Dependencies** in the navigation pane.

#. Click **Create Dependency**.

#. .. _functiongraph_01_2102__en-us_topic_0000001532946444_li224619133510:

   Set the dependency name and runtime, specify the OBS link URL, and click **OK**.


   .. figure:: /_static/images/en-us_image_0000001757397373.png
      :alt: **Figure 1** Setting the dependency

      **Figure 1** Setting the dependency

#. On the function details page, click the **Code** tab, click **Add** in the **Dependencies** area, select the dependency created in :ref:`4 <functiongraph_01_2102__en-us_topic_0000001532946444_li224619133510>`, and click **OK**.


   .. figure:: /_static/images/en-us_image_0000001709398390.png
      :alt: **Figure 2** Selecting a dependency

      **Figure 2** Selecting a dependency

   .. warning::

      Each dependency package cannot contain a file with the same name as a code file. Otherwise, the two files may be incorrectly merged or overwritten. For example, if dependency package **depends.zip** contains a file named **index.py**, the handler of a function cannot be set to **index.handler**. Otherwise, a code file also named **index.py** will be generated.
