:original_name: functiongraph_04_0104.html

.. _functiongraph_04_0104:

Creating an Event Function Using a Container Image and Executing the Function
=============================================================================

This section uses the creation of an event function using a container image as an example to describe how to create and test a container image function.

You need to implement an HTTP server in the image and listen to port **8000** to receive requests. By default, the request path **/init** is the function initialization entry. Implement it as required. The request path **/invoke** is the function execution entry where trigger events are processed. For details about request parameters, see section "Supported Event Sources". Note: You can use any base image.

Constraints
-----------

-  In the cloud environment, UID 1003 and GID 1003 are used to start the container by default. The two IDs can be modified by choosing **Configuration** > **Basic Settings** > **Container Image Override** on the function details page. They cannot be **root** or a reserved ID.
-  If the base image of the Alpine version is used, run the **addgroup** and **adduser** commands.

Prerequisites
-------------

#. Grant the FunctionGraph operation permissions to the user.

   To perform the operations described in this section, ensure that you have the **FunctionGraph FullAccess** permissions, that is, all permissions for FunctionGraph. For more information, see section **"Permissions Management"**.

Step 1: Create an Image
-----------------------

Take the Linux x86 64-bit OS as an example. (No system configuration is required.)

#. Create a folder.

   .. code-block::

      mkdir custom_container_event_example && cd custom_container_event_example

2. Implement an HTTP server to process **init** and **invoke** requests and give a response. Node.js is used as an example.

   Create the **main.js** file to introduce the Express framework and implement a function handler (method **POST** and path **/invoke** and an initializer (method **POST** and path **/init**).

   .. code-block::

      const express = require('express');

      const PORT = 8000;

      const app = express();
      app.use(express.json());

      app.post('/init', (req, res) => {
        console.log('receive', req.body);
        res.send('Hello init\n');
      });

      app.post('/invoke', (req, res) => {
        console.log('receive', req.body);
        res.send('Hello invoke\n');
      });

      app.listen(PORT, () => {
        console.log(`Listening on http://localhost:${PORT}`);
      });

3. Create the **package.json** file for npm so that it can identify the project and process project dependencies.

   .. code-block::

      {
        "name": "custom-container-event-example",
        "version": "1.0.0",
        "description": "An example of a custom container event function",
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
      ENTRYPOINT ["node", "/home/custom_container/main.js"]

   -  **FROM**: Specify base image **node:12.10.0**. The base image is mandatory and its value can be changed.
   -  **ENV**: Set environment variables **HOME** (**/home/custom_container**), **GROUP_NAME** and **USER_NAME** (**custom_container**), **USER_ID** and **GROUP_ID** (**1003**). These environment variables are mandatory and their values can be changed.
   -  **RUN**: Use the format **RUN** *<Command>*. For example, **RUN mkdir -m 550 ${HOME}**, which means to create the **home** directory for user *${USER_NAME}* during container building.
   -  **USER**: Switch to user *${USER_NAME}*.
   -  **WORKDIR**: Switch the working directory to the **${HOME}** directory of user *${USER_NAME}*.
   -  **COPY**: Copy **main.js** and **package.json** to the **home** directory of user *${USER_NAME}* in the container.
   -  **EXPOSE**: Expose port 8000 of the container. Do not change this parameter.
   -  **ENTRYPOINT**: Run the **node /home/tester/main.js** command to start the container.

5. Build an image.

   In the following example, the image name is **custom_container_event_example**, the tag is **latest**, and the period (.) indicates the directory where the Dockerfile is located. Run the image build command to pack all files in the directory and send the package to a container engine to build an image.

   .. code-block::

      docker build -t custom_container_event_example:latest .

Step 2: Perform Local Verification
----------------------------------

#. Start the Docker container.

   .. code-block::

      docker run -u 1003:1003 -p 8000:8000 custom_container_event_example:latest

2. Open a new Command Prompt, and send a message through port 8000 to access the **/init** directory specified in the template code.

   .. code-block::

      curl -XPOST -H 'Content-Type: application/json' localhost:8000/init

   The following information is returned based on the module code:

   .. code-block::

      Hello init

3. Open a new Command Prompt, and send a message through port 8000 to access the **/invoke** directory specified in the template code.

   .. code-block::

      curl -XPOST -H 'Content-Type: application/json' -d '{"message":"HelloWorld"}' localhost:8000/invoke

   The following information is returned based on the module code:

   .. code-block::

      Hello invoke

4. Check whether the following information is displayed:

   .. code-block::

      Listening on http://localhost:8000
      receive {}
      receive { message: 'HelloWorld' }

   |image1|

   Alternatively, run the **docker logs** command to obtain container logs.

   |image2|

Step 3: Upload the Image
------------------------

#. Log in to the SWR console. In the navigation pane, choose **My Images**.

#. Click **Upload Through Client** or **Upload Through SWR** in the upper right corner.

#. Upload the image as prompted.

   |image3|

#. View the image on the **My Images** page.

Step 4: Create a Function
-------------------------

#. In the left navigation pane of the management console, choose **Compute** > **FunctionGraph**. On the FunctionGraph console, choose **Functions** > **Function List** from the navigation pane.
#. Click **Create Function** in the upper right corner. On the displayed page, select **Container Image** for creation mode.
#. Set the basic function information.

   -  **Function Type**: Select **Event Function**.

   -  **Region**: The default value is used. You can select other regions.

      **Regions are geographic areas isolated from each other. Resources are region-specific and cannot be used across regions through internal network connections. For low network latency and quick resource access, select the nearest region.**

   -  **Function Name**: Enter **custom_container_http**.

   -  **Enterprise Project**: The default value is **default**. You can select the created enterprise project.

      Enterprise projects let you manage cloud resources and users by project.

   -  **Agency**: Select an agency with the **SWR Admin** permission. If no agency is available, create one by referring to :ref:`Creating an Agency <functiongraph_01_0920>`.

   -  **Container Image**: Enter the image uploaded to SWR in :ref:`step 3 <functiongraph_04_0103__section15137197135915>`.

#. (Optional) Set container image overriding parameters.

   -  **CMD**: container startup command. Example: **/bin/sh**. If no command is specified, the entrypoint or CMD in the image configuration will be used.
   -  **Args**: container startup parameter. Example: **-args,value1**. If no argument is specified, CMD in the image configuration will be used.
   -  **Working Dir**: working directory where a container runs. If no directory is specified, the directory in the image configuration will be used. The directory must start with a slash (/).
   -  **User ID**: Enter the user ID.
   -  **Group ID**: Enter the user group ID.

#. **Advanced Settings**: **Collect Logs** is disabled by default. If it is enabled, function execution logs will be reported to Log Tank Service (LTS). You will be billed for log management on a pay-per-use basis.

   .. table:: **Table 1** Parameters for configuring Collect Logs

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

#. After the configuration is complete, click **Create Function**.
#. On the function details page, choose **Configuration** > **Lifecycle**, and enable **Initialization**. The **init** API will be called to initialize the function.

Step 5: Test the Function
-------------------------

#. On the function details page, click **Test**. In the displayed dialog box, create a test event.

#. Select **blank-template**, set **Event Name** to **helloworld**, modify the test event as follows, and click **Create**.

   .. code-block::

      {
          "message": "HelloWorld"
      }

Step 6: View the Execution Result
---------------------------------

Click **Test** and view the execution result on the right.


.. figure:: /_static/images/en-us_image_0000001422840354.png
   :alt: **Figure 1** Execution result

   **Figure 1** Execution result

-  **Function Output**: displays the return result of the function.
-  **Log Output**: displays the execution logs of the function.
-  **Summary**: displays key information of the logs.

   .. note::

      A maximum of 2 KB logs can be displayed. For more log information, see :ref:`Querying Function Logs <functiongraph_01_0170>`.

.. |image1| image:: /_static/images/en-us_image_0000001472598601.png
.. |image2| image:: /_static/images/en-us_image_0000001472598777.png
.. |image3| image:: /_static/images/en-us_image_0000001630990134.png
