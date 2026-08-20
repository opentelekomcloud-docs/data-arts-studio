:original_name: dataartsstudio_03_0068.html

.. _dataartsstudio_03_0068:

Why Does the System Display a Message Indicating Insufficient Permissions During Permission Synchronization to DLI?
===================================================================================================================

The tasks of synchronizing permissions to DLI are completed through the cloud service agency (**dlg_agency**). The agency must have the permissions listed in :ref:`Table 1 <dataartsstudio_03_0068__table698195114202>`.

.. _dataartsstudio_03_0068__table698195114202:

.. table:: **Table 1** Required permissions

   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------+-----------------------------------------------------------------+------------------------+
   | Permission                                      | Purpose                                                                                                                                                 | Mandatory                               | Authorization Item/System Permission (Configure Either of Them) |                        |
   +=================================================+=========================================================================================================================================================+=========================================+=================================================================+========================+
   | IAM permission                                  | This permission is required for the system to obtain users or user groups, or create roles.                                                             | Yes                                     | -  iam:users:listUsers                                          | Security Administrator |
   |                                                 |                                                                                                                                                         |                                         | -  iam:groups:listGroups                                        |                        |
   |                                                 | For example, user synchronization fails if this permission is missing.                                                                                  |                                         | -  iam:users:listUsersForGroup                                  |                        |
   |                                                 |                                                                                                                                                         |                                         | -  iam:roles:createRole                                         |                        |
   |                                                 |                                                                                                                                                         |                                         | -  iam:roles:deleteRole                                         |                        |
   |                                                 |                                                                                                                                                         |                                         | -  iam:roles:updateRole                                         |                        |
   |                                                 |                                                                                                                                                         |                                         | -  iam:permissions:grantRoleToGroup                             |                        |
   |                                                 |                                                                                                                                                         |                                         | -  iam:permissions:listRoleAssignments                          |                        |
   |                                                 |                                                                                                                                                         |                                         | -  iam:permissions:revokeRoleFromGroup                          |                        |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------+-----------------------------------------------------------------+------------------------+
   | Permission for synchronizing permissions to DLI | This permission is required for DLI permission synchronization.                                                                                         | Mandatory for DLI permission management | -  dli:database:grantPrivilege                                  | DLI FullAccess         |
   |                                                 |                                                                                                                                                         |                                         | -  dli:table:grantPrivilege                                     |                        |
   |                                                 | For example, if this permission is missing, DLI permission synchronization fails and the system displays a message indicating insufficient permissions. |                                         | -  dli:column:grantPrivilege                                    |                        |
   |                                                 |                                                                                                                                                         |                                         | -  dli:queue:grantPrivilege                                     |                        |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------+-----------------------------------------------------------------+------------------------+

If this message is displayed, perform the following operations to grant permissions (system permissions in this example) to **dlg_agency**:

#. Log in to the IAM console.

#. In the navigation pane, choose **Agencies**.

#. Search for **dlg_agency** and click **Authorize** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002234076360.png
      :alt: **Figure 1** Granting permissions to dlg_agency

      **Figure 1** Granting permissions to dlg_agency

#. On the displayed page, search for and select **Security Administrator** and **DLI FullAccess**, and click **Next**.


   .. figure:: /_static/images/en-us_image_0000002234236208.png
      :alt: **Figure 2** Selecting Security Administrator

      **Figure 2** Selecting Security Administrator

#. Click **OK**. Wait for 15 to 30 minutes. The permissions will be synchronized to DLI.
