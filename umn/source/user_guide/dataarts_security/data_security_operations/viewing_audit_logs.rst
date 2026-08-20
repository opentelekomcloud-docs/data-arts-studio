:original_name: dataartsstudio_01_1181.html

.. _dataartsstudio_01_1181:

Viewing Audit Logs
==================

DataArts Security provides detailed data operation logs for GaussDB(DWS), DLI, and Hive data sources. The logs contain the time, users, objects, and types of operations. Based on these logs, you can quickly audit data operations and better manage data security.

Prerequisites
-------------

-  To audit access to MRS Hive data sources, ensure that the following conditions are met:

   -  The CDM cluster used as the agent in the MRS Hive data connection is of version 2.10.0.300 or later.
   -  The user in the MRS Hive data connection must meet the following conditions:

      -  It is assigned a role that has at least the cluster resource management permission. (You can directly assign the default Manager_operator role to the user.)
      -  A Hive user group has been configured for the user.

-  To audit access to GaussDB(DWS) data sources, ensure that the following conditions are met:

   -  The audit function has been enabled for GaussDB(DWS) clusters.

      The audit function is enabled by default. If it is disabled, set **audit_enabled** to **ON** by following the instructions in "Modifying Database Parameters" in *GaussDB(DWS) User Guide*.

   -  The items to be audited have been enabled.

      For details about GaussDB(DWS) audit items and how to enable them, see "Configuring the Database Audit Logs" in *GaussDB(DWS) User Guide*.

   -  For the GaussDB(DWS) data source, if separation of duties is disabled, users with the SYSADMIN attribute can view audit records by default. If separation of duties is enabled, only users with the AUDITADMIN attribute can view audit records. Therefore, ensure that the account in the data connection or the current user has the preceding permissions. (Before enabling fine-grained authentication, use the account in the data connection to view audit records. If fine-grained authentication is enabled, use the current IAM user to view audit records.)

Constraints
-----------

-  For the GaussDB(DWS) data source, you need to manually enable the audit function and audit items for the GaussDB(DWS) cluster for data access audit. If separation of duties is disabled, users with the SYSADMIN attribute can view audit records by default. If separation of duties is enabled, only users with the AUDITADMIN attribute can view audit records. Therefore, you must ensure that the account of the data connection or the current account has the preceding permissions. (If fine-grained authentication is disabled, you can use the account of the data connection to view audit records. If fine-grained authentication is enabled, you can use the current IAM user to view audit records.)
-  For MRS data, viewing the audit data depends on the agent (CDM cluster) version in the data connection. Ensure that the CDM cluster version is 2.10.0.300 or later. The user in the MRS Hive data connection must meet the following conditions:

   -  It is assigned a role that has at least the cluster resource management permission. (You can directly assign the default Manager_operator role to the user.)
   -  A Hive user group has been configured for the user.

Viewing Data Access Logs
------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Data Access Audit**.


   .. figure:: /_static/images/en-us_image_0000002269120153.png
      :alt: **Figure 1** Data Access Audit

      **Figure 1** Data Access Audit

#. You can switch between tabs to view the audit logs of different data sources. By default, logs generated in the last one hour are displayed. You can customize the time range, which can be up to one month.

   -  DWS audit log: The log list uses the latest DWS data connection by default. Click **Log Details** to view information about a log.

      Click **Export** to export DWS audit logs on the current page in JSON format.


      .. figure:: /_static/images/en-us_image_0000002234240764.png
         :alt: **Figure 2** DWS audit logs

         **Figure 2** DWS audit logs

   -  MRS Hive audit logs: By default, the MRS Hive log list does not display log content. You can search for logs based on conditions. The search results are displayed by tab page. A maximum of five tab pages of search results can be displayed.


      .. figure:: /_static/images/en-us_image_0000002269120137.png
         :alt: **Figure 3** MRS Hive audit logs

         **Figure 3** MRS Hive audit logs

   -  DLI audit logs: By default, the DLI log list displays log information. Click **Log Details** to view information about a log.


      .. figure:: /_static/images/en-us_image_0000002269200217.png
         :alt: **Figure 4** DLI audit logs

         **Figure 4** DLI audit logs
