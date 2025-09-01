:original_name: dataartsstudio_01_0304.html

.. _dataartsstudio_01_0304:

Adding Fields
=============

Scenario
--------

-  After job parameters are configured, field mapping needs to be configured. You can customize new fields by clicking |image1| on the **Map Field** page.
-  If files are migrated between FTP, SFTP, OBS, and HDFS and the migration source's **File Format** is set to **Binary**, files will be directly transferred, free from field mapping.
-  In other scenarios, CDM automatically maps fields of the source table and the destination table. You need to check whether the mapping and time format are correct. For example, check whether the source field type can be converted into the destination field type.

You can click |image2| on the **Map Field** page and select **Add** to customize a new field. This field is usually used to mark the database source to ensure the integrity of the data imported to the migration destination.


.. figure:: /_static/images/en-us_image_0000002234237032.png
   :alt: **Figure 1** Field mapping

   **Figure 1** Field mapping

Currently, the following field types are supported:

-  **Constant Parameter**

   Constant parameters are fixed parameters and do not need to be reconfigured. For example, **lable** = **friends** is used to identify a constant value.

-  **Variables**

   You can use variables such as time macros, table name macros, and version macros to mark database source information. The variable syntax is ${variable}, where **variable** indicates a variable. For example, **input_time** = **${timestamp()}** indicates the timestamp of the current time.

-  Expression

   You can use the expression language to dynamically generate parameter values based on the running environment. The expression syntax is #{expr}, where **expr** indicates an expression. For example, **time** = **#{DateUtil.now()}** is used to identify the current date string.

Constraints
-----------

-  On the **Map Field** tab page, if CDM fails to obtain all columns by obtaining sample values (for example, when data is exported from HBase, CloudTable, or MongoDB, there is a high probability that CDM failed to obtain all columns), you can click |image3| and select **Add a new field** to add new fields to ensure that the data imported to the migration destination is complete.
-  When a relational database, Hive, DLI, or MRS Hudi is used as the migration source, sample values cannot be obtained.
-  When SQLServer is the destination, fields of the timestamp type cannot be written. You must change their type (for example, to datetime) so that they can be written.
-  Column names are displayed when the source of the migration job is OBS, CSV files are to be migrated, and parameter **Extract first row as columns** is set to **Yes**.
-  Field mapping is not involved when the binary format is used to migrate files to files.
-  In the automatic table creation scenario, you need to manually add fields to the destination table in advance and then add fields to the field mapping.
-  After a field is added, its sample value is not displayed on the console. This does not affect the field value transmission. CDM directly writes the field value to the destination end.
-  If the field mapping is incorrect, you can adjust the field mapping by dragging fields or clicking |image4| to map fields in batches.
-  If the data is imported to DWS, you need to select the distribution columns in the destination fields. You are advised to select the distribution columns according to the following principles:

   #. Use the primary key as the distribution column.
   #. If multiple data segments are combined as primary keys, specify all primary keys as the distribution column.
   #. In the scenario where no primary key is available, if no distribution column is selected, DWS uses the first column as the distribution column by default. As a result, data skew risks exist.

-  If a source field type is not supported, convert the field type to a type supported by CDM by referring to :ref:`Converting Unsupported Data Types <dataartsstudio_01_0209>`.

.. |image1| image:: /_static/images/en-us_image_0000002269197469.png
.. |image2| image:: /_static/images/en-us_image_0000002234077148.png
.. |image3| image:: /_static/images/en-us_image_0000002269116389.png
.. |image4| image:: /_static/images/en-us_image_0000002234077176.png
