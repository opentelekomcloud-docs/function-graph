:original_name: functiongraph_03_0870.html

.. _functiongraph_03_0870:

How Do I Troubleshoot "CrashLoopBackOff"?
=========================================

The message "CrashLoopBackOff: The application inside the container keeps crashing" is displayed when a custom image execution failure occurs. In this case, perform the following operations:

#. Analyze the causes.


   .. figure:: /_static/images/en-us_image_0000001351600380.png
      :alt: **Figure 1** Viewing the execution result

      **Figure 1** Viewing the execution result

#. Verify the container image by referring to :ref:`Deploying a Function Using a Container Image <functiongraph_04_0103>`.

#. Check whether the image uses the Linux x86 architecture. Currently, only Linux x86 images are supported.
