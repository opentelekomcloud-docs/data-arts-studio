:original_name: dataartsstudio_01_1159.html

.. _dataartsstudio_01_1159:

Applying for Permissions and Approving Permissions
==================================================

During access permission management, you can grant permissions to users through permission sets or roles, or apply for permissions and approve permission applications.

This section describes how to :ref:`configure a review policy <dataartsstudio_01_1159__section1415314106586>`, how an applicant applies for permissions (:ref:`Applying for Permissions <dataartsstudio_01_1159__en-us_topic_0000001662914226_section61151754163611>`), and how a reviewer reviews permission requests (:ref:`Reviewing Permission Requests <dataartsstudio_01_1159__en-us_topic_0000001662914226_section1961485294915>`) and revokes permissions (:ref:`Revoking Permissions <dataartsstudio_01_1159__section5995174315371>`).

Prerequisites
-------------

-  Before applying for permissions, you have configured a workspace permission set. For details, see :ref:`Configuring Workspace Permission Sets <dataartsstudio_01_1155>`.
-  Before applying for permissions, you have collected the metadata of the data connection in DataArts Catalog. For details, see :ref:`Metadata Collection Task <dataartsstudio_01_0804>`.

Notes and Constraints
---------------------

-  For configuring review policies:

   -  Only one review policy is allowed for a security level. If no security level is selected, only one review policy is allowed.
   -  To create a security level-based review policy, ensure that the following conditions are met:

      -  Data Map is enabled.
      -  Metadata has been collected from the data of a specific security level.
      -  A sensitive data discovery task has been executed, and the security level information has been synchronized to Data Map.

-  For applying for permissions and reviewing permission requests:

   -  You can only apply for the SELECT permission for querying data in tables. Before applying for the permission, ensure that the SELECT permission for all columns in the target table has been configured in the workspace permission set.
   -  If you apply for the permission of multiple tables at a time, multiple requests are generated.
   -  You can apply for DLI permissions for users but not for user groups.
   -  Only the DARTS Administrator, Tenant Administrator, data security administrator, and workspace administrator can revoke permissions from other users.
   -  You can only view your permission requests and review records, and cannot audit permissions.

-  For making permissions take effect:

   -  During permission synchronization, you need to configure required permissions for the **dlg_agency**. For details, see :ref:`Authorizing dlg_agency <dataartsstudio_01_1152>`.
   -  The current data permission control uses the allowlist mechanism, which adds operation conditions to the users to be authorized without affecting the permissions the users already have. If you only want to make the permissions granted by the data permission control take effect, you need to revoke the original permissions of the users to be authorized. For details, see :ref:`Data Permission Management <dataartsstudio_01_1151__en-us_topic_0000001678748550_section47668147310>`.
   -  During script execution and job testing in DataArts Factory, the MRS or GaussDB(DWS) data source uses the account of the data connection for authentication by default. Therefore, permission management still does not take effect during data development. You need to enable fine-grained authentication so that the current user is used for authentication during script execution and job testing in DataArts Factory. In this way, different users have different data permissions, and permission management for roles and permission sets takes effect.

.. _dataartsstudio_01_1159__section1415314106586:

Configuring a Review Policy
---------------------------

Through review policies, you can set multi-level review processes or set different review processes for data of different security levels.

Note that review policies configured for a DataArts Studio instance are visible to and take effect for all the workspaces of the instance.

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Permission Review**.

#. On the displayed page, click the **Review Policies** tab and then **Create**.


   .. figure:: /_static/images/en-us_image_0000002269117233.png
      :alt: **Figure 1** Creating a review policy

      **Figure 1** Creating a review policy

#. In the slide-out panel, set parameters based on :ref:`Table 1 <dataartsstudio_01_1159__table14914181311586>`. You can click |image1| to add review nodes.


   .. figure:: /_static/images/en-us_image_0000002234237840.png
      :alt: **Figure 2** Configuring the review policy

      **Figure 2** Configuring the review policy

   .. _dataartsstudio_01_1159__table14914181311586:

   .. table:: **Table 1** Review policy parameters

      +--------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Configuration Item                                           | Description                                                                                                                                                                                                                                                                 |
      +==============================================================+=============================================================================================================================================================================================================================================================================+
      | **Basic Information**                                        |                                                                                                                                                                                                                                                                             |
      +--------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Policy Name                                                | Name of the review policy. It can contain a maximum of 32 characters, including letters, digits, and underscores (_).                                                                                                                                                       |
      +--------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Description                                           | Description of the policy. It can contain a maximum of 255 characters.                                                                                                                                                                                                      |
      +--------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Security Level                                          | If you want to set different review processes for the permission requests for data of different security levels, select a data security level. Only one review policy is allowed for a security level. If no security level is selected, only one review policy is allowed. |
      |                                                              |                                                                                                                                                                                                                                                                             |
      |                                                              | The prerequisites for selecting a data security level are as follows:                                                                                                                                                                                                       |
      |                                                              |                                                                                                                                                                                                                                                                             |
      |                                                              | -  Data Map is enabled.                                                                                                                                                                                                                                                     |
      |                                                              | -  Metadata has been collected from the data of a specific security level.                                                                                                                                                                                                  |
      |                                                              | -  A sensitive data discovery task has been executed, and the security level information has been synchronized to Data Map.                                                                                                                                                 |
      +--------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Review Node Settings-System Role/IAM User/IAM User Group** |                                                                                                                                                                                                                                                                             |
      +--------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Reviewer Type                                                | Type of the reviewer                                                                                                                                                                                                                                                        |
      +--------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Role                                                         | Reviewer role matching the reviewer type                                                                                                                                                                                                                                    |
      +--------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After setting the review policy, click **Submit**. The created review policy is disabled by default. To make it take effect, click |image2| in the **Status** column.


   .. figure:: /_static/images/en-us_image_0000002234237868.png
      :alt: **Figure 3** Review policy list

      **Figure 3** Review policy list

.. _dataartsstudio_01_1159__en-us_topic_0000001662914226_section61151754163611:

Applying for Permissions
------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Permission Review**.

#. On the **Data permission request** page, click **Create** to create a service ticket for applying for permissions.


   .. figure:: /_static/images/en-us_image_0000002234078080.png
      :alt: **Figure 4** Creating a permission request

      **Figure 4** Creating a permission request

#. On the displayed **Data permission request** page, fill in the service ticket by referring to :ref:`Table 2 <dataartsstudio_01_1159__en-us_topic_0000001662914226_table19786314182513>`.


   .. figure:: /_static/images/en-us_image_0000002516640626.png
      :alt: **Figure 5** Filling in the service ticket

      **Figure 5** Filling in the service ticket

   .. _dataartsstudio_01_1159__en-us_topic_0000001662914226_table19786314182513:

   .. table:: **Table 2** Parameters for the permission request

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Item                              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | **Basic information**             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Workspace                       | Select a workspace for which a workspace permission set has been configured.                                                                                                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Workspace Permission Sets       | Select a workspace permission set that contains the required resource permissions.                                                                                                                                                                                                                                                                                                                                                                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Source                     | Select **MRS Hive**, **DLI**, or **DWS**.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Cluster Name                    | Select the cluster of the requested resource permissions.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Connection                 | Select the data connection of the requested resource permissions.                                                                                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Resource selection**            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Available Resources             | After selecting a database in the navigation tree, select the required data tables. You can select tables in different databases.                                                                                                                                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   |    -  You can only apply for the SELECT permission for querying data in tables. Before applying for the permission, ensure that the SELECT permission for all columns in the selected table has been configured in the workspace permission set.                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   | If **Fast mode** is enabled, metadata of databases, tables, and columns is obtained from DataArts Catalog. Otherwise, metadata is obtained from the data source. You are advised to enable **Fast mode**.                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Selected Resources              | In the list of selected resources, you can view the selected tables, permissions, and reviewers.                                                                                                                                                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   |    The reviewers are the administrators of permission sets or roles by default. For example, if the SELECT permission for all columns in the selected table is defined in the workspace permission set, permission set A, and role B, the reviewer can be the administrator of permission set A or role B. If the SELECT permission for all columns in the selected table is only defined in the workspace permission set, the reviewer is the administrator of the workspace permission set. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Request information**           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | For myself                        | If you select this option, you can apply for the selected resource permissions for yourself.                                                                                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Workspace Account                 | If a public IAM account for scheduling has been configured in DataArts Factory, you can apply for the selected resource permissions for the workspace account.                                                                                                                                                                                                                                                                                                                                |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | For others                        | Select members in the workspace and apply for the selected resource permissions for them.                                                                                                                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Request Reason                  | Enter the reason for applying for the permissions so that the reviewer can determine whether to approve your request.                                                                                                                                                                                                                                                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After filling in the service ticket, click **Submit** to generate a service ticket to be reviewed. In the service ticket list, you can view the service ticket ID, summary, and status. You can click the service ticket ID to view the ticket details. You can also withdraw service tickets that have not been approved.


   .. figure:: /_static/images/en-us_image_0000002548285041.png
      :alt: **Figure 6** Service ticket list

      **Figure 6** Service ticket list

.. _dataartsstudio_01_1159__en-us_topic_0000001662914226_section1961485294915:

Reviewing Permission Requests
-----------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Permission Review**.

#. Click the **Permission Review** tab.


   .. figure:: /_static/images/en-us_image_0000002269197301.png
      :alt: **Figure 7** Permission Review

      **Figure 7** Permission Review

#. The **Permission Review** page displays the service tickets to be reviewed. You can view the service ticket ID, summary, and status, and click the service ticket ID to view the ticket details. Review the service ticket based on service rationality and data security, and click **Approve** or **Reject**. You can also select service tickets and click **Batch Review** above the list to approve or reject service tickets in batches.

#. Click the **Reviewed** tab to view the service tickets that have been approved.


   .. figure:: /_static/images/en-us_image_0000002269197349.png
      :alt: **Figure 8** List of approved service tickets

      **Figure 8** List of approved service tickets

.. _dataartsstudio_01_1159__section5995174315371:

Revoking Permissions
--------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Permission Review**.

#. Click the **Revoking permissions** tab.


   .. figure:: /_static/images/en-us_image_0000002269197293.png
      :alt: **Figure 9** Revoking permissions tab

      **Figure 9** Revoking permissions tab

#. The **Revoking permissions** page displays the data permissions you have obtained. You can filter permissions by **Workspace**, **Member Name**, **Database Name**, or **Table Name** (fuzzy match is supported). Locate a permission and click **Reclaim** in the **Operation** column to delete the permission.

   Only the DARTS Administrator, Tenant Administrator, workspace administrator, and data security administrator can revoke data permissions of users in the corresponding workspace.


   .. figure:: /_static/images/en-us_image_0000002269117285.png
      :alt: **Figure 10** Revoking permissions

      **Figure 10** Revoking permissions

Related Operations
------------------

-  Editing a review policy: On the **Review Policies** page, locate a policy and click **Edit** in the **Operation** column.

-  Setting the review policy status: A new review policy is disabled by default and does not take effect.

   To change the status of a review policy, click |image3| or |image4| to enable or disable the policy.

-  Deleting review policies: On the **Review Policies** page, locate a policy and click **Delete** in the **Operation** column. To delete multiple policies, select them and click **Delete** above the policy list.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000002234237848.png
.. |image2| image:: /_static/images/en-us_image_0000002234237856.png
.. |image3| image:: /_static/images/en-us_image_0000002269197289.png
.. |image4| image:: /_static/images/en-us_image_0000002234078088.png
