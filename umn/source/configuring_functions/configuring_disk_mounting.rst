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

#. Enable VPC access by referring to :ref:`Configuring the Network <functiongraph_01_0222>` and enter the VPC and subnet obtained in :ref:`1 <functiongraph_01_0402__en-us_topic_0000001298786853_li152661816111216>`.

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

Follow-up Operations
--------------------

A function can read and write data in an access path in the same way as in the mounted file system.

Function logs can be persisted by configuring the log path as a subdirectory in the access path.

The following uses SFS Turbo and template **Web-Server-Access-Log-Statistics** as an example to describe how to analyze logs of servers running on the cloud.

#. Log in to the FunctionGraph console. In the navigation pane, choose **Templates**.

#. In the upper right corner of the **Templates** page, enter **Web-Server-Access-Log-Statistics** in the search box and press **Enter**.

#. In the search result, click **Configure**. The configuration page is displayed, as shown in :ref:`Figure 2 <functiongraph_01_0402__en-us_topic_0000001298786853_fig193615583517>`. Set the parameters as follows:

   .. _functiongraph_01_0402__en-us_topic_0000001298786853_fig193615583517:

   .. figure:: /_static/images/en-us_image_0000002192364610.png
      :alt: **Figure 2** Function template

      **Figure 2** Function template

   -  **Region**: Select the same region as the created VPC and file system. For details about how to create a VPC and file system, see :ref:`Configuring the Network <functiongraph_01_0222>` and `Creating a File System <https://docs.otc.t-systems.com/scalable-file-service/umn/getting_started/create_a_file_system.html#en-us-topic-0034428727>`__.
   -  **Project**: Use **default**.
   -  **Function Name**: Enter a custom name.
   -  **Agency**: Select an agency with the file system, VPC, and APIG permissions. For details about how to create an agency, see :ref:`Configuring Agency Permissions <functiongraph_01_0920>`.
   -  **Enterprise Project**: Select an enterprise project as required.
   -  **Environment Variables**: **access_log_path** indicates the log file address. Set this parameter to **/home/test/access_log.log**.

      .. note::

         To specify file paths in the file system, use absolute paths starting with a slash (/). However, if no file system is mounted, you can skip adding the slash (/) and simply set the parameter to **code/access_log.log**.

   -  **Trigger Type**: The default value is **API Gateway (APIG)**. For details about how to configure APIG, see :ref:`Using an APIG (Dedicated) Trigger <functiongraph_01_0204>`.
   -  **API Name**: Enter a custom name.
   -  **API Group**: Select a group based on the actual service.
   -  **Environment**: Select **RELEASE**.
   -  **Security Authentication**: Select **None**.
   -  **Protocol** and **Timeout (ms)**: Retain the default values.

#. After parameter configuration is complete, click **Create Function**.

#. On the function details page, click the **Code** tab, add the following code to the **index.py** file, and click **Deploy**.

   .. code-block::

      import shutil

   .. code-block::

      shutil.copyfile('/opt/function/code/access_log.log', '/home/test/access_log.log')


   .. figure:: /_static/images/en-us_image_0000002227609317.png
      :alt: **Figure 3** Adding code

      **Figure 3** Adding code

   In addition, add the public dependency **Jinja2-2.10**. For details, see :ref:`How Do I Add a Dependency to a Function? <functiongraph_03_0889>`.

   .. note::

      If no file system is mounted, you do not need to add the preceding code.

#. On the function details page, choose **Configuration** > **Network** and enable **VPC Access**. Set **VPC** and **Subnet** to the created VPC and subnet, and click **Save**.


   .. figure:: /_static/images/en-us_image_0000002227735377.png
      :alt: **Figure 4** VPC access

      **Figure 4** VPC access

#. Choose **Disk Mounting**, click **Mount File System**, and select **SFS Turbo**.

   -  **File System**: Select an existing SFS Turbo file system.
   -  **Access Path**: Set this parameter to **/home/test**.

#. Click the **Code** tab, select **Configure Test Event**, create a **Blank Template**, and click **Create**.


   .. figure:: /_static/images/en-us_image_0000002227702917.png
      :alt: **Figure 5** Configuring a test event

      **Figure 5** Configuring a test event

#. Select the created test event and click **Test**.


   .. figure:: /_static/images/en-us_image_0000002192221412.png
      :alt: **Figure 6** Test result

      **Figure 6** Test result

#. Choose **Configuration** > **Triggers**, copy the URL of the APIG trigger, and open the URL using a browser.


   .. figure:: /_static/images/en-us_image_0000002192223000.png
      :alt: **Figure 7** Copying the URL

      **Figure 7** Copying the URL


   .. figure:: /_static/images/en-us_image_0000001889911457.png
      :alt: **Figure 8** Results display

      **Figure 8** Results display

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

#. Install the NFS server.

   Paid software: haneWIN NFS Server. Download the software at the `haneWIN official website <https://www.hanewin.net/nfs-e.htm>`__.

   Free software: FreeNFS and WinNFSd. Download the software at the `SourceForge website <https://sourceforge.net/projects/winnfsd/>`__.

#. Enable the NFS function.

   -  In the case of WinNFSd, see `WinNFSd configuration <https://github.com/winnfsd/winnfsd>`__.

      a. Download and decompress WinNFSd, and create the **nfs** folder in the decompressed directory.

      b. Set the sharing and read/write permissions on the **nfs** file.

         #. Right-click the **nfs** file and choose **Properties**.

         #. Click the **Sharing** tab, and then click **Share...**.

         #. Add **Everyone** and click **Share**.


            .. figure:: /_static/images/en-us_image_0000001885930909.png
               :alt: **Figure 9** Adding Everyone

               **Figure 9** Adding Everyone

         #. Click the **Security** tab, select **Everyone** in the **Group or user names** list, and click **Edit**.

         #. In the displayed **Security** dialog box, select **Everyone** from the **Group or user name** list, select **Read** and **Write** from the **Allow** check boxes in the **Permissions for Everyone** list, and click **OK**.

      c. Disable all firewalls, including the **Domain network**, **Private network**, and **Public network**. Enable them after the entire configuration is complete.

      d. Log in to the virtual server of the router and enable ports **111**, **2049**, and **1058** of the external network. (Note: An external IP address is required.)

      e. Run the following command. For details, see https://github.com/winnfsd/winnfsd.

         .. code-block::

            WinNFSd.exe -addr {Your own local IP address 192.168.xxx.xxx} F:\nfs /nfs

   -  In the case of haneWIN NFS Server, perform the following steps:

      a. Run the downloaded **.exe** file as the Windows system administrator.
      b. After the installation is complete, open the **NFS Server** file and choose **Edit** > **Preferences**.
      c. Retain the default settings on the **NFS**, **Server**, and **PortMapper** tab pages. Click the **Exports** tab, click **Edit exports file** to configure the shared directory, and click **Save**.

         .. note::

            The shared directory format can be referenced as **D:\\share -public -name:nfs**, which means to set the permission on the **share** folder to **public** and define an alias **nfs**.

      d. Click **OK**.
      e. Disable all firewalls, including the **Domain network**, **Private network**, and **Public network**. Enable them after the entire configuration is complete.

         .. note::

            Run the following command in Linux to mount the directory and check whether the file sharing is successful:

            .. code-block::

               mount -t nfs -o nolock 192.168.xxx.xxx:/nfs /mnt

            -  **192.168.xxx.xxx** is the IP address of the Windows operating system.
            -  **nfs** is the alias created when the shared directory is configured.
            -  **/mnt** is the local directory where the remote directory is mounted.
