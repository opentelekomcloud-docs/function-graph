:original_name: functiongraph_01_1442.html

.. _functiongraph_01_1442:

Creating an HTTP Function
=========================

Overview
--------

HTTP functions are designed to optimize web services. You can send HTTP requests to URLs to trigger function execution. HTTP functions support APIG triggers only.

.. note::

   -  HTTP functions do not distinguish between programming languages. The handler must be set in the **bootstrap** file. You can directly write the startup command, and allow access over port 8000. The bound IP address is **127.0.0.1**.
   -  The **bootstrap** file is the startup file of the HTTP function. The HTTP function can only read **bootstrap** as the startup file name. If the file name is not **bootstrap**, the service cannot be started. For more information, see the :ref:`bootstrap file example <functiongraph_01_1442__en-us_topic_0000001298667441_li194597302096>`.
   -  HTTP functions support multiple programming languages.
   -  Functions must return a valid HTTP response.
   -  This section uses Node.js as an example. To use another runtime, simply change the runtime path. The code package path does not need to be changed. For the paths of other runtimes, see :ref:`Table 1 <functiongraph_01_1442__en-us_topic_0000001298667441_table20671103902218>`.

Prerequisites
-------------

#. Prepare a Node.js script. A code example is as follows:

   .. code-block::

      const http = require('http'); // Import Node.js core module

      var server = http.createServer(function (req, res) {   //create web server
          res.writeHead(200, { 'Content-Type': 'text/html' });
          res.write('<html><body><h2>This is http function.</h2></body></html>');
          res.end();
      });

      server.listen(8000, '127.0.0.1'); //6 - listen for any incoming requests

      console.log('Node.js web server at port 8000 is running..')

#. .. _functiongraph_01_1442__en-us_topic_0000001298667441_li194597302096:

   You have prepared a **bootstrap** file as the startup file of the HTTP function.

   **Example**

   The content of the **bootstrap** file is as follows:

   .. code-block::

      /opt/function/runtime/nodejs12.13/rtsp/nodejs/bin/node $RUNTIME_CODE_ROOT/index.js

#. Compress the preceding two files into a ZIP package.


   .. figure:: /_static/images/en-us_image_0000001768776664.png
      :alt: **Figure 1** Compressing files into a ZIP package

      **Figure 1** Compressing files into a ZIP package

   .. note::

      For HTTP functions in Python, add the **-u** parameter in the **bootstrap** file to ensure that logs can be flushed to the disk. Example:

      .. code-block::

         /opt/function/runtime/python3.6/rtsp/python/bin/python3 -u $RUNTIME_CODE_ROOT/index.py

   To use another runtime, change the runtime path by referring to :ref:`Table 1 <functiongraph_01_1442__en-us_topic_0000001298667441_table20671103902218>`. The code package path does not need to be changed.

   .. _functiongraph_01_1442__en-us_topic_0000001298667441_table20671103902218:

   .. table:: **Table 1** Paths for different runtimes

      ========== =======================================================
      Runtime    Path
      ========== =======================================================
      Java 8     /opt/function/runtime/java8/rtsp/jre/bin/java
      Java 11    /opt/function/runtime/java11/rtsp/jre/bin/java
      Node.js 6  /opt/function/runtime/nodejs6.10/rtsp/nodejs/bin/node
      Node.js 8  /opt/function/runtime/nodejs8.10/rtsp/nodejs/bin/node
      Node.js 10 /opt/function/runtime/nodejs10.16/rtsp/nodejs/bin/node
      Node.js 12 /opt/function/runtime/nodejs12.13/rtsp/nodejs/bin/node
      Node.js 14 /opt/function/runtime/nodejs14.18/rtsp/nodejs/bin/node
      Node.js 16 /opt/function/runtime/nodejs16.17/rtsp/nodejs/bin/node
      Node.js 18 /opt/function/runtime/nodejs18.15/rtsp/nodejs/bin/node
      Python 2.7 /opt/function/runtime/python2.7/rtsp/python/bin/python
      Python 3.6 /opt/function/runtime/python3.6/rtsp/python/bin/python3
      Python 3.9 /opt/function/runtime/python3.9/rtsp/python/bin/python3
      ========== =======================================================

Procedure
---------

#. Create a function.

   a. Create an HTTP function. For details, see :ref:`Creating an Event Function <functiongraph_01_1441>`. Pay special attention to the following parameters:

      -  **Function Type**: HTTP function
      -  **Region**: Select a region where you will deploy your code.

   b. Choose **Upload** > **Local ZIP**, upload the ZIP package, and click **Deploy**.


      .. figure:: /_static/images/en-us_image_0000001629983696.png
         :alt: **Figure 2** Uploading a ZIP file

         **Figure 2** Uploading a ZIP file

#. Create a trigger.

   .. note::

      HTTP functions support APIG triggers only.

   a. On the function details page, choose **Configuration** > **Triggers** and click **Create Trigger**.

   b. Set the trigger information. This step uses an APIG (dedicated) trigger as an example. For more information, see :ref:`Using an APIG (Dedicated) Trigger <functiongraph_01_0204>`.


      .. figure:: /_static/images/en-us_image_0000001678749193.png
         :alt: **Figure 3** Creating a trigger

         **Figure 3** Creating a trigger

      .. note::

         In this example, **Security Authentication** is set to **None**. You need to select an authentication mode based on site requirements.

         -  **App**: AppKey and AppSecret authentication. This mode is of high security and is recommended.
         -  **IAM**: IAM authentication. This mode grants access permissions to IAM users only and is of medium security.
         -  **None**: No authentication. This mode grants access permissions to all users.

   c. When the configuration is complete, click **OK**. After the trigger is created, **API_test_http** will be generated on the APIG console.

#. Publish the API.

   a. On the **Triggers** tab page, click an API name to go to the API overview page.


      .. figure:: /_static/images/en-us_image_0000001629992736.png
         :alt: **Figure 4** APIG trigger

         **Figure 4** APIG trigger

   b. Click **Edit** in the upper right corner. The **Basic Information** page is displayed.


      .. figure:: /_static/images/en-us_image_0000001259876542.png
         :alt: **Figure 5** Editing an API

         **Figure 5** Editing an API

   c. Click **Next**. On the **Define API Request** page that is displayed, change **Path** to **/user/get** and click **Finish**.


      .. figure:: /_static/images/en-us_image_0000001307957865.png
         :alt: **Figure 6** Defining an API request

         **Figure 6** Defining an API request

   d. Click **Publish API**. On the displayed page, click **Publish**.

#. Trigger a function.

   a. Go to the FunctionGraph console, choose **Functions** > **Function List** in the navigation pane, and click the created HTTP function to go to its details page.

   b. Choose **Configuration** > **Triggers**, copy the URL, and access it using a browser.


      .. figure:: /_static/images/en-us_image_0000001630335086.png
         :alt: **Figure 7** Copying the URL

         **Figure 7** Copying the URL

   c. View the request result.


      .. figure:: /_static/images/en-us_image_0000001260038950.png
         :alt: **Figure 8** Viewing the request result

         **Figure 8** Viewing the request result

Common Function Request Headers
-------------------------------

The following table lists the default request header fields of an HTTP function.

.. table:: **Table 2** Default request header fields

   ================== =================================
   Field              Description
   ================== =================================
   X-CFF-Request-Id   ID of the current request
   X-CFF-Memory       Allocated memory
   X-CFF-Timeout      Function timeout duration
   X-CFF-Func-Version Function version
   X-CFF-Func-Name    Function name
   X-CFF-Project-Id   Project ID
   X-CFF-Package      App to which the function belongs
   X-CFF-Region       Current region
   ================== =================================
