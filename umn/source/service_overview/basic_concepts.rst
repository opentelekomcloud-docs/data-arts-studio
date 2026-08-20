:original_name: dataartsstudio_07_004.html

.. _dataartsstudio_07_004:

Basic Concepts
==============

DataArts Studio Instance
------------------------

A DataArts Studio instance is the minimum unit of compute resources provided for users. You can create, access, and manage multiple DataArts Studio instances at the same time. A DataArts Studio instance allows you to access the following modules: Management Center, DataArts Architecture, DataArts Migration, DataArts Factory, DataArts Quality, and DataArts Catalog. You can obtain DataArts Studio instances with specifications tailored to your service requirements.

Workspace
---------

A workspace enables admins to manage member permissions, resources, and configurations of the underlying compute engines.

The workspace is a basic unit for member management as well as role and permission assignment. Each team must have an independent workspace.

You can access the Management Center, DataArts Catalog, DataArts Quality, DataArts Architecture, DataArts DataService, DataArts Security, DataArts Factory, and DataArts Migration modules only after your account is added to a workspace and assigned the permissions required to perform such operations.

Member and Role
---------------

A member is a account that has been assigned the permissions required to access and use a workspace. As an admin, when you add a workspace member, you must set a role.

A role is a predefined combination of permissions. Different roles have different permission sets. After a role is assigned to a member, the member has all the permissions of that role. Each member must have at least one role, and they can have multiple roles at the same time.

CDM Cluster
-----------

A CDM cluster run on an ECS. You can create data migration tasks in a CDM cluster and migrate data between homogeneous or heterogeneous data sources in the cloud and on-premises data center.

Data Source
-----------

A data source is a medium for storing or processing data, such as a relational database, data warehouse, and data lake. Different data sources use different data storage, transmission, processing, and application modes, as well as different scenarios, technologies, and tools.

Source Data
-----------

Source data is the data that is not processed after created. In data management, source data refers to the data directly from source files (such as service system databases, offline files, and IoT files) or copies of source files.

Data Connection
---------------

A data connection is a collection of details required for accessing where data is stored, including the connection type, name, and login information.

Concurrency
-----------

Concurrency refers to the maximum number of threads that can be concurrently read from the source in a data integration job.

Dirty Data
----------

Dirty data refers to the data meaningless to business or in invalid format. For example, if the source data of the VARCHAR type is not properly converted, it cannot be written to the destination column of the INT type.

Job (DataArts Factory)
----------------------

A job is composed of one or more nodes that run together to complete data operations.

Node
----

A node is a definition for the actions to be performed on your data. For example, you can use the MRS Spark node to execute predefined Spark jobs in MRS.

Solution
--------

A solution is a series of convenient and systematic management operations that meet service requirements and objectives. Each solution can contain one or more business-related jobs, and each job can be reused by multiple solutions.

Resource
--------

A resource is the self-defined code or text file that you upload. It is invoked when nodes run.

Expression Language (EL)
------------------------

Node parameters in data development jobs can be dynamically generated based on the running environment using ELs. An EL often uses simple arithmetic and calculation logic and references embedded objects including job objects and tool objects.

Environment Variable
--------------------

An environmental variable is an object with a specific name in the operating system. It contains information to be used by one or more applications.

PatchData
---------

PatchData is an instance that was generated in the past by a repeatedly scheduled job.

Data Governance
---------------

Data governance is the process by which you can manage, utilize, and protect your enterprise data throughout the data lifecycle. It includes access control, data quality management, and risk management.

Data Survey
-----------

A data survey involves collecting data that is generated when sorting business requirements, creating business processes, and classifying data subjects based on the existing business data and industry status.

Subject Design
--------------

Subject design provides hierarchical architectures that help you define and classify data assets, helping you better understand your data assets and clarify the relationship between business domains and business objects.

Subject Area Group
------------------

A subject area group is a collection of subject areas that have the same business features.

Subject Area
------------

A subject area is a high-level, non-overlapping classification of data used to manage business objects.

Business Object
---------------

A business object includes important information about people, events, and things that are indispensable to your enterprise's operations and management.

Process Design
--------------

Process design is to generate a structured framework of data processing process, including the categories, levels, boundaries, scope, and input/output relationships, and reflect the business models and characteristics of your enterprise.

Data Standard
-------------

A data standard is the description of data meanings and business rules that must be complied with by your enterprise. It describes the common understanding of certain data at the company level.

Lookup Table
------------

A lookup table includes a series of allowed values and additional text descriptions that are generally associated with data standards to generate a range of values for the verification of quality monitoring rules.

Data Warehouse Planning
-----------------------

DataArts Architecture provides four default data warehouse layers, including SDI, DWI, DWR, and DM. You can customize data warehouse layers. Data warehouse layers and models are centrally managed.

SDI
---

Source Data Integration (SDI) copies data from source systems.

DWI
---

Data Warehouse Integration (DWI) integrates and cleanses data from multiple source systems, and builds ER models based on the third normal form (3NF).

DWR
---

Data Warehouse Report (DWR) is based on multi-dimensional models and its data granularity is the same as that of DWI.

DM
--

Data Mart (DM) is where multiple types of data are summarized and displayed.

ER Modeling
-----------

Entity Relationship (ER) modeling describes business activities of an enterprise. ER models are compliant with the third normal form (3NF). You can use ER models for data integration, which merges and classifies data from different systems by similarity or subject. However, you cannot use ER models for decision-making.

Dimensional Modeling
--------------------

A dimensional model is generally created for data analysis and decision-making. Its aim is to complete the analysis of complex and multiple user requirements at full speed.

A multidimensional model is a fact table that consists of numeric measure metrics. The fact table is associated with a group of dimensional tables that contain description attributes through primary or foreign keys.

In the DataArts Architecture module of DataArts Studio, dimensional modeling involves constructing bus matrices to extract business facts and dimensions for model creation. You need to sort out business requirements for constructing metric systems and creating summary models.

Metric (DataArts Architecture)
------------------------------

A metric is a statistical value that measures the overall characteristic of a target and indicates the business situation in a business activity of an enterprise. A metric consists of its name and value. The metric name and its meaning reflect the quality and quantity of the metric. The metric value reflects the quantifiable values of the specified time, location, and condition of the metric.

Measure
-------

A measure is a quantifiable value used to measure business situations. It usually refers to a number, for example, an amount, quantity, or period. Measures are numerical values that do not have explicit business relevance, but they can be converted into metrics in a business context.

Dimension
---------

A dimension is used to observe and analyze business data. It supports data aggregation, drilling, and slicing analysis and is used as the GROUP BY condition in SQL statements. Most dimensions have a hierarchical structure, for example, geographic dimension (including country, region, province, and city levels) and time dimension (including annually, quarterly, and monthly levels).

Atomic Metric
-------------

An atomic metric is generated based on dimension tables and fact tables of a multidimensional model. The business objects and the finest data granularity of an atomic metric are consistent with those of the multidimensional model. An atomic metric usually consists of measures and attributes related with measures and business objects, all of which aim to support agile self-service consumption of derivative metrics, for example, the number of retail stores (including the store names and levels).

Derivative Metric
-----------------

A derivative metric is derived from the combination of modifiers, standards, dimensions, and atomic metrics. Modifiers, standards, and definitions are usually the attributes of an atomic metric. An example is the in-store promoter coverage.

Compound Metric
---------------

A compound metric is generated by derivative metrics. The dimensions and modifiers of a compound metric are the same as those of the derivative metric. (No new dimensions and modifiers for a compound metric can be generated if its derivative metric has no dimensions and modifiers.)

Data Quality Rule
-----------------

A data quality rule is a logical unit used to determine whether the data meets business requirements.

Data Asset
----------

A data asset is a resource that is owned or controlled by your enterprise and can be monetized in the future. The data resource is recorded in physical or electronic mode. Not all the data of your enterprise can be considered as a data asset. A data asset must be a data resource that can generate value for your enterprise.

Data Map
--------

A data map is a data search-driven tool that displays the source, quality, distributions, standards, flow directions, and relationships of data in graphical forms. You can use a data map to easily find, read, and consume data.

Metadata
--------

Metadata is data about data. Specifically, it is information about the organization, domain, and relationships of data. Metadata includes metadata entities and metadata elements. A metadata element is a basic unit of metadata, and several related metadata elements form a metadata entity.

In DataArts Studio, metadata may be used to describe the attributes of data (such as the data connection, type, name, and size) or other related information of data (such as the data owner, tag, category, and security level).

Metadata Collection
-------------------

You can customize a collection policy to collect technical metadata from data sources.

Data Asset Report
-----------------

A data asset report provides an overview of the data asset and their statistics.

DataArts DataService
--------------------

DataArts DataService provides data as a product based on data distribution and release frameworks. The product provided meets your requirements for real-time data and industry standards. It can be reused and shared securely.

API Gateway
-----------

API Gateway provides API hosting services through the API gateway, covering the full life-cycle management of API release, management, O&M, and sales. It helps you easily implement microservice aggregation, frontend and backend separation, system integration, and open functions and data to partners and developers in a quick, cost-effective, but low risky way.
