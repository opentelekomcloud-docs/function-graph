:original_name: functiongraph_03_0130.html

.. _functiongraph_03_0130:

How Does a Function Access the MySQL Database?
==============================================

Perform the following operations:

#. Check whether the MySQL database is deployed in a VPC.

   -  Yes: Configure the same VPC and subnet as the MySQL database for the function by referring to section "Configuring VPC Access".
   -  No: See :ref:`How Do I Configure External Network Access? <functiongraph_03_0834>`

#. Search for MySQL templates and select the one with the desired runtime, as shown in :ref:`Figure 1 <functiongraph_03_0130__fig118911551163113>`. Set the parameters as required and click **Create Function**.

   .. _functiongraph_03_0130__fig118911551163113:

   .. figure:: /_static/images/en-us_image_0000001631986292.png
      :alt: **Figure 1** Selecting a function template

      **Figure 1** Selecting a function template

#. After the MySQL function is created, choose **Configuration** > **Environment Variables**, enable encryption as required (see :ref:`Figure 2 <functiongraph_03_0130__fig8962192433716>`), and click **Save**.

   .. _functiongraph_03_0130__fig8962192433716:

   .. figure:: /_static/images/en-us_image_0000001632148468.png
      :alt: **Figure 2** Enabling encryption

      **Figure 2** Enabling encryption

   .. note::

      If the function needs to access RDS APIs, create an agency and grant required permissions.
