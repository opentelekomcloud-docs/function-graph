:original_name: functiongraph_06_0103.html

.. _functiongraph_06_0103:

Trigger Management Models
=========================

Trigger Type Model
------------------

.. code-block:: text

   {
       "trigger_type_code":"string",
       "display_name":"string",
       "status":"string",
       "event_codes":"array of string",
       "description":"string"
   }

:ref:`Table 1 <functiongraph_06_0103__table1072087614167>` describes the parameters in the trigger type model.

.. _functiongraph_06_0103__table1072087614167:

.. table:: **Table 1** Parameters in the trigger type model

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                    |
   +===================================+================================================================================================================================+
   | trigger_type_code                 | Trigger type code. Options: **SMN**, **APIG**, **TIMER**, **DMS**, **kafka**, **DDS**, **CTS**, **DIS**, **LTS**, and **OBS**. |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | display_name                      | Trigger type value.                                                                                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | status                            | Trigger type status. Options:                                                                                                  |
   |                                   |                                                                                                                                |
   |                                   | -  **DISABLED**: The trigger is disabled.                                                                                      |
   |                                   | -  **TEST**: The trigger is under test and invisible to clients.                                                               |
   |                                   | -  **ACTIVE**: The trigger is available.                                                                                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | description                       | Trigger description.                                                                                                           |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

Trigger Instance Model
----------------------

.. code-block:: text

   {
       "trigger_id":"string",
       "trigger_type_code":"string",
       "event_type_code":"string",
       "status":"string",
       "event_data":"json struct",
       "last_updated_time":"string",
       "created_time":"string"
   }

:ref:`Table 2 <functiongraph_06_0103__table11855096142915>` describes the parameters in the trigger instance model.

.. _functiongraph_06_0103__table11855096142915:

.. table:: **Table 2** Parameters in the trigger instance model

   +-------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Description                                                                                                                    |
   +===================+================================================================================================================================+
   | trigger_id        | Trigger ID.                                                                                                                    |
   +-------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | trigger_type_code | Trigger type code. Options: **SMN**, **APIG**, **TIMER**, **DMS**, **kafka**, **DDS**, **CTS**, **DIS**, **LTS**, and **OBS**. |
   +-------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | event_type_code   | Event type code. This parameter is mandatory. It can be any non-null character string. This parameter is not used currently.   |
   +-------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | status            | Trigger status. Options: **ACTIVE** and **DISABLED**.                                                                          |
   +-------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | event_data        | Trigger data defined in JSON format.                                                                                           |
   +-------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | last_updated_time | Time when the trigger was last updated.                                                                                        |
   +-------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | created_time      | Time when the trigger was created.                                                                                             |
   +-------------------+--------------------------------------------------------------------------------------------------------------------------------+

Trigger Instance Data
---------------------

-  The data of a Simple Message Notification (SMN) trigger is as follows:

   .. code-block:: text

      {
          "topic_urn":"string",
          "subscription_status":"string"
      }

   :ref:`Table 3 <functiongraph_06_0103__table46683704143627>` describes the parameters of an SMN trigger.

   .. _functiongraph_06_0103__table46683704143627:

   .. table:: **Table 3** Parameters of an SMN trigger

      +---------------------+----------------------------------------------------------------------------------+
      | Parameter           | Description                                                                      |
      +=====================+==================================================================================+
      | topic_urn           | URN of an SMN topic. This parameter is mandatory when you create an SMN trigger. |
      +---------------------+----------------------------------------------------------------------------------+
      | subscription_status | Subscription status of a topic. Options: **Unconfirmed** and **Confirmed**.      |
      +---------------------+----------------------------------------------------------------------------------+

-  The data of a Distributed Message Service (DMS) trigger is as follows:

   .. code-block:: text

      {
          "queue_id":"string",
          "consumer_group_id":"string",
          "polling_interval":"int"
      }

   :ref:`Table 4 <functiongraph_06_0103__table0558183404>` describes the parameters of a DMS trigger.

   .. _functiongraph_06_0103__table0558183404:

   .. table:: **Table 4** Parameters of a DMS trigger

      +-------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter         | Description                                                                                                           |
      +===================+=======================================================================================================================+
      | queue_id          | Name of a DMS queue. This parameter is mandatory when you create a DMS trigger.                                       |
      +-------------------+-----------------------------------------------------------------------------------------------------------------------+
      | consumer_group_id | Name of a DMS consumer group. This parameter is mandatory when you create a DMS trigger.                              |
      +-------------------+-----------------------------------------------------------------------------------------------------------------------+
      | polling_interval  | Interval at which messages are polled. This parameter is mandatory when you create a DMS trigger. Default value: 30s. |
      +-------------------+-----------------------------------------------------------------------------------------------------------------------+

-  The data of an Object Storage Service (OBS) trigger is as follows:

   .. code-block:: text

      {
         "bucket": "yourBucketName",
         "events": ["s3:ObjectCreated:Put"],
         "prefix": "yourPrefix",
         "suffix": "yourSuffix"
      }

   .. table:: **Table 5** Parameters of an OBS trigger

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================================================================================================+
      | bucket                            | Bucket name. This parameter is mandatory.                                                                                                                                                                                                                                                                                          |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | events                            | Collection of OBS trigger events. Options: **s3:ObjectCreated:\***, **s3:ObjectCreated:Put**, **s3:ObjectCreated:Post**, **s3:ObjectCreated:Copy**, **s3:ObjectCreated:CompleteMultipartUpload**, **s3:ObjectRemoved:\***, **s3:ObjectRemoved:DeleteMarkerCreated**, and **s3:ObjectRemoved:Delete**. This parameter is mandatory. |
      |                                   |                                                                                                                                                                                                                                                                                                                                    |
      |                                   | Note that **s3:objectcreated:\*** includes all events that start with **s3:objectcreated**, and **s3:objectremoved:\*** includes all events that start with **s3:objectremoved**.                                                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | prefix                            | Prefix of an OBS object. This parameter is optional.                                                                                                                                                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | suffix                            | Suffix of an OBS object. This parameter is optional.                                                                                                                                                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  The data of a Data Ingestion Service (DIS) trigger is as follows:

   .. code-block:: text

      {
      "stream_name": "dis-qYPJ",
      "polling_interval": 30,
      "batch_size": 100,
      "sharditerator_type": "TRIM_HORIZON"
      }

   :ref:`Table 6 <functiongraph_06_0103__table797218531255>` describes the parameters of a DIS trigger.

   .. _functiongraph_06_0103__table797218531255:

   .. table:: **Table 6** Parameters of a DIS trigger

      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter          | Description                                                                                                                                           |
      +====================+=======================================================================================================================================================+
      | stream_name        | Name of a stream. This parameter is mandatory.                                                                                                        |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | polling_interval   | Pull period. This parameter is optional. Value range: 1-60. Default value: 30.                                                                        |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | batch_size         | Number of data records that can be pulled from a specified stream. This parameter is optional. Value range: 1-10000. Default value: 100.              |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | sharditerator_type | Options: TRIM_HORIZON (pulling data from the beginning of a stream) and LATEST (pulling data from the current position). This parameter is mandatory. |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

-  The data of an APIG trigger is as follows:

   .. code-block:: text

      {
          "group_id":"string",
          "env_id":"string",
          "auth":"string",
          "protocol":"string",
          "name":"string",
          "path":"string",
          "match_mode":"string",
          "req_method":"string" ,
          "backend_type":"string" ,
          "type": int ,
          "sl_domain":"string"
      }

   :ref:`Table 7 <functiongraph_06_0103__table18282101120468>` describes the parameters of an APIG trigger.

   .. _functiongraph_06_0103__table18282101120468:

   .. table:: **Table 7** Parameters of an APIG trigger

      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | Parameter    | Description                                                                                                             |
      +==============+=========================================================================================================================+
      | group_id     | API group. This parameter is mandatory.                                                                                 |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | env_id       | API publishing environment. This parameter is mandatory.                                                                |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | auth         | API authentication mode. Options: **NONE**, **IAM**, and **APP**. This parameter is mandatory.                          |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | protocol     | Access protocol. Options: **HTTP** and **HTTPS**. This parameter is mandatory.                                          |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | name         | API name. This parameter is mandatory.                                                                                  |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | path         | API access address, which must meet the URL rules, for example, **/a/b**. This parameter is mandatory.                  |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | match_mode   | Match mode. Currently, only the prefix match mode (corresponding to **SWA**) is supported. This parameter is mandatory. |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | req_method   | API request method, which is of enumerated type. Options: **GET**, **POST**, and **PUT**. This parameter is mandatory.  |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | backend_type | Backend type, which must be set to **FUNCTION**. This parameter is mandatory.                                           |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | type         | API type. Currently, only open APIs (corresponding to value **1**) are supported. This parameter is mandatory.          |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+
      | sl_domain    | Subdomain name. This parameter is mandatory.                                                                            |
      +--------------+-------------------------------------------------------------------------------------------------------------------------+

-  The data of a timer trigger is as follows:

   .. code-block:: text

      {
          "name": "string",
          "schedule_type": "string",
          "schedule": "string",
          "user_event": "string"
      }

   :ref:`Table 8 <functiongraph_06_0103__table169831625017>` describes the parameters of a timer trigger.

   .. _functiongraph_06_0103__table169831625017:

   .. table:: **Table 8** Parameters of a timer trigger

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                      |
      +===================================+==================================================================================================================+
      | name                              | Trigger name. This parameter is mandatory.                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+
      | schedule_type                     | Schedule type. Options: **Rate** or **Cron**. This parameter is mandatory.                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+
      | schedule                          | Schedule setting, which varies depending on the schedule type you choose. This parameter is mandatory.           |
      |                                   |                                                                                                                  |
      |                                   | When **schedule_type** is set to **Rate**, add unit m, h, or d behind a rate, for example, **3m** for 3 minutes. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+
      | user_event                        | Additional information for calling a function. This parameter is optional.                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------+

-  The data of a Log Tank Service (LTS) trigger is as follows:

   .. code-block:: text

      {
          "trigger_type_code": "LTS",
          "event_type_code": "MessageCreated",
          "trigger_status": "ACTIVE",
          "event_data": {
              "log_group_id": "3e4d3bf7-7bad-11e9-92c5-fa163e6216be",
              "log_topic_id": "41d90375-7bad-11e9-8bcf-fa163ea23ac3",
              "log_group_name": "lts-group-5b42",
              "log_topic_name": "lts-topic-5f3e"
          }
      }

   :ref:`Table 9 <functiongraph_06_0103__table866014421545>` describes the parameters of an LTS trigger.

   .. _functiongraph_06_0103__table866014421545:

   .. table:: **Table 9** Parameters of an LTS trigger

      +-----------+------------------------------------------------------------------------+
      | Parameter | Description                                                            |
      +===========+========================================================================+
      | group_id  | Log group. This parameter is mandatory when you create an LTS trigger. |
      +-----------+------------------------------------------------------------------------+
      | topic_id  | Log topic. This parameter is mandatory when you create an LTS trigger. |
      +-----------+------------------------------------------------------------------------+

-  The data of a Cloud Trace Service (CTS) trigger is as follows:

   .. code-block:: text

      {
          "name": "eqwrwe",
          "operations": ["AAD:addprotocolrule:addProtocolRule", "BCS:baas-apiserver:scalePeers", "ARS:ars:setConfigArs"]
      }

   :ref:`Table 10 <functiongraph_06_0103__table15406140191011>` describes the parameters of a CTS trigger.

   .. _functiongraph_06_0103__table15406140191011:

   .. table:: **Table 10** Parameters of a CTS trigger

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                       |
      +===================================+===================================================================================================================================================+
      | name                              | Name of a key notification.                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | operations                        | Operation list.                                                                                                                                   |
      |                                   |                                                                                                                                                   |
      |                                   | The format is "service type:resource type A;resource type B:operation 1;operation 2". Example: ["ECS:ecs;server:restartServer;deleteServer",...]. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

-  The data of a Document Database Service (DDS) trigger is as follows:

   .. code-block::

      {
          "instance_id": "string",
              "collection_name": "string",
              "db_name": "string",
          "db_password": string,
              "batch_size": int,
      }

   .. table:: **Table 11** Parameters of a DDS trigger

      =============== ========================================
      Parameter       Description
      =============== ========================================
      instance_id     DB instance ID.
      collection_name Collection name.
      db_name         Database name.
      db_password     Password for logging in to the database.
      batch_size      Batch size.
      =============== ========================================

-  The data of a Kafka trigger is as follows:

   .. code-block::

      {
              "instance_id": "string",
          "db_name": "string",
              "collection_name": "string",
              "db_user": "string",
          "db_password": string,
              "batch_size": int,
      }

   .. table:: **Table 12** Parameters of a Kafka trigger

      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Description                                                                                                                             |
      +==================+=========================================================================================================================================+
      | instance_id      | Kafka instance ID.                                                                                                                      |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | topic_id         | Topic ID.                                                                                                                               |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | kafka_user       | Username.                                                                                                                               |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | kafka_password   | Password.                                                                                                                               |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | kafka_ssl_enable | Whether to enable SSL authentication. If SSL authentication is enabled, the **kafka_user** and **kafka_password** fields are mandatory. |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | batch_size       | Batch size.                                                                                                                             |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
