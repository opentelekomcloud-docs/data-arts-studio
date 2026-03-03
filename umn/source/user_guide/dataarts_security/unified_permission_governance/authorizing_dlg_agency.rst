:original_name: dataartsstudio_01_1152.html

.. _dataartsstudio_01_1152:

Authorizing dlg_agency
======================

Cloud service agencies allow DataArts Studio to perform operations such as task scheduling and resource O&M on cloud services on your behalf. When you log in to the DataArts Studio console homepage for the first time, a dialog box is displayed, prompting you to authorize other cloud services to access DataArts Studio. After the authorization is complete, DataArts Studio automatically creates an agency named **dlg_agency**. If you do not agree to the authorization, the dialog box will be displayed again when you access the console homepage next time.

When using an agency, DataArts Security requires higher cloud service permissions. Before using DataArts Security, you need to grant the permissions listed in :ref:`Table 1 <dataartsstudio_01_1152__en-us_topic_0000001713189413_table1082226173214>` to **dlg_agency**.

.. _dataartsstudio_01_1152__en-us_topic_0000001713189413_table1082226173214:

.. table:: **Table 1** Required permissions

   +---------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Permission                                        | Purpose                                                                                                                                                                    | Mandatory                                                      | Authorization Item/System Permission (Configure Either of Them)                                                                                                                                                             |                                                    |
   +===================================================+============================================================================================================================================================================+================================================================+=============================================================================================================================================================================================================================+====================================================+
   | IAM permission                                    | This permission is required for the system to obtain users or user groups, or create roles.                                                                                | Mandatory for MRS, GaussDB(DWS), and DLI permission management | -  iam:users:listUsers                                                                                                                                                                                                      | Security Administrator                             |
   |                                                   |                                                                                                                                                                            |                                                                | -  iam:groups:listGroups                                                                                                                                                                                                    |                                                    |
   |                                                   | For example, user or permission synchronization fails if this permission is missing.                                                                                       |                                                                | -  iam:users:listUsersForGroup                                                                                                                                                                                              |                                                    |
   |                                                   |                                                                                                                                                                            |                                                                | -  iam:roles:createRole                                                                                                                                                                                                     |                                                    |
   |                                                   |                                                                                                                                                                            |                                                                | -  iam:roles:deleteRole                                                                                                                                                                                                     |                                                    |
   |                                                   |                                                                                                                                                                            |                                                                | -  iam:roles:updateRole                                                                                                                                                                                                     |                                                    |
   |                                                   |                                                                                                                                                                            |                                                                | -  iam:permissions:grantRoleToGroup                                                                                                                                                                                         |                                                    |
   |                                                   |                                                                                                                                                                            |                                                                | -  iam:permissions:listRoleAssignments                                                                                                                                                                                      |                                                    |
   |                                                   |                                                                                                                                                                            |                                                                | -  iam:permissions:revokeRoleFromGroup                                                                                                                                                                                      |                                                    |
   |                                                   |                                                                                                                                                                            |                                                                |                                                                                                                                                                                                                             |                                                    |
   |                                                   |                                                                                                                                                                            |                                                                | .. note::                                                                                                                                                                                                                   |                                                    |
   |                                                   |                                                                                                                                                                            |                                                                |                                                                                                                                                                                                                             |                                                    |
   |                                                   |                                                                                                                                                                            |                                                                |    Due to the restrictions of permission policies in IAM, no action is available for obtaining DLI user groups. To manage the permissions of DLI user groups, you must grant the Security Administrator system permissions. |                                                    |
   +---------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | MRS/GaussDB(DWS) data connection agent permission | This permission is required for permission synchronization.                                                                                                                | Mandatory for MRS and GaussDB(DWS) permission management       | Any CDM permission, for example, cdm:cluster:get                                                                                                                                                                            | Any CDM permission, for example, CDM Administrator |
   |                                                   |                                                                                                                                                                            |                                                                |                                                                                                                                                                                                                             |                                                    |
   |                                                   | For example, if this permission is missing, permission synchronization between permission sets, role permission synchronization, or permission application approval fails. |                                                                |                                                                                                                                                                                                                             |                                                    |
   +---------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | MRS user synchronization permission               | This permission is required for MRS user synchronization.                                                                                                                  | Mandatory for MRS permission management                        | -  mrs:cluster:syncUser                                                                                                                                                                                                     | MRS FullAccess                                     |
   |                                                   |                                                                                                                                                                            |                                                                |                                                                                                                                                                                                                             |                                                    |
   |                                                   | For example, MRS user synchronization fails if this permission is missing.                                                                                                 |                                                                |                                                                                                                                                                                                                             |                                                    |
   +---------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | GaussDB(DWS) user synchronization permission      | This permission is required for GaussDB(DWS) user synchronization.                                                                                                         | Mandatory for GaussDB(DWS) permission management               | -  dws:dbAuthority:syncIamUser                                                                                                                                                                                              | DWS FullAccess                                     |
   |                                                   |                                                                                                                                                                            |                                                                | -  dws:dbAuthority:updateUser                                                                                                                                                                                               |                                                    |
   |                                                   | For example, GaussDB(DWS) user synchronization fails if this permission is missing.                                                                                        |                                                                |                                                                                                                                                                                                                             |                                                    |
   +---------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | DLI permission synchronization permission         | This permission is required for DLI permission synchronization and sensitive data discovery.                                                                               | Mandatory for DLI permission management                        | Actions are not supported. System permissions DLI FullAccess and DLI Service Administrator are required.                                                                                                                    | DLI FullAccess                                     |
   |                                                   |                                                                                                                                                                            |                                                                |                                                                                                                                                                                                                             |                                                    |
   |                                                   | For example, if this permission is missing, DLI permission synchronization fails and the system displays a message indicating insufficient permissions.                    |                                                                |                                                                                                                                                                                                                             | DLI Service Administrator                          |
   +---------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+

Prerequisites
-------------

In the dialog box displayed on the DataArts Studio console homepage, you have selected **Agree** to allow the system to automatically create an agency named **dlg_agency**.

Constraints
-----------

After the agency authorization is successful, it takes 15 to 30 minutes for the permissions to take effect. Then, you can use DataArts Security to manage access permissions.

Granting Permissions to dlg_agency
----------------------------------

When granting permissions to **dlg_agency**, you need to select either an authorization item or system permission from :ref:`Table 1 <dataartsstudio_01_1152__en-us_topic_0000001713189413_table1082226173214>` as needed.

This section uses the MRS permission management scenario as an example. The permissions to be granted include the IAM permission, MRS/GaussDB(DWS) data connection agent permission, and MRS user synchronization permission. The principle of least privilege is used. The operations are as follows:

#. Log in to the IAM console.

#. In the left navigation pane, choose **Permissions** > **Policies/Roles** and click **Create Custom Policy**.


   .. figure:: /_static/images/en-us_image_0000002234080212.png
      :alt: **Figure 1** Clicking Create Custom Policy

      **Figure 1** Clicking Create Custom Policy

#. On the displayed **Create Custom Policy** page, select **JSON** for **Policy View**, enter the IAM custom policy content required for MRS permission management, and click **OK**.

   .. note::

      A custom policy can contain permissions for either global or project-level services. You need to configure IAM policies first, and then MRS and CDM policies.

   -  **Policy Name**: Enter **DataArtsIamUserGroup_IAM**.

   -  **Policy View**: Select **JSON** to switch to the JSON view.

   -  **Policy Content**: Enter the following JSON code and click **OK**.

      .. code-block::

         {
             "Version": "1.1",
             "Statement": [
                 {
                     "Effect": "Allow",
                     "Action": [
                         "iam:users:listUsers",
                         "iam:groups:listGroups",
                         "iam:users:listUsersForGroup",
                         "iam:roles:createRole",
                         "iam:roles:deleteRole",
                         "iam:roles:updateRole",
                         "iam:permissions:grantRoleToGroup",
                         "iam:permissions:listRoleAssignments",
                         "iam:permissions:revokeRoleFromGroup"
                     ]
                 }
             ]
         }


      .. figure:: /_static/images/en-us_image_0000002269199465.png
         :alt: **Figure 2** Creating a custom policy for IAM

         **Figure 2** Creating a custom policy for IAM

#. Click **Create Custom Policy** again. On the displayed **Create Custom Policy** page, select **JSON** for **Policy View**, enter the MRS and CDM custom policy content required for MRS permission management, and click **OK**.

   .. note::

      A custom policy can contain permissions for either global or project-level services. You need to configure IAM policies first, and then MRS and CDM policies.

   -  **Policy Name**: Enter **DataArtsIamUserGroup_MRS**.

   -  **Policy View**: Select **JSON** to switch to the JSON view.

   -  **Policy Content**: Enter the following JSON code.

      .. code-block::

         {
             "Version": "1.1",
             "Statement": [
                 {
                     "Effect": "Allow",
                     "Action": [
                         "mrs:cluster:syncUser",
                         "cdm:cluster:get"
                     ]
                 }
             ]
         }


      .. figure:: /_static/images/en-us_image_0000002234080220.png
         :alt: **Figure 3** Creating custom policies for MRS and CDM

         **Figure 3** Creating custom policies for MRS and CDM

#. In the left navigation pane, choose **Agencies**, search for **dlg_agency**, and click **Authorize**.


   .. figure:: /_static/images/en-us_image_0000002269119381.png
      :alt: **Figure 4** Authorizing dlg_agency

      **Figure 4** Authorizing dlg_agency

#. In the displayed dialog box, locate and select the created custom policies **DataArtsIamUserGroup_IAM** and **DataArtsIamUserGroup_MRS**, and click **Next**.


   .. figure:: /_static/images/en-us_image_0000002234080188.png
      :alt: **Figure 5** Selecting the created custom policies

      **Figure 5** Selecting the created custom policies

#. Click **OK**. After the authorization is complete, wait for 15 to 30 minutes. Then, you can use DataArts Security to manage MRS access permissions.
