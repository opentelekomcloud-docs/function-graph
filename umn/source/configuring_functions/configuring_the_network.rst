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


   .. figure:: /_static/images/en-us_image_0000001630849458.png
      :alt: **Figure 1** Configuring VPC access

      **Figure 1** Configuring VPC access

   .. note::

      a. For details on how to create a VPC and a subnet, see section "Creating a VPC".
      b. Specify an agency with VPC administrator permissions for the function. For details, see :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.
      c. You can bind functions in a project to up to four different subnets in any VPCs. (Each project has a unique 32-digit project ID, which is allocated when your account is created. The project IDs of your account and IAM user are the same.)

#. Click **Save**.

.. _functiongraph_01_0222__en-us_topic_0000001298507413_section1888817242319:

Configuring a Fixed Public IP Address
-------------------------------------

If a function needs to access public network resources in a VPC or requires a fixed public IP address, configure a NAT gateway for the VPC and bind an EIP to the gateway.

**Prerequisites**

#. You have created a VPC and a subnet according to section "Creating a VPC".
#. You have obtained an EIP according to section "Assigning an EIP".

**Procedure**

#. In the left navigation pane of the management console, choose **Network** > **NAT Gateway** to go to the NAT Gateway console. Then click **Create NAT Gateway**.
#. On the displayed page, enter gateway information, select a VPC (for example, **vpc-01**) and subnet, and confirm and submit the settings. For details, see section "Creating a Public NAT Gateway".
#. Click the NAT gateway name. On the details page that is displayed, click **Add SNAT Rule**, set the rule, and click **OK**.
