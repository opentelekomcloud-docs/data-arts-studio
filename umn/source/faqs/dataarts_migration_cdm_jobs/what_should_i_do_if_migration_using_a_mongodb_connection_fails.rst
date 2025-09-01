:original_name: dataartsstudio_03_0072.html

.. _dataartsstudio_03_0072:

What Should I Do If Migration Using a MongoDB Connection Fails?
===============================================================

Symptom
-------

Migration using a MongoDB connection fails.

Solution
--------

By default, the **userAdmin** role has only the permissions to manage roles and users and does not have the read and write permissions on a database.

If migration using a MongoDB connection fails, you need to view the user permission information in the MongoDB connection to ensure that the user has the read and write permissions on the specified database.
