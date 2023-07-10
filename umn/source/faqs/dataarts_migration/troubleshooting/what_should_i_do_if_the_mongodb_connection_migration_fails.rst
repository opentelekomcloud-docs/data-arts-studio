:original_name: dataartsstudio_03_0072.html

.. _dataartsstudio_03_0072:

What Should I Do If the MongoDB Connection Migration Fails?
===========================================================

By default, the **userAdmin** role has only the permissions to manage roles and users and does not have the read and write permissions on a database.

If the MongoDB connection fails to be migrated, you need to view the user permission information in the MongoDB connection to ensure that the user has the read and write permissions on the specified database.
