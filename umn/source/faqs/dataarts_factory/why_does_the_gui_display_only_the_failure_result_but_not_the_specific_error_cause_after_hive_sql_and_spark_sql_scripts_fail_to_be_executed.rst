:original_name: dataartsstudio_03_0059.html

.. _dataartsstudio_03_0059:

Why Does the GUI Display Only the Failure Result but Not the Specific Error Cause After Hive SQL and Spark SQL Scripts Fail to Be Executed?
===========================================================================================================================================

Check whether the data connection used by the Hive SQL and Spark SQL scripts is direct connection or proxy connection.

In direct connection mode, DataArts Studio users submit the scripts to MRS through APIs and then check whether the scripts are executed successfully. MRS does not send the specific error cause to DataArts Studio. Therefore, the GUI displays only the execution result (success or failure) but does not display the error cause.

If you want to view the error cause, go to the job management page of MRS.
