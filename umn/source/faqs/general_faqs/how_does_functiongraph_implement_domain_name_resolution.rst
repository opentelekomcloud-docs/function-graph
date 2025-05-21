:original_name: functiongraph_03_0839.html

.. _functiongraph_03_0839:

How Does FunctionGraph Implement Domain Name Resolution?
========================================================

FunctionGraph cannot directly resolve private DNS domain names. To resolve them, call DNS APIs and perform the following steps.

Resolving a Private DNS Domain Name with an Event Function
----------------------------------------------------------

Ensure that a VPC and private DNS domain name have been created before performing the following steps:

#. Associate a VPC with the private domain name and add record sets.

   Log in to the DNS console and associate a VPC with the private domain name.


   .. figure:: /_static/images/en-us_image_0000002250724973.png
      :alt: **Figure 1** Associating a VPC with the private domain name

      **Figure 1** Associating a VPC with the private domain name

   Click the domain name, and add a type A record set.


   .. figure:: /_static/images/en-us_image_0000002250645069.png
      :alt: **Figure 2** Adding a record set

      **Figure 2** Adding a record set

#. .. _functiongraph_03_0839__li614065010467:

   Create a function.

   Create a function whose runtime is Python 2.7. The following is sample code.

   .. code-block::

      # -*- coding:utf-8 -*-
      import json
      import os
      def handler(event, context):
           os.system("curl -iv www.test.com")

#. .. _functiongraph_03_0839__li1714025011466:

   Configure an agency with DNS and VPC permissions for the function.

   Log in to the IAM console, and configure an agency with the **DNS ReadOnlyAccess** and **VPC Administrator** permissions for FunctionGraph.


   .. figure:: /_static/images/en-us_image_0000002269988645.png
      :alt: **Figure 3** Creating an agency with DNS and VPC permissions

      **Figure 3** Creating an agency with DNS and VPC permissions

   .. note::

      You need to configure the permission to read DNS resource data because the function needs to obtain such data when resolving a domain name. Otherwise, the following error message is displayed, indicating that the DNS resource data failed to be obtained.

      .. code-block::

         2020/08/20 10:37:12 GMT+08:00  Start invoke request 'a2f105b4-2e72-4fda-94a5-86d3837e961d', version: latest
         [GET /v2/zones/{zone_id}/recordsets] failed, response: {"code":"DNS.1802","message":"Policy doesn't allow dns:recordset:list to be performed."}
         2020/08/20 10:37:13 GMT+08:00  Finish invoke request 'a2f105b4-2e72-4fda-94a5-86d3837e961d', duration: 1030.072ms, billing duration: 1100ms, memory used: 77.039MB.

#. Configure the function.

   On the details page of the function created in :ref:`step 2 <functiongraph_03_0839__li614065010467>`, click the **Configuration** tab and configure the following settings:

   a. For **Permissions**, select the agency created in :ref:`step 3 <functiongraph_03_0839__li1714025011466>`.
   b. Enable VPC access and select the created VPC, subnet, and domain name.


   .. figure:: /_static/images/en-us_image_0000002250645081.png
      :alt: **Figure 4** Configuring the function

      **Figure 4** Configuring the function

#. Check the execution result.

   All configured IPv4 domain names can be resolved.


   .. figure:: /_static/images/en-us_image_0000002215725106.png
      :alt: **Figure 5** Executing the function

      **Figure 5** Executing the function

.. note::

   Changes to the IP addresses corresponding to the VPC domain names you configure will take effect in 10 minutes.

Resolving a Private DNS Domain Name with a Container Image-based Function
-------------------------------------------------------------------------

#. Obtain a private domain name and zone ID.

   This procedure uses a domain name with a record set as an example.

   a. Log in to the DNS console.

   b. Obtain a zone ID.

      Click |image1|, and select **Domain Name** in the search box to obtain a zone ID.

   c. Obtain the private domain name corresponding to a recording set.

      Click the domain name to go to the record set list, and select a record set.

2. Compile the resolution logic.

   Use to debug the API used to `query record sets in a zone <https://docs.otc.t-systems.com/domain-name-service/api-ref/apis/record_set_management/querying_record_sets_in_a_zone.html#dns-api-64004>`__.

   -  Set **zone_id** to the zone ID obtained in the preceding step, and click **Debug**. The IP address of the private domain name is displayed in the response body.
   -  Switch to the **Sample Code** tab to obtain the complete code. For details about the dependencies, click **View SDK Details**.

.. |image1| image:: /_static/images/en-us_image_0000002248343474.png
