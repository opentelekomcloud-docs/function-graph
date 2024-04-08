:original_name: functiongraph_03_0868.html

.. _functiongraph_03_0868:

Why Does a Function Use More Memory Than Estimated and Even Trigger the Out of Memory Alarm?
============================================================================================

#. Event parsing and cache consume extra memory during function invocation.
#. After the invocation is complete, reclaimed memory is often put in the internal pool instead of back to the OS, resulting in high memory usage. This is more obvious in the case of high concurrency.
