:original_name: functiongraph_06_0102.html

.. _functiongraph_06_0102:

Function Model
==============


Function Model
--------------

The function model of FunctionGraph is as follows:

.. code-block:: text

   {
     "functions": [
      {
       "func_urn": "urn:fss:xxxxxxxxx:7aad83af3e8d42e99ac194e8419e2c9b:function:default:test",
       "func_name": "test",
       "domain_id": "cff01_hk",
       "namespace": "7aad83af3e8d42e99ac194e8419e2c9b",
       "project_name": "xxxxxxxxxx",
       "package": "default",
       "runtime": "Node.js6.10",
       "timeout": 3,
       "handler": "test.handler",
       "memory_size": 128,
       "cpu": 300,
       "code_type": "inline",
       "code_url": "",
       "code_filename": "index.js",
       "code_size": 272,
       "user_data": "",
       "digest": "decbce6939297b0b5ec6d1a23bf9c725870f5e69fc338a89a6a4029264688dc26338f56d08b6535de47f15ad538e22ca66613b9a46f807d50b687bb53fded1c6",
       "version": "latest",
       "image_name": "latest-5qe8e",
       "xrole": "cff",
       "app_xrole": null,
       "description": "111",
       "version_description": "",
       "last_modified": "2018-03-28T11:30:32+08:00",
   "func_code": {
     "file": "",
     "link": ""
    },
    "func_vpc":null,
    "mount_config":null,
    "depend_list": null,
    "strategy_config": {
        "concurrency": -1
    },
    "extend_config": "",
    "dependencies": null,
   "initializer_handler": "index.initializer",
   "initializer_timeout": 3
      }
     ],
     "next_marker": 45
    }

Description
-----------

:ref:`Table 1 <functiongraph_06_0102__table357132064218>` describes the parameters in the function model.

.. _functiongraph_06_0102__table357132064218:

.. table:: **Table 1** Parameters in the function model

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                               |
   +===================================+===========================================================================================================================================================================================================================================+
   | func_urn                          | Function URN.                                                                                                                                                                                                                             |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | func_name                         | Function name.                                                                                                                                                                                                                            |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id                         | Tenant name.                                                                                                                                                                                                                              |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | namespace                         | Project ID.                                                                                                                                                                                                                               |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_name                      | Project name.                                                                                                                                                                                                                             |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | package                           | Group to which the function belongs. This field is defined to group functions.                                                                                                                                                            |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | runtime                           | Environment for executing the function. FunctionGraph supports Node.js 6.10, Node.js 8.10, Node.js 10.16, Node.js 12.13, Python 2.7, Python 3.6, Java 8, Go 1.8, C# (.NET Core 2.0), C# (.NET Core 2.1), C# (.NET Core 3.1), and PHP 7.3. |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timeout                           | Maximum duration the function can be executed. Value range: 3s-900s.                                                                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | handler                           | Handler of the function in the format of "xx.xx". It must contain a period (.).                                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                           |
   |                                   | For example, for Node.js function **myfunction.handler**, the file name is **myfunction.js**, and the entry point function is **handler**.                                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | memory_size                       | Memory (MB) consumed by the function.                                                                                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                                           |
   |                                   | Options: 128, 256, 512, 768, 1024, 1280, 1536, 1792, 2048, 2560, 3072, 3584, and 4096.                                                                                                                                                    |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cpu                               | Number of CPU millicores used by the function (1 core = 1000 millicores).                                                                                                                                                                 |
   |                                   |                                                                                                                                                                                                                                           |
   |                                   | The value of this field is proportional to that of **MemorySize**. By default, 100 CPU millicores are required for 128 MB memory. The value is calculated as follows: Memory/128 x 100 + 200 (basic CPU millicores).                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code_type                         | Function code type. Options:                                                                                                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                           |
   |                                   | -  **inline**: inline code                                                                                                                                                                                                                |
   |                                   | -  **zip**: ZIP file                                                                                                                                                                                                                      |
   |                                   | -  **jar**: JAR file (mainly for Java functions)                                                                                                                                                                                          |
   |                                   | -  **obs**: function code stored in an Object Storage Service (OBS) bucket                                                                                                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code_url                          | -  When **code_type** is set to **obs**, this parameter indicates the address of a function code package in OBS.                                                                                                                          |
   |                                   | -  When **code_type** is set to **inline**, **zip**, or **jar**, this parameter is left blank.                                                                                                                                            |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code_filename                     | Function file name.                                                                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                           |
   |                                   | -  When **code_type** is set to **zip** or **jar**, this parameter is required.                                                                                                                                                           |
   |                                   | -  When **code_type** is set to **obs** or **inline**, this parameter is not required.                                                                                                                                                    |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code_size                         | Code size in bytes.                                                                                                                                                                                                                       |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_data                         | Name/Value information defined for the function.                                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                                                                           |
   |                                   | For example, if a function needs to access a host, define Host={host_ip}. You can define a maximum of 20 such parameters, and their total length cannot exceed 4 KB.                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | digest                            | SHA512 hash value of function code, which is used to determine whether the function is changed.                                                                                                                                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version                           | Function version, which is automatically generated by the system. The version name is in the format of "vYYYYMMDD-HHMMSS" (v+year/month/day-hour/minute/second).                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_name                        | Internal identifier of a function version.                                                                                                                                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | xrole                             | Agency used by the function. You need to create an agency on the Identity and Access Management (IAM) console. This field is mandatory when a function needs to access other services.                                                    |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_xrole                         | Agency used by the function app. You need to create an agency on the IAM console. This field is mandatory when a function needs to access other services.                                                                                 |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                       | Description of the function.                                                                                                                                                                                                              |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_description               | Description of the function version.                                                                                                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | last_modified                     | Time when the function was last updated.                                                                                                                                                                                                  |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | func_code                         | Function code. See :ref:`Table 2 <functiongraph_06_0102__table18312152434512>`.                                                                                                                                                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | depend_list                       | Dependency list.                                                                                                                                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | strategy_config                   | Function policy configuration. See :ref:`Table 3 <functiongraph_06_0102__table4775818446>`.                                                                                                                                               |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | extend_config                     | Function extension configuration.                                                                                                                                                                                                         |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dependencies                      | Dependency list. See :ref:`Table 5 <functiongraph_06_0102__table3788232112820>`.                                                                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | initializer_handler               | Initializer of the function in the format of "xx.xx". It must contain a period (.).                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                           |
   |                                   | For example, for Node.js function **myfunction.initializer**, the file name is **myfunction.js**, and the initialization function is **initializer**.                                                                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | initializer_timeout               | Maximum duration the function can be initialized. Value range: 1s-300s.                                                                                                                                                                   |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | func_vpc                          | Virtual Private Cloud (VPC) configuration. See :ref:`Table 4 <functiongraph_06_0102__table11522131317013>`.                                                                                                                               |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | mount_config                      | File system configuration. See :ref:`Table 6 <functiongraph_06_0102__table2317745151313>`.                                                                                                                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _functiongraph_06_0102__table18312152434512:

.. table:: **Table 2** func_code parameters

   ========= =============================================
   Parameter Description
   ========= =============================================
   file      Function code. Nothing will be returned.
   link      Function code link. Nothing will be returned.
   ========= =============================================

.. _functiongraph_06_0102__table4775818446:

.. table:: **Table 3** strategy_config parameter

   +-----------------------------------+-------------------------------------+
   | Parameter                         | Description                         |
   +===================================+=====================================+
   | concurrency                       | -  **0**: The function is disabled. |
   |                                   | -  **-1**: The function is enabled. |
   +-----------------------------------+-------------------------------------+

.. _functiongraph_06_0102__table11522131317013:

.. table:: **Table 4** func_vpc parameters

   =========== ====== =================================== ============
   Parameter   Type   Mandatory                           Description
   =========== ====== =================================== ============
   vpc_name    String ``-``                               VPC name.
   vpc_id      String Yes when **func_vpc** is not empty. VPC ID.
   subnet_name String ``-``                               Subnet name.
   subnet_id   String Yes when **func_vpc** is not empty. Subnet ID.
   cidr        String ``-``                               Subnet mask.
   gateway     String ``-``                               Gateway.
   =========== ====== =================================== ============

.. _functiongraph_06_0102__table3788232112820:

.. table:: **Table 5** dependency parameters

   +-------------+--------+-----------+-----------------------------------------------------------------------------+
   | Parameter   | Type   | Mandatory | Description                                                                 |
   +=============+========+===========+=============================================================================+
   | owner       | String | ``-``     | Domain ID of the dependency owner.                                          |
   +-------------+--------+-----------+-----------------------------------------------------------------------------+
   | link        | String | ``-``     | URL of the dependency package on OBS.                                       |
   +-------------+--------+-----------+-----------------------------------------------------------------------------+
   | runtime     | String | ``-``     | Language of the dependency package (only used for classification purposes). |
   +-------------+--------+-----------+-----------------------------------------------------------------------------+
   | etag        | String | ``-``     | MD5 value of the dependency package.                                        |
   +-------------+--------+-----------+-----------------------------------------------------------------------------+
   | size        | Int    | ``-``     | Size of the dependency package.                                             |
   +-------------+--------+-----------+-----------------------------------------------------------------------------+
   | name        | String | ``-``     | Name of the dependency package.                                             |
   +-------------+--------+-----------+-----------------------------------------------------------------------------+
   | description | String | ``-``     | Description of the dependency package.                                      |
   +-------------+--------+-----------+-----------------------------------------------------------------------------+
   | file_name   | String | ``-``     | File name of the dependency package (ZIP).                                  |
   +-------------+--------+-----------+-----------------------------------------------------------------------------+

.. _functiongraph_06_0102__table2317745151313:

.. table:: **Table 6** mount_config parameters

   +-------------+----------------------------------------------------------------+-----------+---------------------------------+
   | Parameter   | Type                                                           | Mandatory | Description                     |
   +=============+================================================================+===========+=================================+
   | mount_user  | :ref:`mount_user <functiongraph_06_0102__table14797155061717>` | ``-``     | File system user configuration. |
   +-------------+----------------------------------------------------------------+-----------+---------------------------------+
   | func_mounts | :ref:`func_mounts <functiongraph_06_0102__table1937492111205>` | ``-``     | File system list.               |
   +-------------+----------------------------------------------------------------+-----------+---------------------------------+

.. _functiongraph_06_0102__table14797155061717:

.. table:: **Table 7** mount_user parameters

   +---------------+------+---------------------------------------+------------------------------------------------------------------------------------+
   | Parameter     | Type | Mandatory                             | Description                                                                        |
   +===============+======+=======================================+====================================================================================+
   | user_id       | Int  | Yes when **mount_user** is not empty. | User ID, which is an integer from -1 to 65,534, excluding 0, 1000, and 1002.       |
   +---------------+------+---------------------------------------+------------------------------------------------------------------------------------+
   | user_group_id | Int  | Yes when **mount_user** is not empty. | User group ID, which is an integer from -1 to 65,534, excluding 0, 1000, and 1002. |
   +---------------+------+---------------------------------------+------------------------------------------------------------------------------------+

.. _functiongraph_06_0102__table1937492111205:

.. table:: **Table 8** func_mounts parameters

   +------------------+--------+--------------------------------------------+-----------------------------------------------------------+
   | Parameter        | Type   | Mandatory                                  | Description                                               |
   +==================+========+============================================+===========================================================+
   | mount_type       | String | Yes when **func_mounts** is not empty.     | Mount type. Options: **ecs**.                             |
   +------------------+--------+--------------------------------------------+-----------------------------------------------------------+
   | mount_resource   | String | Yes when **func_mounts** is not empty.     | ID of the mounted resource (corresponding cloud service). |
   +------------------+--------+--------------------------------------------+-----------------------------------------------------------+
   | mount_share_path | String | Yes when **mount_type** is set to **ecs**. | Remote mount path. Example: **192.168.0.12:/data**.       |
   +------------------+--------+--------------------------------------------+-----------------------------------------------------------+
   | local_mount_path | String | Yes when **func_mounts** is not empty.     | Function access path.                                     |
   +------------------+--------+--------------------------------------------+-----------------------------------------------------------+

The format of a function URN is as follows:

.. code-block:: text

   urn:fss:<region_id>:<project_id>:function:<package>:<function_name>[:<version>|:!<alias>]

.. note::

   A function URN is divided into eight fields by colons. The value of **region_id** is included in the system configuration. You can set this parameter to the same as that in the backend. The content in the brackets ([]) is a function version or alias. If you enter an alias, add an exclamation mark (!) in front of it for easy identification.

When a function URN is used as an API parameter, you can provide it in a simplified format as follows:

-  1 field: **<function_name>**. **project_id** is obtained from a token, **package** is **default**, and **version** is **latest**.
-  2 fields: **<package>:<function_name>**. **project_id** is obtained from a token, and **version** is **latest**.
-  3 fields: **<project_id>:<package>:<function_name>**. **version** is **latest**.
-  4 fields: **<project_id>:<package>:<function_name>:<Version or Alias>**.
-  7 fields: **urn:fss:<region_id>:<project_id>:function:<package>:<function_name>**. **version** is **latest**.
-  8 fields: **urn:fss:<region_id>:<project_id>:function:<package>:<function_name>:<Version or Alias>**.
