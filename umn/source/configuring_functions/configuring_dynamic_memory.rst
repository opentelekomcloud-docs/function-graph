:original_name: functiongraph_01_0310.html

.. _functiongraph_01_0310:

Configuring Dynamic Memory
==========================

Overview
--------

By default, a function is bound with only one resource specification. After enabling dynamic memory, you can configure a specification for request processing. If no specification is configured, the default one is used.

Scenario
--------

Take video transcoding as an example. The size of a video file ranges from MB to GB. Different encoding formats and resolutions require different computing resources. To ensure performance, you usually need to configure a large resource specification, which however will result in a waste during low-resolution video (such as short video) processing. To solve this problem, implement the transcoding service with two functions: metadata obtaining and transcoding. Configure a specification for the transcoding function according to the metadata information to minimize the resources and cost.

Prerequisites
-------------

You have created a function according to :ref:`Creating a Function from Scratch <functiongraph_01_0153>`.

Procedure
---------

#. Log in to the FunctionGraph console, choose **Functions** > **Function List** in the navigation pane, and click the name of the created function.


   .. figure:: /_static/images/en-us_image_0000001298507537.png
      :alt: **Figure 1** Selecting a created function

      **Figure 1** Selecting a created function

#. On the function details page, choose **Configuration** > **Advanced Settings** and enable **Dynamic Memory**.

#. Call the synchronous or asynchronous function execution API, add **X-Cff-Instance-Memory** to the request header, and set the value to **128**, **256**, **512**, **768**, **1024**, **1280**, **1536**, **1792**, **2048**, **2560**, **3072**, **3584**, **4096**, **8192**, or **10240**.

   The following describes how to call an API using Postman. Add **X-Cff-Instance-Memory** to **Headers** and set the value to **512**. If the API is called successfully, error code 200 will be returned.


   .. figure:: /_static/images/en-us_image_0000001252067312.png
      :alt: **Figure 2** Adding a request header and calling the function

      **Figure 2** Adding a request header and calling the function

   .. note::

      -  If **Dynamic Memory** is not enabled, the memory size set when the function is created will be used by default.

      -  If **Dynamic Memory** is enabled but the memory value has not been set, the memory size set when the function is created will be used by default. If the API is called successfully, error code 200 will be returned.

      -  If **Dynamic Memory** is enabled but the memory value is not **128**, **256**, **512**, **768**, **1024**, **1280**, **1536**, **1792**, **2048**, **2560**, **3072**, **3584**, **4096**, **8192**, or **10240**, error code FSS.0406 will be returned when the API is called. You only need to reset the memory value.


         .. figure:: /_static/images/en-us_image_0000001251748292.png
            :alt: **Figure 3** Invocation failure

            **Figure 3** Invocation failure
