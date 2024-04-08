:original_name: functiongraph_03_0849.html

.. _functiongraph_03_0849:

What Should I Do If the **os.system("command &")** Execution Logs Are Not Collected?
====================================================================================

Do not use **os.system("command &")**. The background command output will not be collected. To obtain the command output, use **subprocess.Popen** instead.
