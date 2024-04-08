:original_name: functiongraph_03_0834.html

.. _functiongraph_03_0834:

How Do I Configure External Network Access?
===========================================

By default, functions deployed in a VPC are isolated from the Internet. If a function needs to access both internal and external networks, add a NAT gateway for the VPC.

**Prerequisites**

#. You have created a VPC and subnet according to section "Creating a VPC".
#. You have obtained an elastic IP address according to section "Assigning an EIP".

**Procedure of Creating a NAT Gateway**

#. Log in to the NAT Gateway console, and click **Create NAT Gateway**.
#. On the displayed page, enter gateway information, select a VPC and subnet (for example, **vpc-01**), and confirm and submit the settings to create a NAT gateway. For details, see section "Creating a NAT Gateway".
#. Click the NAT gateway name. On the details page that is displayed, click **Add an SNAT Rule** and click **OK**.
