:original_name: functiongraph_03_0840.html

.. _functiongraph_03_0840:

How Do I Use a Domain Name to Access an API Registered with API Gateway (Dedicated)?
====================================================================================

The domain name **www.test.com** is used as an example. The procedure is as follows:

#. Log in to the API Gateway console, choose **Dedicated Gateways** in the navigation pane, and click the target gateway name. On the **Gateway Information** page, view **EIP** in the **Inbound Access** area to obtain the IP address of the API gateway.
#. On the DNS console, configure an IPv4 rule for mapping **www.test.com** to an API gateway address.
#. Configure domain name resolution. In this way, you can access the API registered with the API gateway by using domain name **www.test.com**.
