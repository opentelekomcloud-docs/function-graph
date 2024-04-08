:original_name: functiongraph_04_0103.html

.. _functiongraph_04_0103:

Developing an HTTP Function
===========================

Introduction
------------

When developing an HTTP function using a custom image, implement an HTTP server in the image and listen on **port 8000** for requests. **(Do not change port 8000 in the examples provided in this section.)** HTTP functions support only APIG triggers.

Step 1: Prepare the Environment
-------------------------------

To perform the operations described in this section, ensure that you have the **FunctionGraph FullAccess** permissions, that is, all permissions for FunctionGraph. For more information, see section "Permissions Management".

Step 2: Create an Image
-----------------------

Take the Linux x86 64-bit OS as an example.

#. Create a folder.

   .. code-block::

      mkdir custom_container_http_example && cd custom_container_http_example

2. Implement an HTTP server. Node.js is used as an example. For details about other languages, see section "Creating an HTTP Function".

   Create the **main.js** file to introduce the Express framework, receive POST requests, print the request body as standard output, and return "Hello FunctionGraph, method POST" to the client.

   .. code-block::

      const express = require('express');

      const PORT = 8000;

      const app = express();
      app.use(express.json());

      app.post('/*', (req, res) => {
          console.log('receive', req.body);
          res.send('Hello FunctionGraph, method POST');
      });

      app.listen(PORT, () => {
        console.log(`Listening on http://localhost:${PORT}`);
      });

3. Create the **package.json** file for npm so that it can identify the project and process project dependencies.

   .. code-block::

      {
        "name": "custom-container-http-example",
        "version": "1.0.0",
        "description": "An example of a custom container http function",
        "main": "main.js",
        "scripts": {},
        "keywords": [],
        "author": "",
        "license": "ISC",
        "dependencies": {
            "express": "^4.17.1"
        }
      }

   -  **name**: project name
   -  **version**: project version
   -  **main**: application entry file
   -  **dependencies**: all available dependencies of the project in npm

4. Create a Dockerfile.

   .. code-block::

      FROM node:12.10.0

      ENV HOME=/home/custom_container
      ENV GROUP_ID=1003
      ENV GROUP_NAME=custom_container
      ENV USER_ID=1003
      ENV USER_NAME=custom_container

      RUN mkdir -m 550 ${HOME} && groupadd -g ${GROUP_ID} ${GROUP_NAME} && useradd -u ${USER_ID} -g ${GROUP_ID} ${USER_NAME}

      COPY --chown=${USER_ID}:${GROUP_ID} main.js ${HOME}
      COPY --chown=${USER_ID}:${GROUP_ID} package.json ${HOME}

      RUN cd ${HOME} && npm install

      RUN chown -R ${USER_ID}:${GROUP_ID} ${HOME}

      RUN find ${HOME} -type d | xargs chmod 500
      RUN find ${HOME} -type f | xargs chmod 500

      USER ${USER_NAME}
      WORKDIR ${HOME}

      EXPOSE 8000
      ENTRYPOINT ["node", "main.js"]

   -  **FROM**: Specify base image **node:12.10.0**. The base image is mandatory and its value can be changed.
   -  **ENV**: Set environment variables **HOME** (**/home/custom_container**), **GROUP_NAME** and **USER_NAME** (**custom_container**), **USER_ID** and **GROUP_ID** (**1003**). These environment variables are mandatory and their values can be changed.
   -  **RUN**: Use the format **RUN** *<Command>*. For example, **RUN mkdir -m 550 ${HOME}**, which means to create the **home** directory for user *${USER_NAME}* during container building.
   -  **USER**: Switch to user *${USER_NAME}*.
   -  **WORKDIR**: Switch the working directory to the **home** directory of user *${USER_NAME}*.
   -  **COPY**: Copy **main.js** and **package.json** to the **home** directory of user *${USER_NAME}* in the container.
   -  **EXPOSE: Expose port 8000 of the container. Do not change this parameter.**
   -  **ENTRYPOINT**: Run the **node main.js** command to start the container. Do not change this parameter.

   .. note::

      a. You can use any base image.
      b. In the cloud environment, UID 1003 and GID 1003 are used to start the container by default. The two IDs can be modified by choosing **Configuration** > **Basic Settings** > **Container Image Override** on the function details page. They cannot be **root** or a reserved ID.
      c. **Do not change port 8000 in the example HTTP function.**

5. Build an image.

   In the following example, the image name is **custom_container_http_example**, the tag is **latest**, and the period (.) indicates the directory where the Dockerfile is located. Run the image build command to pack all files in the directory and send the package to a container engine to build an image.

   .. code-block::

      docker build -t custom_container_http_example:latest .

Step 3: Perform Local Verification
----------------------------------

#. Start the Docker container.

   .. code-block::

      docker run -u 1003:1003 -p 8000:8000 custom_container_http_example:latest

2. Open a new Command Prompt, and send a message through port 8000. You can access all paths in the root directory in the template code. The following uses **helloworld** as an example.

   .. code-block::

      curl -XPOST -H 'Content-Type: application/json' -d '{"message":"HelloWorld"}' localhost:8000/helloworld

   The following information is returned based on the module code:

   .. code-block::

      Hello FunctionGraph, method POST

3. Check whether the following information is displayed:

   .. code-block::

      receive {"message":"HelloWorld"}

   |image1|

   Alternatively, run the **docker logs** command to obtain container logs.

   |image2|

Step 4: Upload the Image
------------------------

#. Log in to the SoftWare Repository for Container (SWR) console. In the navigation pane, choose **My Images**.

#. Click **Upload Through Client** or **Upload Through SWR** in the upper right corner.

#. Upload the image as prompted.

   |image3|

#. View the image on the **My Images** page.

Step 5: Create a Function
-------------------------

#. In the left navigation pane of the management console, choose **Compute** > **FunctionGraph**. On the FunctionGraph console, choose **Functions** > **Function List** from the navigation pane.
#. Click **Create Function** in the upper right corner and choose **Container Image**.
#. Set the basic information.

   -  **Function Type**: Select **HTTP Function**.
   -  **Function Name**: Enter **custom_container_http**.
   -  **Container Image**: Select the image uploaded to SWR.
   -  **Agency**: Select an agency with the **SWR Admin** permission. If no agency is available, create one by referring to section "Creating an Agency".

#. After the configuration is complete, click **Create Function**.

Step 6: Test the Function
-------------------------

#. On the function details page, click **Test**. In the displayed dialog box, create a test event.

#. Select **apig-event-template**, set **Event Name** to **helloworld**, modify the test event as follows, and click **Create**.

   .. code-block::

      {
          "body": "{\"message\": \"helloworld\"}",
          "requestContext": {
              "requestId": "11cdcdcf33949dc6d722640a13091c77",
              "stage": "RELEASE"
          },
          "queryStringParameters": {
              "responseType": "html"
          },
          "httpMethod": "POST",
          "pathParameters": {},
          "headers": {
              "Content-Type": "application/json"
          },
          "path": "/helloworld",
          "isBase64Encoded": false
      }

Step 7: View the Execution Result
---------------------------------

Click **Test** and view the execution result on the right.


.. figure:: /_static/images/en-us_image_0000001422359706.png
   :alt: **Figure 1** Execution result

   **Figure 1** Execution result

-  **Function Output**: displays the return result of the function.
-  **Log Output**: displays the execution logs of the function.
-  **Summary**: displays key information of the logs.

   .. note::

      A maximum of 2 KB logs can be displayed. For more log information, see section "Querying Function Logs".

Step 8: View Monitoring Metrics
-------------------------------

On the function details page, click the **Monitoring** tab.

-  On the **Monitoring** tab page, choose **Metrics**, and select a time range (such as 5 minutes, 15 minutes, or 1 hour) to query the function.
-  The following metrics are displayed: invocations, errors, duration (including the maximum, average, and minimum durations), and throttles.

Step 9: Delete the Function
---------------------------

#. On the function details page, choose **Operation** > **Delete Function** in the upper right corner.
#. In the confirmation dialog box, enter **DELETE** and click **OK** to release resources in a timely manner.

.. |image1| image:: /_static/images/en-us_image_0000001472516001.png
.. |image2| image:: /_static/images/en-us_image_0000001422359078.png
.. |image3| image:: /_static/images/en-us_image_0000001631149450.png
