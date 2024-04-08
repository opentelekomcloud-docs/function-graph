:original_name: functiongraph_03_0348.html

.. _functiongraph_03_0348:

How Does FunctionGraph Process Concurrent Requests?
===================================================

FunctionGraph automatically scales in or out function instances based on the number of requests. If the number of concurrent requests increases, FunctionGraph allocates more function instances to process the requests. If that number decreases, FunctionGraph allocates fewer function instances accordingly.

Number of function instances = Function concurrency/Concurrency per instance

-  Function concurrency: the number of requests concurrently executed by a function at a certain time point.
-  Concurrency per instance: the maximum number of concurrent requests allowed by a single instance. This is equivalent to the **Max. Requests per Instance** parameter on the **Concurrency** page.
