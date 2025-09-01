:original_name: dataartsstudio_01_0013.html

.. _dataartsstudio_01_0013:

Overview
========

DataArts Migration is an efficient and easy-to-use data integration service. Based on the big data migration to the cloud and intelligent data lake solutions, CDM provides easy-to-use migration capabilities and can integrate various types of data sources into the data lake, which simplifies data source migration and integration and improves efficiency for you.

In this document, DataArts Migration refers to Cloud Data Migration (CDM).

Introduction to CDM
-------------------

CDM uses a distributed compute framework and concurrent processing techniques to help you migrate enterprise data in batches without any downtime and rapidly build desired data structures.


.. figure:: /_static/images/en-us_image_0000002234076228.png
   :alt: **Figure 1** CDM

   **Figure 1** CDM

Functions
---------

-  **Table/file/entire DB migration**

   Tables or files can be migrated in batches. An entire database can be migrated between homogeneous and heterogeneous databases. A job can migrate hundreds of tables.

-  **Incremental data migration**

   CDM supports incremental migration of files, relational databases, and HBase/CloudTable, as well as with WHERE clauses and macro variables of date and time.

-  **Migration in transaction mode**

   When a CDM job fails to be executed, CDM rolls back the data to the state before the job starts and automatically deletes data from the destination table.

-  **Field conversion**

   CDM supports field conversion functions, such as anonymization, character string operations, and date operations.

-  **File encryption**

   When files are migrated to a file system, CDM can encrypt the files written to the cloud.

-  **MD5 verification**

   MD5 verification is supported to check the file consistency from end to end and output verification result.

-  **Dirty data archiving**

   CDM can archive the data that fails to be processed during migration, has been filtered out, or is not compliant with conversion or cleaning rules to dirty data logs. The threshold for dirty data ratio can be set to determine whether a task is successful.

Migration Principles
--------------------

When a tenant uses CDM, the CDM system provisions a fully-managed CDM instance in the tenant's VPC. The instance allows only console and RESTful API access. Therefore the tenant cannot access the instance through other interfaces (such as SSH). This ensures data isolation between CDM tenants, prevents data leakage, and ensures transmission security during data migration between different cloud services in a VPC. Tenants can also use the VPN to migrate data from the on-premises data center to cloud services to ensure migration security.

CDM works in push-pull mode. CDM pulls data from the migration source and pushes the data to the migration destination. Data access operations are initiated by CDM. SSL will be used if the data source (such as RDS) supports it. During the migration, the usernames and passwords of the migration source and destination are required. Such information is stored in the database of the CDM instance. Protecting such information is critical to ensure CDM security.


.. figure:: /_static/images/en-us_image_0000002269115445.png
   :alt: **Figure 2** Migration principles

   **Figure 2** Migration principles
