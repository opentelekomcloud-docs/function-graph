:original_name: functiongraph_03_0330.html

.. _functiongraph_03_0330:

How Does a Function Read or Write Files?
========================================

Background
----------

A function can read files in the code directory. The working directory of a function is the upper-level directory of the handler file. Assume that you have uploaded a folder named **backend**. To read its **test.conf** file in the same level of directory as the handler file, use relative path **code/backend/test.conf** or use a full path (that is, the value of the **RUNTIME_CODE_ROOT** environment variable). To write a file (for example, to create or download a file), go to the **/tmp** directory or use the file system mounting feature provided by FunctionGraph.

.. note::

   -  If containers are reclaimed, file read/written content will become invalid.
   -  Currently, FunctionGraph does not support instance persistence.

Typical Scenarios
-----------------

-  Download files stored in Object Storage Service (OBS) to the **/tmp** directory for processing.
-  To store function execution data in OBS, create a file in the **/tmp** directory, write the data into the file, and then upload the file to OBS.
