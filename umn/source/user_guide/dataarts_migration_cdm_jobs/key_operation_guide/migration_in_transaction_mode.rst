:original_name: dataartsstudio_01_0589.html

.. _dataartsstudio_01_0589:

Migration in Transaction Mode
=============================

When a CDM job fails to be executed, CDM rolls back the data to the state before the job starts and automatically deletes data from the destination table.

-  Parameter position: When creating a table/file migration job, if the migration source is a relational database, set **Import to Staging Table** in the advanced attributes of **Destination Job Configuration** to determine whether to enable the transaction mode.

-  Parameter principle: If you set this parameter to **Yes**, CDM automatically creates a temporary table and imports the data to the temporary table. After the data is imported successfully, CDM migrates the data to the destination table in transaction mode of the database. If the import fails, the destination table is rolled back to the state before the job starts.


   .. figure:: /_static/images/en-us_image_0000002234076628.png
      :alt: **Figure 1** Migration in transaction mode

      **Figure 1** Migration in transaction mode

.. note::

   If you select **Clear part of data** or **Clear all data** for **Clear Data Before Import**, CDM does not roll back the deleted data in transaction mode.
