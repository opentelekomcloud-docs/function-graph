:original_name: functiongraph_01_0222.html

.. _functiongraph_01_0222:

Configuring the Network
=======================

Public Access
-------------

By default, functions can access services on public networks. If the target public network service requires whitelist verification using a fixed IP address, :ref:`enable VPC access <functiongraph_01_0222__en-us_topic_0000001298507413_li10711134319497>`, configure a NAT gateway for the VPC, and bind an Elastic IP (EIP) to the gateway. For details, see :ref:`Configuring a Fixed Public IP Address <functiongraph_01_0222__en-us_topic_0000001298507413_section1888817242319>`

Configuring VPC Access
----------------------

Functions can access resources in a VPC bound to it. If a function needs both VPC and public access, configure a NAT gateway for the VPC and bind an EIP to the gateway. For details, see :ref:`Configuring a Fixed Public IP Address <functiongraph_01_0222__en-us_topic_0000001298507413_section1888817242319>`.

**Required Permissions**

Configure an agency by referring to :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.

-  Permissions for VPC access: an agency with the **VPC Administrator** permission or with the least permissions listed in :ref:`Table 1 <functiongraph_01_0222__en-us_topic_0000001298507413_table3170115712597>`

   .. _functiongraph_01_0222__en-us_topic_0000001298507413_table3170115712597:

   .. table:: **Table 1** Least permissions required

      ================= ================
      Permission        Action
      ================= ================
      Deleting a port   vpc:ports:delete
      Querying a port   vpc:ports:get
      Creating a port   vpc:ports:create
      Querying a VPC    vpc:vpcs:get
      Querying a subnet vpc:subnets:get
      ================= ================

-  Permissions for private domain name resolution: an agency with the **DNS ReadOnlyAccess** permission

**Procedure**

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. .. _functiongraph_01_0222__en-us_topic_0000001298507413_li10711134319497:

   Choose **Configuration** > **Network**, enable **VPC Access**, and specify a VPC and subnet.

   To enable **VPC Access**, you need to configure the following inbound and outbound rules in the default security group. For details, see section "Adding a Security Group Rule".

   -  Inbound rule: Set **Action** to **Allow**, **Protocol & Port** to **ICMP**, and the minimum range for **Source** to the VPC CIDR block selected for the function. For example, if the VPC CIDR block of the function is **192.168.\ x.x/24**, add an inbound rule with **Allow** for **Action**, **ICMP** for **Protocol & Port**, and **192.168.\ x.x/24** for **Source**.
   -  Outbound rule: Set **Action** to **Allow**.

   .. _functiongraph_01_0222__en-us_topic_0000001298507413_fig11843319207:

   .. figure:: /_static/images/en-us_image_0000001630849458.png
      :alt: **Figure 1** Configuring VPC access

      **Figure 1** Configuring VPC access

   .. note::

      a. For details on how to create a VPC and a subnet, see `Creating a VPC <https://docs.otc.t-systems.com/virtual-private-cloud/umn/vpc_and_subnet/vpc/creating_a_vpc.html#en-us-topic-0013935842>`__.
      b. Specify an agency with VPC administrator permissions for the function. For details, see :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.
      c. All functions of a tenant in a project can be bound to a maximum of four subnets. (Each project has a unique 32-digit project ID, which is allocated when your account is created. The project IDs of your account and IAM user are the same.)

#. .. _functiongraph_01_0222__en-us_topic_0000001298507413_li19413205719162:

   (Optional) Configure the domain name.

   Enter one or more private domain names of the VPC so that the function can use them to access resources in this VPC. See :ref:`Figure 1 <functiongraph_01_0222__en-us_topic_0000001298507413_fig11843319207>`.

   .. note::

      a. For details about how to create a private domain name, see `Creating a Private Zone <https://docs.otc.t-systems.com/domain-name-service/umn/private_zones/creating_a_private_zone.html#en-us-topic-0057773658>`__.
      b. Functions can resolve only domain names of the A record set type. For details about how to add a record set, see `Record Set Types and Configuration Rules <https://docs.otc.t-systems.com/domain-name-service/umn/record_sets/adding_record_sets/record_set_types_and_configuration_rules.html#dns-usermanual-0601>`__.

#. (Optional) Configure the VPC CIDR block.

   .. _functiongraph_01_0222__en-us_topic_0000001298507413_fig5838194095016:

   .. figure:: /_static/images/en-us_image_0000002223713009.png
      :alt: **Figure 2** VPC CIDR block

      **Figure 2** VPC CIDR block

   .. note::

      -  You can enter the VPC CIDR block used in the code to check whether it conflicts with FunctionGraph's VPC CIDR block.

#. Click **Save**.

.. _functiongraph_01_0222__en-us_topic_0000001298507413_section1888817242319:

Configuring a Fixed Public IP Address
-------------------------------------

If a function needs to access public network resources in a VPC or requires a fixed public IP address, configure a NAT gateway for the VPC and bind an EIP to the gateway.

**Prerequisites**

#. You have created a VPC and a subnet according to `Creating a VPC <https://docs.otc.t-systems.com/virtual-private-cloud/umn/vpc_and_subnet/vpc/creating_a_vpc.html#en-us-topic-0013935842>`__.
#. You have obtained an EIP according to `Assigning an EIP <https://docs.otc.t-systems.com/elastic-ip/umn/elastic_ip/assigning_an_eip_and_binding_it_to_an_ecs.html>`__.

**Procedure**

#. In the left navigation pane of the management console, choose **Network** > **NAT Gateway** to go to the NAT Gateway console. Then click **Create NAT Gateway**.
#. On the displayed page, enter gateway information, select a VPC (for example, **vpc-01**) and subnet, and confirm and submit the settings. For details, see `Creating a Public NAT Gateway <https://docs.otc.t-systems.com/nat-gateway/umn/managing_nat_gateways/creating_a_public_nat_gateway.html>`__.
#. Click the NAT gateway name. On the details page that is displayed, click `Add SNAT Rule <https://docs.otc.t-systems.com/nat-gateway/umn/managing_snat_rules/adding_an_snat_rule.html#en-us-topic-0127489529>`__, set the rule, and click **OK**.
