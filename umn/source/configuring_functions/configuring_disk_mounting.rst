:original_name: functiongraph_01_0402.html

.. _functiongraph_01_0402:

Configuring Disk Mounting
=========================

Introduction
------------

FunctionGraph allows you to mount file systems to your functions. Multiple functions can share the same file system. This greatly expands the function execution and storage space compared with the temporary disk space allocated to a function.

Scenarios
---------

FunctionGraph supports the following types of file systems:

-  SFS Turbo

   SFS Turbo supports the following storage classes: Standard (500 GB-32 TB), Standard-Enhanced (10 TB-320 TB), Performance (500 GB-32 TB), and Performance-Enhanced (10 TB-320 TB). SFS Turbo is expandable to 320 TB, and provides fully hosted shared file storage. It features high availability and durability, and supports massive quantities of small files and applications requiring low latency and high input/output operations per second (IOPS). SFS Turbo is suitable for high-performance websites, log storage, compression and decompression, DevOps, enterprise offices, and containerized applications. For details, see `SFS Service Overview <https://docs.otc.t-systems.com/scalable-file-service/umn/introduction/file_system_types.html>`__.

-  ECS

   A directory on an ECS is specified as a shared file system (see :ref:`Mounting an ECS Shared Directory <functiongraph_01_0402__en-us_topic_0000001298786853_section11158112711472>`) by using the network file system (NFS) service. The directory can then be mounted to a function in the same VPC as the ECS so that the function can read and write data in the directory. ECS file systems make it possible for dynamic expansion of compute resources. This type of file system is suitable for low service demand scenarios.

Benefits from using these file systems:

-  The function execution space can be greatly expanded comparing with **/tmp**.
-  A file system can be shared by multiple functions.
-  ECS compute resources can be dynamically expanded and existing ECS storage capability can be used to achieve stronger computing performance.

   .. note::

      You can write temporary files in the **/tmp** directory. The total size of these files cannot exceed 10,240 MB.

.. _functiongraph_01_0402__en-us_topic_0000001298786853_section20160164412551:

Creating an Agency
------------------

Before adding file systems to a function, specify an agency with permissions for accessing the file system services for the function.

There is a limit on the maximum number of agencies you can create, and cloud service agencies cannot be modified. Therefore, you are advised to create an agency with high-level permissions, for example, **Tenant Administrator**, to allow a function to access all resources in the selected region. For more information, see :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.

.. _functiongraph_01_0402__en-us_topic_0000001298786853_section457221344513:

Mounting an SFS Turbo File System
---------------------------------

**Setting an Agency**

Before mounting an SFS Turbo file system to a function, specify an agency that has been granted **SFS Administrator** and **VPC Administrator** permissions for the function. If no agencies are available, create one in IAM.

**Configuring VPC Access**

An SFS Turbo file system is accessible only in the VPC where it has been created. Before mounting such a file system to a function, enable VPC access for the function.

#. .. _functiongraph_01_0402__en-us_topic_0000001298786853_li152661816111216:

   On the SFS console, obtain the information about the VPC and subnet where a file system is to be mounted to your function. For details, see `File System Management <https://docs.otc.t-systems.com/scalable-file-service/umn/management/file_system_management/index.html>`__.

#. Enable VPC access by referring to :ref:`Configuring Networks <functiongraph_01_0222>` and enter the VPC and subnet obtained in :ref:`1 <functiongraph_01_0402__en-us_topic_0000001298786853_li152661816111216>`.

**Mounting an SFS Turbo File System**

SFS Turbo file systems can be mounted in the same way as SFS file systems. Select a file system and set the access path.

.. _functiongraph_01_0402__en-us_topic_0000001298786853_section11158112711472:

Mounting an ECS Shared Directory
--------------------------------

**Specifying an Agency**

Before mounting an ECS shared directory to a function, specify an agency that has been granted **Tenant Guest** and **VPC Administrator** permissions for the function. If no agencies are available, create one in IAM. For details, see :ref:`Creating an Agency <functiongraph_01_0402__en-us_topic_0000001298786853_section20160164412551>`.

**Configuring VPC Access**

Before adding an ECS shared directory, specify the VPC where the ECS is deployed. View the VPC information on the details page of the ECS. Click the VPC name to go to the VPC details page, and view the subnet.

Set the acquired VPC and subnet for the function.

**Mounting an ECS Directory**

Enter a shared directory and function access path.


.. figure:: /_static/images/en-us_image_0000001304635949.png
   :alt: **Figure 1** Setting the path

   **Figure 1** Setting the path

.. _functiongraph_01_0402__en-us_topic_0000001298786853_section13985217105113:

Creating an NFS Shared Directory on ECS
---------------------------------------

#. **Linux**

   -  CentOS, SUSE, EulerOS, Fedora, or openSUSE

      a. Configure a YUM repository.

         1. Create a file named **euleros.repo** in the **/etc/yum.repos.d** directory. Ensure that the file name must end with **.repo**.

         2. Run the following command to enter **euleros.repo** and edit the configuration:

         .. code-block::

            vi /etc/yum.repos.d/euleros.repo

         The EulerOS 2.0 SP3 YUM configuration is as follows:

         .. code-block::

            [base]
            name=EulerOS-2.0SP3 base
            baseurl=http://repo.cloud.com/euler/2.3/os/x86_64/
            enabled=1
            gpgcheck=1
            gpgkey=http://repo.cloud.com/euler/2.3/os/RPM-GPG-KEY-EulerOS

         The EulerOS 2.0 SP5 YUM configuration is as follows:

         .. code-block::

            [base]
            name=EulerOS-2.0SP5 base
            baseurl=http://repo.cloud.com/euler/2.5/os/x86_64/
            enabled=1
            gpgcheck=1
            gpgkey=http://repo.cloud.com/euler/2.5/os/RPM-GPG-KEY-EulerOS

         .. note::

            Parameter description:

            **name**: repository name

            **baseurl**: URL of the repository

            -  HTTP-based network address: **http://path/to/repo**
            -  Local repository address: **file:///path/to/local/repo**

            **gpgcheck**: indicates whether to enable the GNU privacy guard (GPG) to check the validity and security of RPM package resources. **0**: The GPG check is disabled. **1**: The GPG check is enabled. If this option is not specified, the GPG check is enabled by default.

         3. Save the configurations.

         4. Run the following command to clear the cache:

         .. code-block::

            yum clean all

      b. Run the following command to install nfs-utils:

         .. code-block::

            yum install nfs-utils

      c. Create a shared directory.

         When you open **/etc/exports** and need to create shared directory **/sharedata**, add the following configuration:

         /sharedata 192.168.0.0/24(rw,sync,no_root_squash)

         .. note::

            The preceding configuration is used to share the **/sharedata** directory with other servers in the **192.168.0.0/24** subnet.

            After the preceding command is run, run the **exportfs -v** command to view the shared directory and check whether the setting is successful.

      d. Run the following commands to start the NFS service:

         .. code-block::

            systemctl start rpcbind
            service nfs start

      e. Create another shared directory.

         For example, to create the **/home/myself/download** directory, add the following configuration to **/etc/exports**:

         /home/myself/download 192.168.0.0/24(rw,sync,no_root_squash)

         Restart the NFS service.

         .. code-block::

            service nfs restart

         Alternatively, run the following command without restarting the NFS service:

         .. code-block::

            exportfs -rv

      f. (Optional) Enable automatic startup of the rpcbind service.

         Run the following command:

         .. code-block::

            systemctl enable rpcbind

   -  **Ubuntu**

      a. Run the following commands to install nfs-kernel-server:

         .. code-block::

            sudo apt-get update
            sudo apt install nfs-kernel-server

      b. Create a shared directory.

         .. code-block::

            vim /etc/exports

         When you open **/etc/exports** and need to create shared directory **/sharedata**, add the following configuration:

         /sharedata 192.168.0.0/24(rw,sync,no_root_squash)

         .. note::

            The preceding configuration is used to share the **/sharedata** directory with other servers in the **192.168.0.0/24** subnet.

      c. Start the NFS service.

         .. code-block::

            service nfs-kernel-server restart

         .. note::

            After the preceding command is run, run the **exportfs -v** command to view the shared directory and check whether the setting is successful.

      d. Create another shared directory.

         For example, to create the **/home/myself/download** directory, add the following configuration to **/etc/exports**:

         /home/myself/download 192.168.0.0/24(rw,sync,no_root_squash)

         Restart the NFS service.

         .. code-block::

            service nfs restart

         Alternatively, run the following command without restarting the NFS service:

         .. code-block::

            exportfs -rv

2. **Windows**

   For details about how to install NFS and share files, see the `official document <https://learn.microsoft.com/en-us/windows-server/storage/nfs/deploy-nfs?tabs=gui>`__ on Windows.
