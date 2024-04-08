:original_name: functiongraph_01_0154.html

.. _functiongraph_01_0154:

Configuring Environment Variables
=================================

Overview
--------

Environment variables allow you to pass dynamic parameters to a function without modifying code.

Scenario
--------

-  Environment distinguishing: Configure different environment variables for the same function logic. For example, use environment variables to configure testing and development databases.
-  Configuration encryption: Configure encrypted environment variables to dynamically obtain authentication information (account, password, AK/SK) required to access other services.
-  Dynamic configuration: Configure environment variables for parameters that need to be dynamically adjusted, including query period and timeout, in function logic.

Procedure
---------

You can configure encryption settings and environment variables to dynamically pass settings to your function code and libraries without changing your code.


.. figure:: /_static/images/en-us_image_0000001630698024.png
   :alt: **Figure 1** Adding environment variables

   **Figure 1** Adding environment variables

For example, for Node.js, encryption settings and environment variable values can be obtained from **getUserData(string key)** in **Context**.

.. warning::

   -  Environment variables and encryption settings are user-defined key-value pairs that store function settings. Keys can contain letters, digits, and underscores (_), and must start with a letter.
   -  The total length of the key and value cannot exceed 4096 characters.
   -  When you define environment variables, FunctionGraph displays all your input information in plain text. For security purposes, do not include sensitive information.
   -  After encryption is enabled, key-value pairs are encrypted on the console and will remain encrypted during transmission.

Preset Parameters
-----------------

The following lists preset parameters. Do not configure environment variables with the same names as any of these parameters.

.. table:: **Table 1** Preset parameters and description

   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | Environment Variable        | Description                                                            | Obtaining Method and Default Value                                          |
   +=============================+========================================================================+=============================================================================+
   | RUNTIME_PROJECT_ID          | Project ID                                                             | Obtain the value from a Context interface or a system environment variable. |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_FUNC_NAME           | Function name                                                          | Obtain the value from a Context interface or a system environment variable. |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_FUNC_VERSION        | Function version                                                       | Obtain the value from a Context interface or a system environment variable. |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_HANDLER             | Handler                                                                | Obtain the value from a system environment variable.                        |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_TIMEOUT             | Execution timeout allowed for a function.                              | Obtain the value from a system environment variable.                        |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_USERDATA            | Value passed through an environment variable                           | Obtain the value from a Context interface or a system environment variable. |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_CPU                 | CPU usage of a function. The value is in proportion to **MemorySize**. | Obtain the value from a Context interface or a system environment variable. |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_MEMORY              | Memory size configured for a function                                  | Obtain the value from a Context interface or a system environment variable. |
   |                             |                                                                        |                                                                             |
   |                             |                                                                        | Unit: MB                                                                    |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_MAX_RESP_BODY_SIZE  | Maximum size of a response body                                        | Obtain the value from a system environment variable.                        |
   |                             |                                                                        |                                                                             |
   |                             |                                                                        | Default value: 6,291,456 bytes                                              |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_INITIALIZER_HANDLER | Initializer                                                            | Obtain the value from a system environment variable.                        |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_INITIALIZER_TIMEOUT | Initialization timeout of a function                                   | Obtain the value from a system environment variable.                        |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_ROOT                | Runtime package path                                                   | Obtain the value from a system environment variable.                        |
   |                             |                                                                        |                                                                             |
   |                             |                                                                        | Default value: **/home/snuser/runtime**                                     |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_CODE_ROOT           | Path for storing code in a container                                   | Obtain the value from a system environment variable.                        |
   |                             |                                                                        |                                                                             |
   |                             |                                                                        | Default value: **/opt/function/code**                                       |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | RUNTIME_LOG_DIR             | Path for storing system logs in a container                            | Obtain the value from a system environment variable.                        |
   |                             |                                                                        |                                                                             |
   |                             |                                                                        | Default value: **/home/snuser/log**                                         |
   +-----------------------------+------------------------------------------------------------------------+-----------------------------------------------------------------------------+

Example
-------

You can use environment variables to configure which directory to install files in, where to store outputs, and how to store connection and logging settings. These settings are decoupled from the application logic, so you do not need to update your function code when you change the settings.

In the following code snippet, **obs_output_bucket** is the bucket used for storing processed images.

.. code-block:: text

   def handler(event, context):
       srcBucket, srcObjName = getObsObjInfo4OBSTrigger(event)
       obs_address = context.getUserData('obs_address')
       outputBucket = context.getUserData('obs_output_bucket')
       if obs_address is None:
           obs_address = '{obs_address_ip}'
       if outputBucket is None:
           outputBucket = 'casebucket-out'

       ak = context.getAccessKey()
       sk = context.getSecretKey()

       # download file uploaded by user from obs
       GetObject(obs_address, srcBucket, srcObjName, ak, sk)

       outFile = watermark_image(srcObjName)

       # Upload converted files to a new OBS bucket.
       PostObject (obs_address, outputBucket, outFile, ak, sk)

       return 'OK'

Using environment variable **obs_output_bucket**, you can flexibly set the OBS bucket used for storing output images.


.. figure:: /_static/images/en-us_image_0000001679098753.png
   :alt: **Figure 2** Environment variables

   **Figure 2** Environment variables
