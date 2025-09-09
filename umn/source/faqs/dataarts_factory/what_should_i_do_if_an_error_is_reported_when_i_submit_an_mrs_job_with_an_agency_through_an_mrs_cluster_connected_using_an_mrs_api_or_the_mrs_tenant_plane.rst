:original_name: dataartsstudio_03_0630.html

.. _dataartsstudio_03_0630:

What Should I Do If an Error Is Reported When I Submit an MRS Job with an Agency Through an MRS Cluster Connected Using an MRS API or the MRS Tenant Plane?
===========================================================================================================================================================

Symptom
-------

Error messages:

#. Failed to query the user who submits the job on MRS Manager. The error code is 0191.
#. The current user does not exist on MRS Manager. Grant the user sufficient permissions on IAM and then perform IAM user synchronization on the Dashboard tab page. The error code is 0192.

Solution
--------

If either of the preceding errors is reported when you submit an MRS job (such as an MRS Hive SQL, MRS Spark SQL, and MRS Spark Python job) with a public agency or job agency through an MRS cluster connected using an MRS API or the MRS tenant plane, you need to add the tenant to which the current user belongs as a machine-machine user on MRS Manager and grant permissions of corresponding components to the user.
