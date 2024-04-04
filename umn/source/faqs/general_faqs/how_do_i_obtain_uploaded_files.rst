:original_name: functiongraph_03_0846.html

.. _functiongraph_03_0846:

How Do I Obtain Uploaded Files?
===============================

Take Python as an example. If you use **os.getcwd()** to query the current directory, the directory will be **/opt/function**. However, code has actually been uploaded to **/opt/function/code**.

You can use either of the following methods to obtain uploaded files:

#. Run the **cd** command to switch to **/opt/function/code**.
#. Access the full path (value of the **RUNTIME_CODE_ROOT** environment variable).

   .. note::

      You can obtain uploaded files by referring to the preceding methods when other languages are used.
