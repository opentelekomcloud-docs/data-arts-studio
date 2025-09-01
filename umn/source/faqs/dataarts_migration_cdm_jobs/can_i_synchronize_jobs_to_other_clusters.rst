:original_name: dataartsstudio_03_0030.html

.. _dataartsstudio_03_0030:

Can I Synchronize Jobs to Other Clusters?
=========================================

Symptom
-------

Can I synchronize jobs to other CDM clusters?

Solution
--------

CDM does not support direct job migration across clusters. However, you can use the batch job import and export function to indirectly implement cross-cluster migration as follows:

#. Export all jobs from CDM cluster 1 and save the jobs' JSON files to a local PC.

   For security purposes, no link password is exported when CDM exports jobs. All passwords are replaced by *Add password here*.

#. Edit each JSON file on the local PC by replacing *Add password here* with the actual password of the corresponding link.

#. Import the edited JSON files to CDM cluster 2 in batches to implement job migration between cluster 1 and cluster 2.
