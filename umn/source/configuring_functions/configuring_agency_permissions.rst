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

   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenario                               | Admin Permission              | Fine-Grained Minimum Permission                                                                                                                                                      | Description                                                                                                                                                                                                                                          |
   +========================================+===============================+======================================================================================================================================================================================+======================================================================================================================================================================================================================================================+
   | Using a custom image                   | SWR Administrator             | Unavailable                                                                                                                                                                          | SWR Admin: administrator who has all permissions for the Software Repository for Container (SWR) service.                                                                                                                                            |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      | For details about how to create a custom image, see :ref:`Deploying a Function Using a Container Image <functiongraph_01_1047>`.                                                                                                                     |
   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mounting an SFS Turbo file system      | SFS Turbo ReadOnlyAccess      | sfsturbo:shares:getShare (Query details about a file system)                                                                                                                         | SFS Turbo ReadOnlyAccess: read-only permissions for SFS Turbo.                                                                                                                                                                                       |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               | sfsturbo:shares:showFsDir (Check whether a directory exists)                                                                                                                         | sfsturbo:shares:getShare: permission for querying a file system in SFS.                                                                                                                                                                              |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      | sfsturbo:shares:showFsDir: permission for checking whether a directory exists in SFS.                                                                                                                                                                |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      | For details about how to mount an SFS Turbo file system, see :ref:`Mounting an SFS Turbo File System <functiongraph_01_0402__en-us_topic_0000001298786853_section457221344513>`.                                                                     |
   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mounting an ECS shared directory       | ECS ReadOnlyAccess            | ecs:cloudServers:get (Query details about an ECS)                                                                                                                                    | ECS ReadOnlyAccess: read-only permissions for ECS.                                                                                                                                                                                                   |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      | ecs:cloudServers:get: permission for querying an ECS.                                                                                                                                                                                                |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      | For details about how to mount an ECS shared directory, see :ref:`Mounting an ECS Shared Directory <functiongraph_01_0402__en-us_topic_0000001298786853_section11158112711472>`.                                                                     |
   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Configuring a reserved instance policy | AOM ReadOnlyAccess            | aom:metric:get (Query a metric)                                                                                                                                                      | AOM ReadOnlyAccess: read-only permissions for AOM.                                                                                                                                                                                                   |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               | aom:metric:list (Query metric list)                                                                                                                                                  | aom:metric:get: permissions for querying a metric in AOM.                                                                                                                                                                                            |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      | aom:metric:list: permissions for querying metric list in AOM.                                                                                                                                                                                        |
   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Using a DIS trigger                    | DIS Administrator             | Unavailable                                                                                                                                                                          | Administrator who has all permissions for the DIS service.                                                                                                                                                                                           |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      | For details about how to create a DIS trigger, see :ref:`Using a DIS Trigger <functiongraph_01_0206>`.                                                                                                                                               |
   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Using a DMS trigger                    | DMS ReadOnlyAccess            | dms:instance:get (Query instance details)                                                                                                                                            | DMS ReadOnlyAccess: read-only permissions for DMS.                                                                                                                                                                                                   |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      | dms:instance:get: permissions for querying instance details in DMS.                                                                                                                                                                                  |
   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Configuring cross-domain VPC access    | VPC Administrator             | vpc:ports:get (Query a port)                                                                                                                                                         | Users with the **VPC Administrator** permissions can perform any operations on all cloud resources of the VPC. To configure cross-VPC access, specify an agency with VPC management permissions.                                                     |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               | vpc:ports:create (Create a port)                                                                                                                                                     | Fine-grained minimum permission for VPC: permissions for unbinding a virtual IP address from a VM, querying a port, creating a port, querying a VPC, querying a subnet, and querying security groups or details about a security group.              |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               | vpc:vpcs:get (Query a VPC)                                                                                                                                                           | For details about how to configure cross-domain VPC access, see :ref:`Configuring the Network <functiongraph_01_0222>`.                                                                                                                              |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               | vpc:subnets:get (Query a subnet)                                                                                                                                                     |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               | vpc:vips:delete (Unbind a virtual IP address from a VM)                                                                                                                              |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               | vpc:securityGroups:get (Query security groups or details about a security group)                                                                                                     |                                                                                                                                                                                                                                                      |
   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Configuring asynchronous notification  | If the target service is OBS: | obs:bucket:HeadBucket (Obtain bucket metadata)                                                                                                                                       | OBS Administrator: administrator who has all permissions for OBS.                                                                                                                                                                                    |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        | OBS Administrator             | obs:bucket:CreateBucket (Create a bucket)                                                                                                                                            | Fine-grained minimum permission for OBS: permissions for obtaining bucket metadata, creating a bucket, uploading objects using POST method, copying objects, appending an object, initializing a multipart task, uploading parts, and merging parts. |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               | obs:object:PutObject (Upload objects using PUT method, upload objects using POST method, copy objects, append an object, initialize a multipart task, upload parts, and merge parts) | For details about how to configure asynchronous notification, see :ref:`Configuring Asynchronous Execution Notification <functiongraph_01_0390_03>`.                                                                                                 |
   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                        | If the target service is SMN: | smn:topic:publish (Publish a message)                                                                                                                                                | SMN Administrator: administrator who has all permissions for SMN.                                                                                                                                                                                    |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        | SMN Administrator             | smn:topic:list (Query the topic list)                                                                                                                                                | Fine-grained minimum permission for using SMN: permissions for publishing a message and querying the topic list.                                                                                                                                     |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        |                               |                                                                                                                                                                                      | For details about how to configure asynchronous notification, see :ref:`Configuring Asynchronous Execution Notification <functiongraph_01_0390_03>`.                                                                                                 |
   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                        | If the target service is DIS: | Unavailable                                                                                                                                                                          | DIS Administrator: administrator who has all permissions for DIS.                                                                                                                                                                                    |
   |                                        |                               |                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
   |                                        | DIS Administrator             |                                                                                                                                                                                      | For details about how to configure asynchronous notification, see :ref:`Configuring Asynchronous Execution Notification <functiongraph_01_0390_03>`.                                                                                                 |
   +----------------------------------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _functiongraph_01_0920__en-us_topic_0000001298507433_section17872123319473:

Creating an Agency
------------------

.. note::

   In the following example, the **VPC Administrator** permission is assigned to FunctionGraph and this setting takes effect only in the authorized regions.

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

4. Click **Next**. On the displayed page, search for the permissions to be added in the search box on the right and select the permissions. The **VPC Administrator** permission is used as an example.


   .. figure:: /_static/images/en-us_image_0000001630365702.png
      :alt: **Figure 3** Selecting policies

      **Figure 3** Selecting policies

   .. table:: **Table 2** Example of agency permissions

      ================= =================
      Policy Name       Scenario
      ================= =================
      VPC Administrator VPC administrator
      ================= =================

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
