:original_name: dataartsstudio_02_0015.html

.. _dataartsstudio_02_0015:

Example of Using Data Development APIs
======================================

Scenarios
---------

DataArts Studio helps enterprises quickly build an end-to-end intelligent data system that covers the entire process from data ingestion to data analytics. The system can eliminate data silos, unify data standards, accelerate data monetization, and promote digital transformation.

The following describes how to create a script by calling the :ref:`Creating a Script <dataartsstudio_02_0097>` API. For details, see :ref:`Calling APIs <dataartsstudio_02_0008>`.

Prerequisites
-------------

You have planned the region where Data Development is located and determined the endpoint for calling an API based on the region.

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. You can obtain endpoints from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Creating a Shell Script
-----------------------

The following is an example of creating a shell script:

.. code-block::

   {
   "name":"echoTimeShell",
   "type":"Shell",
   "content":"echo a",
   "connectionName":"con"
   }

-  **name** indicates a custom script name, for example, **echoTimeShell**.
-  **type** indicates the type of the script.
-  **content** indicates the script content.
-  **connectionName** indicates the name of the data connection associated with the script.

Creating a DLI SQL Script
-------------------------

You can also create a DLI SQL script. The following is an example:

.. code-block::

   {
   "name":"dlisql1",
   "type":"DLISQL",
   "content":"show tables",
   "connectionName":"dliCon1",
   "database":"testDatabase1",
   "queueName":"queue1"
   }

-  **name** indicates a custom script name, for example, **dlisql1**.
-  **type** indicates the type of the script.
-  **content** indicates the script content.
-  **connectionName** indicates the name of the data connection associated with the script.
-  **database** indicates the name of the associated database when the script is executed.
-  **queueName** indicates the name of the queue running on DLI when the SQL statement is executed.
