:original_name: functiongraph_01_0141.html

.. _functiongraph_01_0141:

Creating a User and Granting Permissions
========================================

This section describes how to use Identity and Access Management (IAM) to implement fine-grained permissions control for your FunctionGraph resources. With IAM, you can:

-  Create IAM users for employees based on the organizational structure of your enterprise. Each IAM user has their own security credentials for accessing FunctionGraph resources.
-  Grant only the permissions required for users to perform a task.
-  Entrust other accounts or cloud services to perform professional and efficient O&M on your FunctionGraph resources.

If your account does not need individual IAM users, then you may skip over this chapter.

This section describes the procedure for granting permissions. For details, see :ref:`Figure 1 <functiongraph_01_0141__en-us_topic_0000001252067212_fig484754213103>`.

Prerequisites
-------------

Before assigning permissions to user groups, you should learn about the system permissions listed in "Permissions Management" in the *FunctionGraph Service Overview*. For the system policies of other services, see section "Permissions".

Process
-------

.. _functiongraph_01_0141__en-us_topic_0000001252067212_fig484754213103:

.. figure:: /_static/images/en-us_image_0000001252067292.png
   :alt: **Figure 1** Process for granting FunctionGraph permissions

   **Figure 1** Process for granting FunctionGraph permissions

#. .. _functiongraph_01_0141__en-us_topic_0000001252067212_li1113720874811:

   .

   Create a user group on the IAM console, and assign the **FunctionGraph Invoker** role to the group.

#. .

   Create a user on the IAM console and add the user to the group created in :ref:`1 <functiongraph_01_0141__en-us_topic_0000001252067212_li1113720874811>`.

#. and Verifying Permissions

   Log in to the management console as the created user and check whether this user only has read permissions for FunctionGraph:

   -  Choose **Service List** > **FunctionGraph** to access the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**. Then click **Create Function**. If a message appears indicating insufficient permissions to perform the operation, the **FunctionGraph Invoker** role has already taken effect.
   -  Choose any other service in the **Service List**. If a message appears indicating insufficient permissions to access the service, the **FunctionGraph Invoker** role has already taken effect.
