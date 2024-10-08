:original_name: dataartsstudio_02_0005.html

.. _dataartsstudio_02_0005:

Constraints
===========

-  An IAM user can pass the authentication and access DataArts Studio through an API or SDK only if **Programmatic access** is selected for **Access Type** during the creation of the IAM user.

-  The restrictions on DataArts Catalog APIs are as follows:

   -  CDM jobs carry large volumes of data, which increases the database load. You are advised to periodically delete unused jobs.
   -  If a large number of jobs are delivered in a short period, cluster resources may be exhausted.
   -  CDM is a batch offline migration tool. You are advised not to create a large number of small jobs using CDM.

-  For the constraints of other modules' APIs, see their API descriptions.
