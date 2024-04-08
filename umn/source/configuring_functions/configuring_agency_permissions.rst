:original_name: functiongraph_01_0920.html

.. _functiongraph_01_0920:

Configuring Agency Permissions
==============================

Overview
--------

FunctionGraph works with other cloud services in most scenarios. Create a cloud service agency so that FunctionGraph can perform resource O&M in other cloud services on your behalf.

Scenario
--------

Before using FunctionGraph in the following scenarios, :ref:`create an agency <functiongraph_01_0920__en-us_topic_0000001298507433_section17872123319473>`. Adjust the permissions granted to the agency to meet your service requirements. For example, grant the Admin permission in the development phase, and **change it to the fine-grained minimum permission in the product environment**. This ensures the required permissions while eliminating risks. Select the required action by referring to :ref:`Table 1 <functiongraph_01_0920__en-us_topic_0000001298507433_table375913368504>`.

.. _functiongraph_01_0920__en-us_topic_0000001298507433_table375913368504:

.. table:: **Table 1** Common actions

   +-------------------------------------+-------------------------------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenario                            | Admin Permission                          | Fine-Grained Minimum Permission                                                            | Description                                                                                                                                                                                        |
   +=====================================+===========================================+============================================================================================+====================================================================================================================================================================================================+
   | Using a custom image                | SWR Admin                                 | Unavailable                                                                                | SWR Admin: administrator who has all permissions for the SoftWare Repository for Container (SWR) service.                                                                                          |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           |                                                                                            | For details about how to create a custom image, see :ref:`Deploying a Function Using a Container Image <functiongraph_01_1047>`.                                                                   |
   +-------------------------------------+-------------------------------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mounting an SFS Turbo file system   | SFS Administrator or Tenant administrator | sfsturbo:shares:getShare (Query details about a file system)                               | SFS Administrator: administrator who has all permissions for the Scalable File Service (SFS) service.                                                                                              |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           |                                                                                            | Tenant administrator: administrator for all cloud services except IAM. This user can perform any operations on all cloud resources of the enterprise.                                              |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           |                                                                                            | sfsturbo:shares:getShare: permission for querying a file system in SFS.                                                                                                                            |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           |                                                                                            | For details about how to mount an SFS Turbo file system, see :ref:`Mounting an SFS Turbo File System <functiongraph_01_0402__en-us_topic_0000001298786853_section457221344513>`.                   |
   +-------------------------------------+-------------------------------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mounting an ECS shared directory    | Tenant Guest and VPC Administrator        | ecs:cloudServers:get (Query details about an ECS)                                          | Tenant Guest: user with read-only permissions for all cloud services (except IAM)                                                                                                                  |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           |                                                                                            | VPC Administrator: network administrator                                                                                                                                                           |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           |                                                                                            | ecs:cloudServers:get: permission for querying an ECS.                                                                                                                                              |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           |                                                                                            | For details about how to mount an ECS shared directory, see :ref:`Mounting an ECS Shared Directory <functiongraph_01_0402__en-us_topic_0000001298786853_section11158112711472>`.                   |
   +-------------------------------------+-------------------------------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Using a DIS trigger                 | DIS Administrator                         | Unavailable                                                                                | Administrator who has all permissions for the DIS service.                                                                                                                                         |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           |                                                                                            | For details about how to create a DIS trigger, see :ref:`Using a DIS Trigger <functiongraph_01_0206>`.                                                                                             |
   +-------------------------------------+-------------------------------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Configuring cross-domain VPC access | VPC Administrator                         | vpc:ports:delete (Delete a port)                                                           | Users with the **VPC Administrator** permissions can perform any operations on all cloud resources of the VPC. To configure cross-VPC access, specify an agency with VPC management permissions.   |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           | vpc:ports:get (Query a port)                                                               | Fine-grained minimum permission for VPC: permission for deleting, querying, or creating a port, or querying a VPC or subnet.                                                                       |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           | vpc:ports:create (Create a port)                                                           | For details about how to configure cross-domain VPC access, see :ref:`Configuring the Network <functiongraph_01_0222>`.                                                                            |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           | vpc:vpcs:get (Query a VPC)                                                                 |                                                                                                                                                                                                    |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           | vpc:subnets:get (Query a subnet)                                                           |                                                                                                                                                                                                    |
   +-------------------------------------+-------------------------------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Creating an OBS bucket and trigger  | Tenant Administrator                      | obs:bucket:GetBucketLocation (Query a bucket location)                                     | Tenant administrator: administrator for all cloud services except IAM. This user can perform any operations on all cloud resources of the enterprise.                                              |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           | obs:bucket:ListAllMyBuckets (Query buckets)                                                | Fine-grained minimum permission for OBS: permission for querying a bucket location, buckets, or the event notification configuration of a bucket, or configuring event notifications for a bucket. |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           | obs:bucket:GetBucketNotification (Obtain the event notification configuration of a bucket) | For details about how to create an OBS trigger, see :ref:`Using an OBS Trigger <functiongraph_01_0205>`.                                                                                           |
   |                                     |                                           |                                                                                            |                                                                                                                                                                                                    |
   |                                     |                                           | obs:bucket:PutBucketNotification (Configure event notifications for a bucket)              |                                                                                                                                                                                                    |
   +-------------------------------------+-------------------------------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _functiongraph_01_0920__en-us_topic_0000001298507433_section17872123319473:

Creating an Agency
------------------

.. note::

   In the following example, the **Tenant Administrator** permission is assigned to FunctionGraph and this setting takes effect only in the authorized regions.

Create an agency by referring to section "Creating an Agency" and set parameters as follows:

#. Log in to the IAM console.

#. .. _functiongraph_01_0920__en-us_topic_0000001298507433_li6655512174612:

   On the IAM console, choose **Agencies** from the navigation pane, and click **Create Agency** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000001630843130.png
      :alt: **Figure 1** Creating an agency

      **Figure 1** Creating an agency

#. Configure the agency.


   .. figure:: /_static/images/en-us_image_0000001678804153.png
      :alt: **Figure 2** Setting basic information

      **Figure 2** Setting basic information

   -  For **Agency Name**, enter **serverless-trust**.
   -  For **Agency Type**, select **Cloud service**.
   -  For **Cloud Service**, select **FunctionGraph**.
   -  For **Validity Period**, select **Unlimited**.
   -  **Description**: Enter the description.

4. Click **Next**. On the displayed page, search for the permissions to be added in the search box on the right and select the permissions. The **Tenant Administrator** permission is used as an example.


   .. figure:: /_static/images/en-us_image_0000001630365702.png
      :alt: **Figure 3** Selecting policies

      **Figure 3** Selecting policies

   .. table:: **Table 2** Example of agency permissions

      +----------------------+---------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name          | Scenario                                                                                                                        |
      +======================+=================================================================================================================================+
      | Tenant Administrator | Administrator for all cloud services except IAM. This user can perform any operations on all cloud resources of the enterprise. |
      +----------------------+---------------------------------------------------------------------------------------------------------------------------------+

5. .. _functiongraph_01_0920__en-us_topic_0000001298507433_li18932831837:

   Click **Next** and select the scope.


   .. figure:: /_static/images/en-us_image_0000001679086013.png
      :alt: **Figure 4** Selecting the required permissions

      **Figure 4** Selecting the required permissions

Configuring an Agency
---------------------

#. In the left navigation pane of the management console, choose **Compute** > **FunctionGraph**. On the FunctionGraph console, choose **Functions** > **Function List** from the navigation pane.
#. Click the function to be configured to go to the function details page.
#. Choose **Configuration** > **Permissions**, click **Create Agency**, and set an agency based on site requirements by referring to :ref:`2 <functiongraph_01_0920__en-us_topic_0000001298507433_li6655512174612>`\ ``-``\ :ref:`5 <functiongraph_01_0920__en-us_topic_0000001298507433_li18932831837>`.

   .. table:: **Table 3** Agency configuration parameters

      +----------------------+---------------------------------------------------------------------------------+
      | Parameter            | Description                                                                     |
      +======================+=================================================================================+
      | Configuration Agency | Select a function that you have created.                                        |
      +----------------------+---------------------------------------------------------------------------------+
      | Execution Agency     | Mandatory if you select **Specify an exclusive agency for function execution**. |
      +----------------------+---------------------------------------------------------------------------------+

   .. note::

      -  To ensure optimal performance, select **Specify an exclusive agency for function execution** and set different agencies for function configuration and execution. You can also use no agency or specify the same agency for both purposes. :ref:`Figure 5 <functiongraph_01_0920__en-us_topic_0000001298507433_fig822424719482>` shows the agency options.

         .. _functiongraph_01_0920__en-us_topic_0000001298507433_fig822424719482:

         .. figure:: /_static/images/en-us_image_0000001679087833.png
            :alt: **Figure 5** Setting agencies

            **Figure 5** Setting agencies

      -  **Configuration Agency**: For example, to create Data Ingestion Service (DIS) triggers, first specify an agency with DIS permissions. If such an agency is not specified or the specified agency does not exist, no DIS triggers can be created.

      -  **Execution Agency**: This type of agency enables you to obtain a token and AK/SK from the context in the function handler for accessing other cloud services.

4. Click **Save**.

Modifying an Agency
-------------------

Modifying an agency: You can modify the permissions, validity period, and description of an agency on the IAM console.

.. caution::

   -  After an agency is modified, it takes about 10 minutes for the modification (for example, **context.getToken**) to take effect.
   -  The agency information obtained using the **context** method is valid for 24 hours. Refresh it before it expires.
