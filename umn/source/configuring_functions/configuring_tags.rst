:original_name: functiongraph_01_1839.html

.. _functiongraph_01_1839:

Configuring Tags
================

Introduction
------------

Tags help you identify your cloud resources. When you have many cloud resources of the same type, you can use tags to classify them by dimension (for example, use, owner, or environment).

Add tags for a function on the **Configuration** tab page. Each function can have a maximum of 20 tags.

Scenario
--------

Tags help you identify and manage your function resources. For example, you can define a set of tags for function resources in your account to track the owner and usage of each function resource.

Prerequisites
-------------

You have enabled Tag Management Service (TMS), or the pre-defined tags cannot be used. For details, see `Permission Management <https://docs.otc.t-systems.com/tag-management-service/umn/product_profile/permissions.html#tms-01-0009>`__.

Adding a Tag
------------

#. Log in to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.

#. Click the function to be configured to go to the function details page.

#. Choose **Configuration** > **Tags**, click **Edit Tag**, and click **Add Tag**.

#. Add a tag key and value that meet the following rules:

   -  Each tag consists of a key-value pair. Each key must be unique and have only one value.
   -  Each function can have a maximum of 20 tags.

      .. note::

         If your organization has configured tag policies for FunctionGraph, add tags to functions based on the policies. If a tag does not comply with the tag policies, function creation may fail. Contact your administrator to learn more about tag policies.

      .. table:: **Table 1** Tag naming rules

         +-----------------------------------+----------------------------------------------------------------------------------+
         | Parameter                         | Rule                                                                             |
         +===================================+==================================================================================+
         | Key                               | -  Cannot be empty.                                                              |
         |                                   | -  Cannot start with **\_sys\_** or a space, or end with a space.                |
         |                                   | -  Can contain UTF-8 letters, digits, spaces, and these characters: \_.:=+-@     |
         |                                   | -  Must be unique and cannot exceed 128 characters.                              |
         +-----------------------------------+----------------------------------------------------------------------------------+
         | Value                             | -  Can be an empty string.                                                       |
         |                                   | -  Can contain UTF-8 letters, digits, spaces, and these characters: ``_.:/=+-@`` |
         |                                   | -  Max. 255 characters.                                                          |
         +-----------------------------------+----------------------------------------------------------------------------------+

#. Click **Save**.

   Tag values can be modified but tag keys cannot.

Searching for Functions by Tag
------------------------------

#. Return to the FunctionGraph console. In the navigation pane, choose **Functions** > **Function List**.
#. In the search box, select the **Tag** filter, and then select one or more key-value pairs.
#. (Optional) Add more filters, such as runtime and package type.
#. View the search result in the function list.
