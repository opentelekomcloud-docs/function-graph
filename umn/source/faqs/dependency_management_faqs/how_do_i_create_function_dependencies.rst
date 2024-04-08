:original_name: functiongraph_03_0343.html

.. _functiongraph_03_0343:

How Do I Create Function Dependencies?
======================================

**You are advised to create function dependencies in EulerOS.** If other OSs are used, an error may occur due to underlying dependent libraries. For example, the dynamic link library cannot be found.

.. note::

   If the modules to be installed need dependencies such as .dll, .so, and .a, archive them to a .zip package.

Creating a Dependency for a Python Function
-------------------------------------------

Ensure that the Python version of the packaging environment is the same as that of the function. For Python 2.7, Python 2.7.12 or later is recommended. For Python 3.6, Python 3.6.3 or later is recommended.

To install the PyMySQL dependency for a Python 2.7 function in the local **/tmp/pymysql** directory, run the following command:

.. code-block::

   pip install PyMySQL --root /tmp/pymysql

After the command is successfully executed, go to the **/tmp/pymysql** directory:

.. code-block::

   cd /tmp/pymysql/

Go to the **site-packages** directory (generally, **usr/lib64/python2.7/site-packages/**) and then run the following command:

.. code-block::

   zip -rq pymysql.zip *

The required dependency is generated.

.. note::

   To install the local wheel installation package, run the following command:

   .. code-block::

      pip install piexif-1.1.0b0-py2.py3-none-any.whl --root /tmp/piexif
      //Replace piexif-1.1.0b0-py2.py3-none-any.whl with the actual installation package name.

Creating a Dependency for a Node.js Function
--------------------------------------------

Ensure that the corresponding Node.js version has been installed in the environment.

To install the MySQL dependency for a Node.js 8.10 function, run the following command:

.. code-block::

   npm install mysql --save

The **node_modules** folder is generated under the current directory.

-  Linux OS

   Run the following command to generate a ZIP package.

   .. code-block::

      zip -rq mysql-node8.10.zip node_modules

   The required dependency is generated.

-  Windows OS

   Compress **node_modules** into a ZIP file.

To install multiple dependencies, create a **package.json** file first. For example, enter the following content into the **package.json** file and then run the following command:

.. code-block:: text

   {
       "name": "test",
       "version": "1.0.0",
       "dependencies": {
           "redis": "~2.8.0",
           "mysql": "~2.17.1"
       }
   }

.. code-block::

   npm install --save

.. note::

   Do not run the **CNPM** command to generate Node.js dependencies.

Compress **node_modules** into a ZIP package. This generates a dependency that contains both MySQL and Redis.

For other Node.js versions, you can create dependencies in the way stated above.

Creating a Dependency for a Java Function
-----------------------------------------

When you compile a function using Java, dependencies need to be compiled locally.
