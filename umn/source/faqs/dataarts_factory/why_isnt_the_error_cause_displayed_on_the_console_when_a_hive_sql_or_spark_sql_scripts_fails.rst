:original_name: dataartsstudio_03_0059.html

.. _dataartsstudio_03_0059:

Why Isn't the Error Cause Displayed on the Console When a Hive SQL or Spark SQL Scripts Fails?
==============================================================================================

Possible Causes
---------------

This issue may be caused by the connection mode.

Solution
--------

Check whether the data connection used by the Hive SQL and Spark SQL scripts is an MRS API connection or proxy connection.

In MRS API connection mode, DataArts Studio users submit scripts to MRS through APIs and then check whether the scripts are executed successfully. MRS does not send the specific error cause to DataArts Studio. Therefore, the GUI displays only the execution result (success or failure) but does not display the error cause.

In proxy connection mode, DataArts Studio users submit and run scripts, and check whether the scripts are executed successfully. In addition, the error information and script execution results are displayed in the logs on the DataArts Factory script execution page.

If you want to view the error cause, go to the job management page on the MRS console.
