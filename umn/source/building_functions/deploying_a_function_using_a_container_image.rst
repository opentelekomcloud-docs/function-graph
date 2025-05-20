:original_name: functiongraph_01_1047.html

.. _functiongraph_01_1047:

Deploying a Function Using a Container Image
============================================

Introduction
------------

Package your container images complying with the Open Container Initiative (OCI) standard, and upload them to FunctionGraph. The images will be loaded and run by FunctionGraph. Unlike the code upload mode, you can use a custom code package, which is flexible and reduces migration costs. You can create event and HTTP functions by using a custom image.

For details about how to develop and deploy an HTTP function using a container image, see :ref:`Developing an HTTP Function <functiongraph_04_0103>`.

For details about how to develop and deploy an event function using a container image, see :ref:`Creating an Event Function Using a Container Image and Executing the Function <functiongraph_04_0104>`.

The following features are supported:

-  **Downloading images**

   Images are stored in SoftWare Repository for Container (SWR) and can only be downloaded by users with the **SWR Admin** permission. FunctionGraph will call the SWR API to generate and set temporary login commands before creating instances.

-  **Setting environment variables**

   Encryption settings and environment variables are supported. For details, see :ref:`Configuring Environment Variables <functiongraph_01_0154>`.

-  **Attaching external data disks**

   External data disks can be attached. For details, see :ref:`Configuring Disk Mounting <functiongraph_01_0402>`.

-  **Reserved instances**

   For details, see the description about reserved instances.

-  **Deploying a new image**

   You can redeploy a new image in a function.

.. note::

   User containers will be started using UID 1003 and GID 1003, which are the same as other types of functions.

Prerequisites
-------------

You have created an agency with the **SWR Admin** permission by referring to :ref:`Configuring Agency Permissions <functiongraph_01_0920>`. Images are stored in SWR, and only users with this permission can invoke and pull images.

Procedure
---------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. On the **Function List** page, click **Create Function** in the upper right corner.

#. Select **Container Image**. For details, see :ref:`Table 1 <functiongraph_01_1047__en-us_topic_0000001298667445_table6474815173514>`.


   .. figure:: /_static/images/en-us_image_0000001678918577.png
      :alt: **Figure 1** Creating a function using a container image

      **Figure 1** Creating a function using a container image

   .. _functiongraph_01_1047__en-us_topic_0000001298667445_table6474815173514:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================+
      | \*Function Type                   | Select a function type.                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                        |
      |                                   | **HTTP function**: triggered once HTTP requests are sent to specific URLs.                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                        |
      |                                   | .. note::                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                        |
      |                                   |    -  The custom container image must contain an HTTP server with listening port 8000.                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                        |
      |                                   |    -  HTTP functions support APIG and APIC triggers only.                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                        |
      |                                   |    -  When calling a function using APIG, **isBase64Encoded** is valued **true** by default, indicating that the request body transferred to FunctionGraph is encoded using Base64 and must be decoded for processing. |
      |                                   |                                                                                                                                                                                                                        |
      |                                   |    -  The function must return characters strings by using the following structure.                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                        |
      |                                   |       .. code-block::                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                        |
      |                                   |          {                                                                                                                                                                                                             |
      |                                   |              "isBase64Encoded": true|false,                                                                                                                                                                            |
      |                                   |              "statusCode": httpStatusCode,                                                                                                                                                                             |
      |                                   |              "headers": {"headerName":"headerValue",...},                                                                                                                                                              |
      |                                   |              "body": "..."                                                                                                                                                                                             |
      |                                   |          }                                                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Region                          | Select a region where you will deploy your code.                                                                                                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Function Name                   | Name of the function, which must meet the following requirements:                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                        |
      |                                   | -  Consists of 1 to 60 characters, and can contain letters, digits, hyphens (-), and underscores (_).                                                                                                                  |
      |                                   | -  Starts with a letter and ends with a letter or digit.                                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Enterprise Project              | Select a created enterprise project and add the function to it. By default, **default** is selected.                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container Image                   | Enter an image URL, that is, the location of the container image. You can click **View Image** to view private and shared images.                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container Image Override          | -  **CMD**: container startup command. Example: **/bin/sh**. If no command is specified, the entrypoint or CMD in the image configuration will be used. Enter one or more commands separated with commas (,).          |
      |                                   | -  **Args**: container startup parameter. Example: **-args,value1**. If no argument is specified, CMD in the image configuration will be used. Enter one or more arguments separated with commas (,).                  |
      |                                   | -  **Working Dir**: working directory of the container. The folder path can only be **/** and cannot be created or modified. The path will be **/** by default if not specified.                                       |
      |                                   | -  **User ID**: user ID for running the image. If no user ID is specified, the default value **1003** will be used.                                                                                                    |
      |                                   | -  **Group ID**: user group ID. If no user group ID is specified, the default value **1003** will be used.                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agency                            | Select an agency with the **SWR Admin** permission. To create an agency, see :ref:`Creating an Agency <functiongraph_01_0920__en-us_topic_0000001298507433_section17872123319473>`.                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  **Command**, **Args**, and **Working dir** can contain up to 5120 characters.
      -  When a function is executed at the first time, the image is pulled from SWR, and the container is started during cold start of the function, which takes a certain period of time. If there is no image on a node during subsequent cold starts, an image will be pulled from SWR.
      -  Public and private images are supported. For details, see `Setting Image Attributes <https://docs.otc.t-systems.com/software-repository-container/umn/image_management/setting_image_attributes.html>`__.
      -  The port of a custom container image must be 8000.
      -  The image package cannot exceed 10 GB. For a larger package, reduce the capacity. For example, mount the data of a question library to a container where the data was previously loaded through an external file system.
      -  FunctionGraph uses LTS to collect all logs that the container outputs to the console. These logs can be redirected to and printed on the console through standard output or an open-source log framework. The logs should include the system time, component name, code line, and key data, to facilitate fault locating.
      -  When an out of memory (OOM) error occurs, view the memory usage in the function execution result.
      -  Functions must return a valid HTTP response.

#. **Advanced Settings**: **Collect Logs** is disabled by default. If it is enabled, function execution logs will be reported to Log Tank Service (LTS). You will be billed for log management on a pay-per-use basis.

   .. table:: **Table 2** Parameters for configuring Collect Logs

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                    |
      +===================================+================================================================================================================================+
      | Log Configuration                 | You can select **Auto** or **Custom**.                                                                                         |
      |                                   |                                                                                                                                |
      |                                   | -  **Auto**: Use the default log group and log stream. Log groups prefixed with "functiongraph.log.group" are filtered out.    |
      |                                   | -  **Custom**: Select a custom log group and log stream. Log streams that are in the same enterprise project as your function. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | Log Tag                           | You can use these tags to filter function logs in LTS. You can add 10 more tags.                                               |
      |                                   |                                                                                                                                |
      |                                   | Tag key/value: Enter a maximum of 64 characters. Only digits, letters, underscores (_), and hyphens (-) are allowed.           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

#. (Optional) Deploy a new image.

   On the **Code** tab, click **Deploy Image** on the right, enter the URL of the new image in the text box, and click **OK**. To obtain the URL, perform the following operations:

   a. Log in to the SWR console. In the navigation pane, choose **My Images**.
   b. Click the **Private Images** or **Images From Others** tab. In the image list, click the image name to go to the details page.
   c. Click the **Tags** tab, copy the download command in the image tag list, and delete **docker pull** from the command to obtain the image URL.

Sample Code
-----------

The following uses **Node.js Express** as an example. During function initialization, FunctionGraph uses the POST method to access the **/init** path (optional). Each time when a function is called, FunctionGraph uses the POST method to access the **/invoke** path. The function obtains **context** from **req.headers**, obtains **event** from **req.body**, and returns an HTTP response struct.

.. code-block::

   const express = require('express');
   const app = express();
   const PORT = 8000;

   app.post('/init', (req, res) => {
     res.send('Hello init\n');
   });

   app.post('/invoke', (req, res) => {
     res.send('Hello invoke\n');
   });

   app.listen(PORT, () => {
     console.log(`Listening on http://localhost:${PORT}`);
   });
