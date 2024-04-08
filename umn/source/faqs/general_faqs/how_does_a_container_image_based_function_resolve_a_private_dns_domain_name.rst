:original_name: functiongraph_03_0872.html

.. _functiongraph_03_0872:

How Does a Container Image-based Function Resolve a Private DNS Domain Name?
============================================================================

FunctionGraph functions created with a container image cannot directly parse private Domain Name Service (DNS) domain names. However, you can call DNS APIs to achieve this purpose.

Resolving a Private DNS Domain Name
-----------------------------------

#. Obtain a private domain name and zone ID.

   This procedure uses a domain name with a record set as an example.

   a. Log in to the DNS console.

   b. Obtain a zone ID.

      Click |image1|, and select **Domain Name** in the search box to obtain a zone ID.

   c. Obtain the private domain name corresponding to a recording set.

      Click the domain name to go to the record set list, and select a record set.

2. Compile the resolution logic.

   Debug the API used to query record sets in a zone.

   -  Set **zone_id** to the zone ID obtained in the preceding step, and click **Debug**. The IP address of the private domain name is displayed in the response body.
   -  Switch to the **Sample Code** tab to obtain the complete code. For details about the dependencies, click **View SDK Details**.

.. |image1| image:: /_static/images/en-us_image_0000001382229680.gif
