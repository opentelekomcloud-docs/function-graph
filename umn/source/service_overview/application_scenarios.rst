:original_name: functiongraph_01_0140_0.html

.. _functiongraph_01_0140_0:

Application Scenarios
=====================

FunctionGraph is suitable for various scenarios, such as real-time file processing, real-time data stream processing, web & mobile application backends, and AI application.

Scenario 1: Event-Driven Applications
-------------------------------------

Services are executed in event-driven mode and resources are provisioned based on demands. Developers do not need to be concerned about service peaks or troughs. Idle resources are not billed, reducing O&M costs. Event-driven applications include file processing, image processing, live streaming/transcoding, real-time data stream processing, and IoT rule/event processing.

-  **Real-time file processing**

   When files are uploaded from a client to OBS, functions can be triggered to create image thumbnails in real time, convert video formats, aggregate and filter data files, or implement other file operations.

   Advantages:

   -  FunctionGraph automatically allocates resources to run more function instances as the number of received requests increases.
   -  Files are uploaded to OBS to trigger file processing functions.
   -  You will be billed only for resources used to process files as needed (you are not billed for idle resources during lows in demand).

Scenario 2: Web Applications
----------------------------

Interconnect FunctionGraph with other cloud services or your VMs to quickly build highly available and scalable web & mobile backends. Web applications include mini programs, web pages/apps, chatbots, and Backends for Frontends (BFF).

Advantages:

-  FunctionGraph ensures high reliability of website data using OBS, and high-availability of website logic using API Gateway.
-  FunctionGraph automatically allocates resources to run more function instances as the number of received requests increases.
-  You will be billed only for resources used to process files as needed (you are not billed for idle resources during lows in demand).

Scenario 3: AI Applications
---------------------------

Intelligence evolution requires various services to be integrated for quick rollout. These services include third-party service integration, AI inference, and license plate recognition.

Advantages:

-  FunctionGraph works with AI services for text recognition and content moderation to suit a wide range of scenarios - make adjustments whenever you need as demands change.
-  You only need to apply for related services and write service code without having to provision or manage servers.
-  You will be billed only for function execution and used AI services without having to pay for idle resources when service demands are low.
