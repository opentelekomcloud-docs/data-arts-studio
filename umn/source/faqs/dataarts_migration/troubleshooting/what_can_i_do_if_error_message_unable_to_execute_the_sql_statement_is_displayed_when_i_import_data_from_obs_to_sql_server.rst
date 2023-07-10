:original_name: dataartsstudio_03_0106.html

.. _dataartsstudio_03_0106:

What Can I Do If Error Message "Unable to execute the SQL statement" Is Displayed When I Import Data from OBS to SQL Server?
============================================================================================================================

Symptom
-------

When CDM is used to import data from OBS to SQL Server, the job fails to be executed and error message "Unable to execute the SQL statement. Cause: "String or binary data truncated" is displayed.

Possible Cause
--------------

The data in OBS exceeds the length limit of the SQL Server database.

Solution
--------

When creating a table in the SQL Server database, increase the length of the database field. The length of the database field must be greater than that of the data in OBS.
