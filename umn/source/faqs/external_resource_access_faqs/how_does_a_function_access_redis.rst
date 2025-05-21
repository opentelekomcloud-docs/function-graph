:original_name: functiongraph_03_0300.html

.. _functiongraph_03_0300:

How Does a Function Access Redis?
=================================

Perform the following operations:

#. Check whether the Redis instance is deployed in a VPC.

   -  If the Redis instance is deployed in a VPC, configure the same VPC and subnet as the Redis instance for the function by referring to :ref:`Configuring VPC Access <functiongraph_01_0222>`.
   -  If the Redis instance is built on a public network, obtain its public IP address.

#. Compile code for connecting a function to the Redis instance.

   FunctionGraph has integrated third-party library `redis-py <https://github.com/andymccurdy/redis-py>`__ in its Python 2.7 and Python 3.6 runtimes. Therefore, you do not need to download any other Redis libraries.

   .. code-block:: text

      # -*- coding:utf-8 -*-
      import redis
      def handler (event, context):
          r = redis.StrictRedis(host="host_ip",password="passwd",port=6379)
          print(str(r.get("hostname")))
          return "^_^"

   .. note::

      -  If the function fails to access to the Redis instance on a public network, perform the following operations:

         -  Modify the **redis.conf** file to allow access from any IP addresses.
         -  Set a password for accessing the Redis instance in the **redis.conf** file.
         -  Disable the firewall.

      -  If the function needs to access DCS APIs, :ref:`create an agency <functiongraph_01_0920>` and grant required permissions.
