:original_name: functiongraph_03_0830.html

.. _functiongraph_03_0830:

How Can I Create an ODBC Drive-based Python Dependency Package for Database Query?
==================================================================================

For OS-dependent packages (for example, unixODBC), download the source code to compile dependency packages.

#. Log in to your ECS on the ECS console (ensure that the GCC and Make tools have been installed), and run the following command to download the source code package:

   .. code-block::

      wget source code path

   If you downloaded a **.zip** file, run the following command to decompress it:

   .. code-block::

      unzip xxx/xx.zip

   If you downloaded a **tar.gz** file, run the following command to decompress it:

   .. code-block::

      tar -zxvf xxx/xx.tar.gz

#. Run the following command to create the **/opt/function/code** directory:

   .. code-block::

      mkdir /opt/function/code

#. Go to the destination directory and run the following command:

   .. code-block::

      ./configure --prefix=/opt/function/code --sysconfdir=/opt/function/code;make;make install

#. Go to **/opt/function/code/lib/pkgconfig** and check whether the prefix directory is **/opt/function/code**.

   .. code-block::

      cd /opt/function/code/lib/pkgconfig

#. Copy all files in **/opt/function/code/lib** to **/opt/function/code**.

   .. code-block::

      cp -r /opt/function/code/lib/* /opt/function/code

#. Switch to **/opt/function/code** and compress all files in it to a **.zip** package.

   .. code-block::

      cd /opt/function/code

   .. code-block::

      zip -r xxx.zip *
