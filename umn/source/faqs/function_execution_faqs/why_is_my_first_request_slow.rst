:original_name: functiongraph_03_0820.html

.. _functiongraph_03_0820:

Why Is My First Request Slow?
=============================

Functions are cold-started. If initialization or a lengthy operation is performed during the first function execution, the first request will be delayed. However, subsequent requests before container deletion will be faster. If there is no request within one minute, the container will be deleted.
