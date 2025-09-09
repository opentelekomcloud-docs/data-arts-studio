:original_name: dataartsstudio_03_0334.html

.. _dataartsstudio_03_0334:

What Should I Do If I Cannot Obtain the Schema Name When Creating an Oracle Relational Database Migration Job?
==============================================================================================================

Symptom
-------

I cannot obtain the schema name when creating an Oracle relational database migration job.

Possible Cause
--------------

The latest ORACLE_8 driver, which is not supported, may have been uploaded, for example, the Oracle Database 21c (21.3) driver.

Solution
--------

You are advised to use the ojdbc8.jar driver in Oracle Database 12c. You can download the driver from https://www.oracle.com/database/technologies/jdbc-ucp-122-downloads.html.
