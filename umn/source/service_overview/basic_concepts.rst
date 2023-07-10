:original_name: dataartsstudio_07_004.html

.. _dataartsstudio_07_004:

Basic Concepts
==============

DataArts Studio Instance
------------------------

A DataArts Studio instance is the minimum unit of compute resources provided for users. You can create, access, and manage multiple DataArts Studio instances at the same time. A DataArts Studio instance allows you to access seven modules: Management Center, DataArts Architecture, DataArts Migration, DataArts Factory, DataArts Quality, DataArts Catalog, and DataArts DataService. You can obtain DataArts Studio instances with specifications tailored to your service requirements.

Workspace
---------

A workspace enables admins to manage member permissions, resources, and configurations of the underlying compute engines.

The workspace is a basic unit for member management as well as role and permission assignment. Each team must have an independent workspace.

You can access the Management Center, DataArts Factory, and DataArts Migration modules, but only after your account is added to a workspace and assigned the permissions required to perform such operations.

Member and Role
---------------

A member is a account that has been assigned the permissions required to access and use a workspace. As an admin, when you add a workspace member, you must set a role.

A role is a predefined combination of permissions. Different roles have different permission sets. After a role is assigned to a member, the member has all the permissions of that role. Each member must have at least one role, and they can have multiple roles at the same time.

DataArts Migration
------------------

A DataArts Migration cluster is the smallest resource unit provided to users. DataArts Migration clusters run on ECSs. You can create data migration tasks in a CDM cluster and migrate data between homogeneous or heterogeneous data sources in the cloud and on-premises.

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
