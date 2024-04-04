:original_name: functiongraph_01_0100_0.html

.. _functiongraph_01_0100_0:

What Is FunctionGraph?
======================

FunctionGraph hosts and computes event-driven functions in a serverless context while ensuring high availability, high scalability, and zero maintenance. All you need to do is write your code and set conditions.

:ref:`Figure 1 <functiongraph_01_0100_0__en-us_topic_0000001257380267_fig4953173820317>` shows the process of using FunctionGraph.

.. _functiongraph_01_0100_0__en-us_topic_0000001257380267_fig4953173820317:

.. figure:: /_static/images/en-us_image_0000001212740388.png
   :alt: **Figure 1** Usage process

   **Figure 1** Usage process

1. Write code.

Write code in Node.js, Python, Java, or Go. For details, see the *FunctionGraph Developer Guide*.

2. Upload code.

Currently, you can edit code inline, upload a ZIP or JAR file, or obtain a ZIP file from OBS. For details, see :ref:`Table 2 <functiongraph_01_0200_0__en-us_topic_0000001257380265_table35034283164337>`.

3. Trigger functions by API calls or cloud service events.

Call RESTful APIs or use cloud service event sources to trigger function execution and generate instances to implement service functions.

4. Auto scaling is implemented.

During function execution, FunctionGraph scales automatically based on the number of requests without the need for configurations. For details about the maximum number of function instances that can be run concurrently, see :ref:`Notes and Constraints <functiongraph_01_0150>`.

5. View logs.

View run logs of functions as FunctionGraph is interconnected with Log Tank Service (LTS). For details, see section "Querying Function Logs".

6. View monitoring information.

View graphical monitoring information as FunctionGraph is interconnected with Application Operations Management (AOM). For details, see section "Viewing Function Metrics"

7. Billing mode

After a function is executed, you will be billed based on the number of function execution requests and execution duration.
