:original_name: dataartsstudio_03_0046.html

.. _dataartsstudio_03_0046:

What Should I Do If Error Message "FATAL: Invalid username/password,login denied" Is Displayed During the GaussDB(DWS) Connectivity Check When Fine-grained Authentication Is Enabled?
======================================================================================================================================================================================

Possible Causes
---------------

The current user is not synchronized to the GaussDB(DWS) data source or does not have th GaussDB(DWS) Database Access permission.

Solution
--------

Synchronize the current login user to the GaussDB(DWS) data source, grant the DWS Database Access permissions to the user, and test the connectivity again.
