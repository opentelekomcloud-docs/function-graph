:original_name: functiongraph_01_0215.html

.. _functiongraph_01_0215:

Creating a Custom Policy
========================

Custom policies can be created as a supplement to the system policies of FunctionGraph.

You can create custom policies in either of the following ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

For details, see section "Creating a Custom Policy". This section introduces examples of common FunctionGraph custom policies.

Example Custom Policies
-----------------------

-  Example 1: Authorizing a user to query function code and configuration

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                     "functiongraph:function:list",
                     "functiongraph:function:getConfig",
                     "funcitongraph:function:getCode"
                  ]
               }
          ]
      }

-  Example 2: Denying function deletion

   A policy with only "Deny" permissions must be used in conjunction with other policies to take effect. If both "Allow" and "Deny" permissions are assigned to a user, the "Deny" permissions take precedence over the "Allow" permissions.

   If you need to assign permissions of the **FunctionGraph FullAccess** policy to a user but prevent the user from deleting functions, create a custom policy for denying function deletion, and attach both policies to the group to which the user belongs. In this way, the user can perform all operations on FunctionGraph except deleting functions. The following is an example of a deny policy:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              "Effect": "Deny",
              "Action": [
                  "functiongraph:function:delete"
              ]
          ]
      }

-  Example 3: Configuring permissions for specific resources

   You can grant an IAM user permissions for specific resources. For example, to grant a user permissions for the **functionname** function in the **Default** application, set **functionname** to a specified resource path, that is, **FUNCTIONGRAPH:*:*:function:Default/functionname**.

   .. note::

      Specify function resources:

      Format: **FUNCTIONGRAPH:*:*:function:** *application or function name*

      For function resources, IAM automatically generates the resource path prefix **FUNCTIONGRAPH:*:*:function:**. You can specify a resource path by adding the application or function name next to the path prefix. Wildcards (``*``) are supported. For example, **FUNCTIONGRAPH:*:*:function:Default/\*** indicates any function in the **Default** application.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "functiongraph:function:list"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "functiongraph:function:listAlias",
                      "functiongraph:function:listVersion",
                      "functiongraph:function:getConfig",
                      "functiongraph:function:getCode",
                      "functiongraph:function:updateCode",
                      "functiongraph:function:invoke",
                      "functiongraph:function:updateConfig",
                      "functiongraph:function:createVersion",
                      "functiongraph:function:updateAlias",
                      "functiongraph:function:createAlias"
                  ],
                  "Resource": [
                      "FUNCTIONGRAPH:*:*:function:Default/*"
                  ]
              }
          ]
      }
