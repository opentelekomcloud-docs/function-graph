:original_name: functiongraph_03_0320.html

.. _functiongraph_03_0320:

What Do LATEST and TRIM_HORIZON Mean in DIS Trigger Configuration?
==================================================================

Cursors **LATEST** and **TRIM_HORIZON** specify the start points for reading data in Data Ingestion Service (DIS) streams.

-  **TRIM_HORIZON**: Data is read from the earliest valid record stored in the partition.

   For example, a tenant used a DIS stream to upload three pieces of data A1, A2, and A3. Assuming that A1 expires but A2 and A3 are still valid after a period of time, if the tenant specifies **TRIM_HORIZON** for downloading data, only A2 and A3 can be downloaded.

-  **LATEST**: Data is read from the latest record in the partition. This option ensures that the most recent data in the partition is read.
