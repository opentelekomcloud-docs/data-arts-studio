:original_name: dataartsstudio_03_0109.html

.. _dataartsstudio_03_0109:

What Should I Do If an Error Is Reported Because the Field Type Mapping Does Not Match During Data Migration Using CDM?
=======================================================================================================================

Symptom
-------

When you use CDM to migrate data to DWS, the migration job fails and the error message "value too long for type character varying" is displayed in the execution log.

Possible Cause
--------------

The possible cause is that the type of the source table does not match that of the target table. For example, the **dli** field of the source is of the string type, and the **dws** field of the destination is of the varchar(50) type. As a result, the precision is default and the error message "value too long for type character varying" is reported. This issue also occurs for conversion from string to bigint and from bigint to int.

Solution
--------

-  Locate the field that is incorrectly mapped based on the error information and contact the DBA to modify the table structure.
-  If this issue occurs only for a small amount of data, you can configure the dirty data policy to solve the issue.
