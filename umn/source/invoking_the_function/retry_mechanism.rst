:original_name: functiongraph_01_1814.html

.. _functiongraph_01_1814:

Retry Mechanism
===============

If synchronous or asynchronous invocation fails, do as follows:

-  Synchronous invocation

   Try again.

-  Asynchronous invocation

   You can set the maximum number of retries and the maximum message validity period (up to 24 hours) by referring to :ref:`Configuring Asynchronous Notification Policy <functiongraph_01_0390_03>`. FunctionGraph will retry a function based on these two parameters.

Idempotency
-----------

In programming, idempotency means that an application or component can identify duplicate events and prevent duplication, inconsistency, and data loss. If you want to keep a function idempotent, you need to design the function logic to correctly handle repeated events.

Idempotent function logic helps reduce the following problems:

-  Unnecessary API calls
-  Code processing time
-  Data inconsistency
-  Restrictions
-  Latency

Ensure that your function code can process the same event multiple times without causing duplicate transactions or other unnecessary side effects in case of abnormal calls, retry of client, or retry within dependent functions.
