:original_name: functiongraph_03_0843.html

.. _functiongraph_03_0843:

Why Is Message "failed to mount exist system path" Displayed?
=============================================================

When you see this message, mount the file to a new path.

User ID/user group ID: Can be any number except 1000. The value **-1** will be automatically converted to **1003**. The two IDs control the directory permissions for accessing a remote file system.

File system/ECS name: Name of the file system or ECS to create. Ensure that you have specified a VPC and agency that you have been authorized to access.

Shared directory: To configure a remote shared directory for the mounted ECS, see section "Creating an NFS Shared Directory on an ECS".

Access path: Location where the file system is to be mounted in the function. Set a new two-level directory that starts with **/mnt**. For example, **/mnt/test**.
