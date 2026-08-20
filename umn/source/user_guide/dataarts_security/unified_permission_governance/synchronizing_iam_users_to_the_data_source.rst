:original_name: dataartsstudio_01_1154.html

.. _dataartsstudio_01_1154:

Synchronizing IAM Users to the Data Source
==========================================

By default, when a user accesses the MRS or GaussDB(DWS) data source through a data connection in DataArts Studio, the username and password in the data connection are used for authentication. To manage users' data access permissions based on user information, you need to synchronize user information from IAM to the data source so that different users have different identities in the data source and can use their own user information for authentication during data permission management.

Note that each MRS/GaussDB(DWS) cluster in a DataArts Studio instance can have only one user synchronization task. User synchronization tasks are configured at the DataArts Studio instance level, and data can be exchanged between workspaces.

Prerequisites
-------------

-  You have created a GaussDB(DWS) or MRS Ranger data connection in Management Center. For details, see :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.
-  You have configured permissions for the **dlg_agency** by referring to :ref:`Authorizing dlg_agency <dataartsstudio_01_1152>`.

Constraints
-----------

-  In a DataArts Studio instance, each MRS/GaussDB(DWS) cluster can have only one user synchronization task.
-  If a user synchronization task keeps running for more than half an hour, the task will be stopped due to timeout. If the synchronization fails for more than 10 consecutive times, the task will be stopped.
-  Federated users have only user group information and cannot be synchronized.
-  The data source synchronizes only the user information of its own tenant and cannot synchronize the clusters from data sources of other tenants who are not connected through IP connections.
-  User synchronization is available only for MRS Hive and GaussDB(DWS) data sources. For the GaussDB(DWS) data source, user synchronization is mandatory. For the MRS data source, you can create MRS users with the same name as IAM users so that user synchronization is not needed. DLI uses IAM users for authentication. Therefore, user synchronization is not required.
-  The restrictions on MRS user synchronization tasks are as follows:

   -  If a human-machine user with the same name as the user to be synchronized exists in MRS, the MRS user synchronization task fails. No error message is displayed for this error. You are advised to use either of the following methods to resolve this issue:

      -  Use the IAM user synchronization function on the MRS cluster details page, rather than run the user synchronization task on the DataArts Security console again. The IAM user synchronization function is similar to the user synchronization task, except that if there are users with the same name, only these users will fail to be synchronized, and the other users can still be synchronized successfully.
      -  Log in to MRS Manager, choose **System** > **Permission** > **User**, and delete the human-machine user with the same name as the user to be synchronized.
      -  On the IAM console, delete the user to be synchronized with the same name as the MRS human-machine user.

   -  Before MRS data source synchronization, ensure that the user or user group has at least one of the following permissions. Otherwise, the user or user group will not be synchronized.

      -  Tenant Administrator
      -  MRS FullAccess
      -  MRS CommonOperations
      -  MRS ReadOnlyAccess
      -  MRS Administrator
      -  MRS Admin
      -  MRS User
      -  MRS Viewer
      -  Self Define (any custom policy)

-  The restrictions on GaussDB(DWS) user synchronization tasks are as follows:

   -  GaussDB(DWS) user synchronization is supported only when the guest_agent version of a GaussDB(DWS) cluster is 8.2.1, or later than 8.2.1 and earlier than 9.0.0. For details about how to check the guest_agent version of a GaussDB(DWS) cluster, see :ref:`Viewing the guest_agent Version of a GaussDB(DWS) Cluster <dataartsstudio_01_1153__section1153213235185>`.
   -  Before GaussDB(DWS) user synchronization, ensure that the users at least have the DWS Database Access permission. Otherwise, the synchronization will fail.
   -  To synchronize IAM users to GaussDB(DWS), you must configure the following permissions for the **dlg_agency**. For details, see :ref:`Authorizing dlg_agency <dataartsstudio_01_1152>`.

      -  dws:dbAuthority:syncIamUse
      -  iam:users:listUsers
      -  iam:groups:listGroups
      -  iam:users:listUsersForGroup

   -  GaussDB(DWS) does not support user groups. When an IAM user group is synchronized to GaussDB(DWS), a user named in the *iam_group\_*\ **User group ID** format will be created in GaussDB(DWS), and the *iam_group\_*\ **User group ID** user corresponding to the user group deleted from IAM will be deleted from GaussDB(DWS). Do not create a user prefixed with **iam_group\_** on GaussDB(DWS) because such a user may be deleted by mistake.

Creating a User Synchronization Task
------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane on the DataArts Security console, choose **User Synchronization**.

#. On the **Synchronization Tasks** page, click **Create** to create a user synchronization task.


   .. figure:: /_static/images/en-us_image_0000002234237176.png
      :alt: **Figure 1** Creating a user synchronization task

      **Figure 1** Creating a user synchronization task

#. For details about how to set parameters for creating a user synchronization task, see :ref:`Table 1 <dataartsstudio_01_1154__en-us_topic_0000001630232364_table1369613101252>`. After setting the parameters, click **OK** to create a user synchronization task.


   .. figure:: /_static/images/en-us_image_0000002234237168.png
      :alt: **Figure 2** Creating a user synchronization task

      **Figure 2** Creating a user synchronization task

   .. _dataartsstudio_01_1154__en-us_topic_0000001630232364_table1369613101252:

   .. table:: **Table 1** Parameters for creating a user synchronization task

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================+
      | \*Select Cluster                  | Select a GaussDB(DWS) or MRS cluster that is connected through a GaussDB(DWS) or MRS data connection.                                                                                                        |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Cluster Type                    | You do not need to set this parameter. A matched cluster type is automatically selected.                                                                                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Connection                 | You do not need to set this parameter. The data source cluster is automatically selected.                                                                                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Scheduling Time                 | Select the time period for scheduling, with the start time included and end time excluded.                                                                                                                   |
      |                                   |                                                                                                                                                                                                              |
      |                                   | For example, if the scheduling time is set to **00-05**, the task runs from 00:00 to 05:00 every day. Scheduling is triggered at 00:00 but not at 05:00.                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Scheduling Period               | The task can be scheduled by hour or minute.                                                                                                                                                                 |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Schedule Interval               | Select a proper scheduling interval based on the selected scheduling period. The scheduling interval is the interval from the last running time. Manual synchronization is also counted in the running time. |
      |                                   |                                                                                                                                                                                                              |
      |                                   | For example, if a task starts at 20:00 and manually executed at 20:03, and the interval is five minutes, the task is scheduled again at 20:08.                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Full Synchronization              | If an MRS cluster is selected, you can set whether to synchronize all users. By default, this function is enabled.                                                                                           |
      |                                   |                                                                                                                                                                                                              |
      |                                   | You can disable it if you do not need to synchronize all users.                                                                                                                                              |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*User/User Group                 | If **Full Synchronization** is disabled, you can specify the users or user groups to be synchronized. Select at least one user or user group.                                                                |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After the user synchronization task is created, it does not run directly. You need to manually synchronize or schedule the task. The task takes effect after it is successfully synchronized. For details, see :ref:`Synchronizing or Scheduling Tasks <dataartsstudio_01_1154__en-us_topic_0000001630232364_section1419383714393>`.

.. _dataartsstudio_01_1154__en-us_topic_0000001630232364_section1419383714393:

Related Operations
------------------

-  Synchronizing or scheduling tasks: On the user synchronization task page, click **Synchronize** or choose **More** > **Start Schedule** in the **Operation** column of the corresponding task. If a task has not been executed before and is scheduled for the first time, the task is triggered immediately.

   .. note::

      If a task fails to be executed, perform the following operations:

      -  If the error message indicates insufficient permissions, see :ref:`Authorizing dlg_agency <dataartsstudio_01_1152>`.
      -  If the error message indicates that the GaussDB(DWS) IAM credential fails to be downloaded, check whether the current user has at least the GaussDB(DWS) database access permission.
      -  If error message "Mrs sync failed, please check the failure cause on the MRS page" is displayed for the MRS task, log in to the MRS console and choose **Operation Logs** in the navigation pane to view the cause.
      -  If the MRS operation logs do not contain error information, the synchronization failure cause is that the IAM username conflicts with the name of an existing MRS human-machine user. Log in to MRS Manager and delete the human-machine user with the same name as the IAM user. The default description of the IAM username for the synchronization is **IAM Custom Policy User**, and the IAM user cannot be deleted. A common MRS human-machine user can be deleted.
      -  Handle other errors based on the error messages and logs.

-  Viewing task logs: On the user synchronization task page, locate the task whose logs need to be viewed and click **Details** in the **Operation** column to view the run logs. A maximum of 20 logs are displayed.

   If a task fails to be executed, you can locate the failure cause based on logs, rectify the fault, and try to execute the task again. If the fault persists, contact technical support for assistance.

-  Editing a task: On the user synchronization task page, click **More** in the **Operation** column and select **Edit** to edit the user synchronization task.

-  Deleting a task: On the user synchronization task page, click **More** in the **Operation** column and select **Delete** to delete the user synchronization task. To delete multiple tasks at a time, select the tasks and click **Delete** above the task list.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.
