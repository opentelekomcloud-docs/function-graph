:original_name: functiongraph_01_0130.html

.. _functiongraph_01_0130:

Relationships Between FunctionGraph and Other Services
======================================================

:ref:`Table 1 <functiongraph_01_0130__table3990123112020>` describes the cloud services that have been interconnected with FunctionGraph.

.. _functiongraph_01_0130__table3990123112020:

.. table:: **Table 1** Interconnected services

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Service                           | Description                                                                                                                                                                                                                                      |
   +===================================+==================================================================================================================================================================================================================================================+
   | SMN                               | FunctionGraph functions are constructed to process SMN notifications.                                                                                                                                                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DMS                               | FunctionGraph functions are configured to automatically poll DMS queues for messages and process any new messages.                                                                                                                               |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API Gateway                       | FunctionGraph functions are invoked over HTTPS by defining REST APIs with specified backend services.                                                                                                                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OBS                               | FunctionGraph functions are created to process OBS bucket events, such as object creation or deletion events. For example, when an image is uploaded to the specified bucket, OBS invokes the function to read the image and create a thumbnail. |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | LTS                               | FunctionGraph functions are built to process logs subscribed to in LTS. When LTS collects subscribed logs, the function is triggered to process or analyze the logs or to load the logs to other systems.                                        |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CTS                               | FunctionGraph functions are defined to analyze and process key information in logs according to the event notifications of specified service type and operations configured in CTS.                                                              |
   |                                   |                                                                                                                                                                                                                                                  |
   |                                   | -  With CTS, you can record operations associated with FunctionGraph for later query, audit, and backtracking.                                                                                                                                   |
   |                                   | -  CTS starts recording operations on cloud resources once being enabled. View traces of the last seven days on the CTS console.                                                                                                                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DDS                               | DDS triggers trigger FunctionGraph functions upon a table change in the database.                                                                                                                                                                |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | AOM                               | Monitor function information in graphics.                                                                                                                                                                                                        |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
