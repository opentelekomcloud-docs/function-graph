:original_name: functiongraph_01_0160_0.html

.. _functiongraph_01_0160_0:

Permissions Management
======================

If you need to assign different permissions to employees in your enterprise to access your FunctionGraph resources, IAM is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your cloud resources.

With IAM, you can use your account to create IAM users for your employees, and assign permissions to the users to control their access to specific resource types. For example, some software developers in your enterprise need to use FunctionGraph resources but must not delete them or perform any high-risk operations. To achieve this result, you can create IAM users for the software developers and grant them only the permissions required for using FunctionGraph resources.

If your account does not need individual IAM users for permissions management, you may skip over this chapter.

FunctionGraph Permissions
-------------------------

By default, new IAM users do not have any permissions assigned. You need to add a user to one or more groups, and assign permissions policies to these groups. The user then inherits permissions from the groups it is a member of. This process is called authorization. After authorization, the user can perform specified operations on FunctionGraph based on the permissions.

FunctionGraph is a project-level service deployed and accessed in specific physical regions. To assign FunctionGraph permissions to a user group, specify the scope as region-specific projects and select projects in relevant regions for the permissions to take effect. If **All projects** is selected, the permissions will take effect for the user group in all region-specific projects. When accessing FunctionGraph, the users need to switch to a region where they have been authorized to use the FunctionGraph service.

You can grant users permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you may also need to assign other roles on which the permissions depend. However, roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control.

:ref:`Table 1 <functiongraph_01_0160_0__en-us_topic_0000001257180285_table1181710783714>` lists all the system policies supported by FunctionGraph.

.. _functiongraph_01_0160_0__en-us_topic_0000001257180285_table1181710783714:

.. table:: **Table 1** Permissions description

   +--------------------------------+---------------------------------------------------------------------------------------+-----------------------+------------+
   | Role/Policy Name               | Description                                                                           | Category              | Dependency |
   +================================+=======================================================================================+=======================+============+
   | FunctionGraph FullAccess       | This policy grants all permissions for FunctionGraph.                                 | System-defined policy | N/A        |
   +--------------------------------+---------------------------------------------------------------------------------------+-----------------------+------------+
   | FunctionGraph ReadOnlyAccess   | This policy grants read-only permissions for FunctionGraph.                           | System-defined policy | N/A        |
   +--------------------------------+---------------------------------------------------------------------------------------+-----------------------+------------+
   | FunctionGraph CommonOperations | This policy grants permissions to query functions and triggers, and invoke functions. | System-defined policy | N/A        |
   +--------------------------------+---------------------------------------------------------------------------------------+-----------------------+------------+

.. note::

   If an IAM user granted the **FunctionGraph FullAccess** permission has no permission to create a certain type of trigger or use a certain function, the relevant service or function does not support fine-grained authentication. In this case, grant the admin permission for this service or function to the user. These services and functions include:

   -  CTS and DIS: These do not support fine-grained authentication. Add the admin permission for them.
   -  SMN: This supports fine-grained authentication in some regions. If needed, add the admin permission for this service.

   For more information about the permissions required to use these triggers and relevant functions, see :ref:`Table 2 <functiongraph_01_0160_0__en-us_topic_0000001257180285_table10526732619>`.

.. _functiongraph_01_0160_0__en-us_topic_0000001257180285_table10526732619:

.. table:: **Table 2** Permissions required to use triggers and relevant functions

   +-----------------------------------+-----------------------------------+
   | Trigger/Function                  | Permission                        |
   +===================================+===================================+
   | APIG (dedicated)                  | apig:instances:get                |
   |                                   |                                   |
   |                                   | apig:instances:create             |
   |                                   |                                   |
   |                                   | apig:instances:update             |
   |                                   |                                   |
   |                                   | apig:instances:list               |
   |                                   |                                   |
   |                                   | apig:sharedInstance:operate       |
   +-----------------------------------+-----------------------------------+
   | CTS                               | cts:notification:create           |
   |                                   |                                   |
   |                                   | cts:notification:delete           |
   |                                   |                                   |
   |                                   | cts:notification:update           |
   |                                   |                                   |
   |                                   | cts:operation:list                |
   |                                   |                                   |
   |                                   | cts:tracker:list                  |
   |                                   |                                   |
   |                                   | cts:trace:list                    |
   +-----------------------------------+-----------------------------------+
   | DDS                               | dds:instance:get                  |
   |                                   |                                   |
   |                                   | dds:instance:list                 |
   +-----------------------------------+-----------------------------------+
   | DIS                               | dis:streams:list                  |
   +-----------------------------------+-----------------------------------+
   | LTS                               | lts:groups:create                 |
   |                                   |                                   |
   |                                   | lts:groups:get                    |
   |                                   |                                   |
   |                                   | lts:groups:list                   |
   |                                   |                                   |
   |                                   | lts:groups:put                    |
   |                                   |                                   |
   |                                   | lts:logstreams:delete             |
   |                                   |                                   |
   |                                   | lts:logstreams:list               |
   |                                   |                                   |
   |                                   | lts:topics:get                    |
   |                                   |                                   |
   |                                   | lts:subscriptions:create          |
   |                                   |                                   |
   |                                   | lts:subscriptions:delete          |
   |                                   |                                   |
   |                                   | lts:subscriptions:put             |
   |                                   |                                   |
   |                                   | lts:structConfig:create           |
   |                                   |                                   |
   |                                   | lts:structConfig:get              |
   +-----------------------------------+-----------------------------------+
   | OBS                               | obs:bucket:GetBucketLocation      |
   |                                   |                                   |
   |                                   | obs:bucket:GetBucketNotification  |
   |                                   |                                   |
   |                                   | obs:bucket:PutBucketNotification  |
   |                                   |                                   |
   |                                   | obs:bucket:ListBucket             |
   +-----------------------------------+-----------------------------------+
   | SMN                               | smn:topic:list                    |
   |                                   |                                   |
   |                                   | smn:topic:update                  |
   +-----------------------------------+-----------------------------------+

:ref:`Table 3 <functiongraph_01_0160_0__en-us_topic_0000001257180285_table157711141155617>` lists the common operations supported by each system-defined policy of FunctionGraph. Please choose proper system-defined policies according to this table.

.. _functiongraph_01_0160_0__en-us_topic_0000001257180285_table157711141155617:

.. table:: **Table 3** Common operations supported by each system-defined policy

   +--------------------------+------------------------------+--------------------------------+--------------------------+
   | Operation                | FunctionGraph ReadOnlyAccess | FunctionGraph CommonOperations | FunctionGraph FullAccess |
   +==========================+==============================+================================+==========================+
   | Creating functions       | x                            | x                              | Y                        |
   +--------------------------+------------------------------+--------------------------------+--------------------------+
   | Querying functions       | Y                            | Y                              | Y                        |
   +--------------------------+------------------------------+--------------------------------+--------------------------+
   | Modifying functions      | x                            | x                              | Y                        |
   +--------------------------+------------------------------+--------------------------------+--------------------------+
   | Deleting functions       | x                            | x                              | Y                        |
   +--------------------------+------------------------------+--------------------------------+--------------------------+
   | Invoking functions       | x                            | Y                              | Y                        |
   +--------------------------+------------------------------+--------------------------------+--------------------------+
   | Querying function logs   | Y                            | Y                              | Y                        |
   +--------------------------+------------------------------+--------------------------------+--------------------------+
   | Viewing function metrics | Y                            | Y                              | Y                        |
   +--------------------------+------------------------------+--------------------------------+--------------------------+
