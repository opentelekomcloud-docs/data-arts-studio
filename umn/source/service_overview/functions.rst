:original_name: dataartsstudio_07_005.html

.. _dataartsstudio_07_005:

Functions
=========

DataArts Migration: Efficient Ingestion of Multiple Heterogeneous Data Sources
------------------------------------------------------------------------------

DataArts Migration can help you seamlessly migrate batch data between 30+ homogeneous or heterogeneous data sources. You can use it to ingest data from both on-premises and cloud-based data sources, including file systems, relational databases, data warehouses, NoSQL databases, big data services, and object storage.

DataArts Migration uses a distributed compute framework and concurrent processing techniques to help you migrate enterprise data in batches without any downtime and rapidly build desired data structures.


.. figure:: /_static/images/en-us_image_0000002234068868.png
   :alt: **Figure 1** DataArts Migration

   **Figure 1** DataArts Migration

You can manage data on the wizard-based task management page. You can easily create data migration tasks that meet your requirements. DataArts Migration provides the following functions:

-  **Table/File/Entire DB migration**

   You can migrate tables or files in batches, and migrate an entire database between homogeneous and heterogeneous database systems. You can include hundreds of tables in a single job.

-  **Incremental data migration**

   You can migrate files, relational databases, and HBase in an incremental manner. You can perform incremental data migration by using WHERE clauses and variables of date and time.

-  **Migration in transaction mode**

   When a batch data migration job fails to be executed, data will be rolled back to the state before the job started and data in the destination table will be automatically deleted.

-  **Field conversion**

   Field conversion includes anonymization, character string operations, and date operations.

-  **File encryption**

   You can encrypt files that are migrated to a cloud-based file system in batches.

-  **MD5 verification**

   MD5 is used to check file consistency from end to end.

-  **Dirty data archiving**

   Data that fails to be processed during migration, is filtered out and is not compliant with conversion or cleansing rules is recorded in dirty data logs. You can easily analyze abnormal data. You can also set a threshold for the dirty data ratio to determine whether a task is successful.

DataArts Architecture: Visualized, Automated, and Intelligent Data Modeling
---------------------------------------------------------------------------

DataArts Architecture incorporates data governance methods. You can use it to visualize data governance operations, connect data from different layers, formulate data standards, and generate data assets. You can standardize your data through ER modeling and dimensional modeling. DataArts Architecture is a good option for unified construction of metric platforms. With DataArts Architecture, you can build standard metric systems to eliminate data ambiguity and facilitate communications between different departments. In addition to unifying computing logic, you can use it to query data and explore data value by subject.


.. figure:: /_static/images/en-us_image_0000002269108049.png
   :alt: **Figure 2** DataArts Architecture

   **Figure 2** DataArts Architecture

DataArts Architecture offers the following major functions:

-  **Subject design**

   You can use DataArts Architecture to build unified data classification systems for directory-based data management. Data classification, search, evaluation, and usage are easier than ever before. DataArts Architecture provides hierarchical architectures that help you define and classify data assets, allowing data consumers to better understand and trust your data assets.

-  **Data standards**

   DataArts Architecture can help you create process-based and systematic data standards that fit your needs. Peered with the national and industry standards, these standards enable you to standardize your enterprise data and improve data quality, ensuring that your data is trusted and usable.

-  **Data modeling**

   Data modeling involves building unified data model systems. You can use DataArts Architecture to build a tiered, enterprise-class data system based on data specifications and models. The system incorporates data from the public layer and subject libraries, significantly reducing data redundancy, silos, inconsistency, and ambiguity. This allows freer flow of data, better data sharing, and faster innovation.

   The following data modeling methods are supported:

   -  **ER modeling**

      ER modeling involves describing the business activities of an enterprise, and ER models are compliant with the third normal form (3NF). You can use ER models for data integration, which merges and classifies data from different systems by similarity or subject. However, you cannot use ER models for decision-making.

   -  **Dimensional modeling**

      Dimensional modeling involves constructing bus matrices to extract business facts and dimensions for model creation. You need to sort out business requirements for constructing metric systems and creating summary models.

   -  **Data mart**

      A data mart (DM) aggregates data from multiple layers and consists of a specific analysis object and its related metrics. The DM provides all statistical data by subject.

DataArts Factory: One-stop Collaborative Development
----------------------------------------------------

DataArts Factory provides an intuitive UI and built-in development methods for script and job development. DataArts Factory also supports fully hosted job scheduling, O&M, and monitoring, and incorporates industry data processing pipelines. You can create data development jobs in a few steps, and the entire process is visual. Online jobs can be jointly developed by multiple users. You can use DataArts Factory to manage big data cloud services and quickly build a big data processing center.


.. figure:: /_static/images/en-us_image_0000002269188109.png
   :alt: **Figure 3** DataArts Factory architecture

   **Figure 3** DataArts Factory architecture

DataArts Factory allows you to manage data, develop scripts, and schedule and monitor jobs. Data analysis and processing are easier than ever before.

-  **Data management**

   -  You can manage multiple types of data warehouses, such as GaussDB (DWS), DLI, and MRS Hive.
   -  You can use the graphical interface and data definition language (DDL) to manage database tables.

-  **Script development**

   -  Provides an online script editor that allows more than one operator to collaboratively develop and debug SQL, Python, and Shell scripts online.
   -  You can use Variables.

-  **Job development**

   -  DataArts Factory provides a graphical designer that allows you to rapidly develop workflows through drag-and-drop and build data processing pipelines.
   -  DataArts Factory is preset with multiple task types such as data integration, SQL, and Shell. Data is processed and analyzed based on task dependencies.
   -  You can import and export jobs.

-  **Resource management**

   You can centrally manage file, jar, and archive resources used during script and job development.

-  **Job scheduling**

   -  You can schedule jobs to run once or recursively and use events to trigger scheduling jobs.
   -  Job scheduling supports a variety of hybrid orchestration tasks. The high-performance scheduling engine has been tested by hundreds of applications.

-  **O&M and monitoring**

   -  You can run, suspend, restore, or terminate a job.
   -  You can view the operation details of each job and each node in the job.
   -  You can use various methods to receive notifications when a job or task error occurs.

DataArts Quality: Verifiable and Controllable Data Quality
----------------------------------------------------------

DataArts Quality can monitor your data quality, and screen out unqualified data in a timely manner.

-  **Data quality monitoring**

   You can create data quality rules to check whether the data in your databases is accurate in real time.

   Qualified data must meet the following requirements: integrity, validity, timeliness, consistency, accuracy, and uniqueness. You can standardize data and periodically monitor data across columns, rows, and tables based on quality rules.


   .. figure:: /_static/images/en-us_image_0000002234228716.png
      :alt: **Figure 4** Data quality rule system

      **Figure 4** Data quality rule system

DataArts Catalog: End-to-End Data Asset Visualization
-----------------------------------------------------

With enterprise-class metadata management, you can define your data assets in business terms familiar to data consumers. Data drilling and source tracing are also supported. A data map shows data lineage and a global view of your data assets. Data search, operations, and monitoring are more intelligent than before.

-  **Metadata management**

   Metadata management is vital for data lake governance. You can create policies to collect metadata from your data lake, and customize metadata models to import metadata in batches, associate business data with technical data, manage and use full-link data lineages.


   .. figure:: /_static/images/en-us_image_0000002234068876.png
      :alt: **Figure 5** Full-link data lineages

      **Figure 5** Full-link data lineages

-  **Data map**

   Data maps facilitate data search, analysis, development, mining, and operations. They provide lineage information and impact analysis. Data maps make data search easier and faster than before.

   -  Keyword search and fuzzy search are supported, helping you quickly locate the data you need.
   -  You can search for tables by name. Table details are displayed as soon as the matching table is found. You can also add more descriptions for the searched table.
   -  Data maps display the source, destination, and processing logic of a table field.
   -  You can classify and tag data assets as required.

DataArts DataService: Improved Access, Query, and Search Efficiency
-------------------------------------------------------------------

DataArts DataService enables you to manage your enterprise APIs centrally, and controls the access to your subjects, profiles, and metrics. It helps improve the experience for data consumers and the efficiency of data asset monetization. You can use DataArts DataService to generate APIs and register the APIs with DataArts DataService for unified management and publication.

DataArts DataService uses a serverless architecture. You only need to focus on the API query logic, without worrying about infrastructure such as the runtime environment. DataArts DataService supports elastic scaling of compute resources, significantly reducing O&M costs.


.. figure:: /_static/images/en-us_image_0000002269108033.png
   :alt: **Figure 6** DataArts DataService architecture

   **Figure 6** DataArts DataService architecture

DataArts Security: All-Round Protection
---------------------------------------

-  **Cyber security**

   Tenant isolation and access permissions control are implemented to protect the privacy and data security of systems and users based on preset network isolation, security group, and security hardening rules.

-  **User permissions control**

   Role-based access control involving associating roles with permissions and supports fine-grained permission policies to meet different authorization requirements. DataArts Studio provides four roles: admin, developer, deployer, operator, and viewer. Each role has different permissions.

-  **Data security**

   DataArts Studio provides the review mechanism for key processes.

   Data is managed by level and category throughout the lifecycle, ensuring data privacy compliance and traceability.
