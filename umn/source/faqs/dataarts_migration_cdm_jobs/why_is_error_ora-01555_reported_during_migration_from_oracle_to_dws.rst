:original_name: dataartsstudio_03_0071.html

.. _dataartsstudio_03_0071:

Why Is Error ORA-01555 Reported During Migration from Oracle to DWS?
====================================================================

Symptom
-------

When CDM is used to migrate Oracle data to DWS, an error is reported, as shown in :ref:`Figure 1 <dataartsstudio_03_0071__en-us_topic_0000001163136563_fig1847421211579>`.

.. _dataartsstudio_03_0071__en-us_topic_0000001163136563_fig1847421211579:

.. figure:: /_static/images/en-us_image_0000002234240788.jpg
   :alt: **Figure 1** Symptom

   **Figure 1** Symptom

Cause Analysis
--------------

#. During data migration, if the entire table is queried and the table contains a large amount of data, the query takes a long time.
#. During the query, other users frequently perform the **commit** operation.
#. The RBS (the tablespace used for rollback) of Oracle is small. As a result, the migration task is not complete, the source database has been updated, and the rollback times out.

Summary and Suggestions
-----------------------

#. Reduce the data volume queried each time.
#. Modify the database configurations to increase the RBS of the Oracle database.
