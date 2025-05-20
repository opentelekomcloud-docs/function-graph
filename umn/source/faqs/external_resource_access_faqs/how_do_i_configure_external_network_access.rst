:original_name: functiongraph_03_0834.html

.. _functiongraph_03_0834:

How Do I Configure External Network Access?
===========================================

By default, functions deployed in a VPC are isolated from the Internet. If a function needs to access both internal and external networks, add a NAT gateway for the VPC.

**Prerequisites**

#. You have created a VPC and subnet according to `Creating a VPC <https://docs.otc.t-systems.com/virtual-private-cloud/umn/vpc_and_subnet/vpc/creating_a_vpc.html#>`__.
#. You have obtained an elastic IP address according to `Assigning an EIP <https://docs.otc.t-systems.com/elastic-ip/umn/elastic_ip/assigning_an_eip_and_binding_it_to_an_ecs.html#>`__.

**Procedure of Creating a NAT Gateway**

#. Log in to the NAT Gateway console, and click **Create NAT Gateway**.
#. On the displayed page, enter gateway information, select a VPC and subnet (for example, **vpc-01**), and confirm and submit the settings to create a NAT gateway. For details, see `Creating a NAT Gateway <https://docs.otc.t-systems.com/nat-gateway/umn/managing_nat_gateways/creating_a_public_nat_gateway.html>`__.
#. Click the NAT gateway name. On the details page that is displayed, click `Add an SNAT Rule <https://docs.otc.t-systems.com/nat-gateway/umn/managing_snat_rules/adding_an_snat_rule.html#en-us-topic-0127489529>`__ and click **OK**.
