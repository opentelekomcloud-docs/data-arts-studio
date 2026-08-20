:original_name: dataartsstudio_01_1151.html

.. _dataartsstudio_01_1151:

Permission Governance Process
=============================

Unified permission governance allows you to configure access permissions for the databases, tables, and fields in MRS, DLI, and GaussDB(DWS). It has the following features:

-  Centralized access control

   Permissions of different big data services, such as MRS, DLI, and GaussDB(DWS), are centrally managed. A unified portal is available for you to configure and maintain permissions easily.

-  Multi-level permission configuration model

   Permission models are clearly defined and managed by level. A permission set or role further splits the permission scope defined by the workspace permission set and associates users with permissions for permission control.

-  Refined permission management

   Role-based access control (RBAC) on the console supports refined data permission configuration and permission assignment by role, user, and user group. In addition, on-demand and efficient permission application approval is supported. Approved permissions take effect immediately.

-  Multi-dimensional permission display

   -  By workspace member: You can display the data table permissions requested by each user or user group and display, configure, and revoke the permission set relationship of each user or user group.
   -  By data: You can display and configure the permission relationships of data in the current permission set by database, table, or field.
   -  By permission: You can display, configure, and revoke the permission policy relationships of data in the current permission set by permission policy.

-  Workspace resource management

   In addition to data permissions, workspace resources, such as data connections and agencies, can be managed.

Use Process
-----------

:ref:`Figure 1 <dataartsstudio_01_1151__en-us_topic_0000001678748550_fig204102392282>` shows the process for using unified permission governance.

.. _dataartsstudio_01_1151__en-us_topic_0000001678748550_fig204102392282:

.. figure:: /_static/images/en-us_image_0000002234238520.png
   :alt: **Figure 1** Process of using unified permission governance

   **Figure 1** Process of using unified permission governance

Unified permission governance supports :ref:`data permission management <dataartsstudio_01_1151__en-us_topic_0000001678748550_li1398820379355>`, :ref:`service resource management <dataartsstudio_01_1151__li61811313153914>`, and :ref:`Ranger permission management <dataartsstudio_01_1151__li193578247573>`. Their processes are as follows:

**Data permission management process**

#. .. _dataartsstudio_01_1151__en-us_topic_0000001678748550_li1398820379355:

   :ref:`Authorize dlg_agency. <dataartsstudio_01_1152>`

   When using an agency, DataArts Security requires higher cloud service permissions. Before using DataArts Security, you need to grant required permissions to dlg_agency.

#. :ref:`Check the cluster version and permissions. <dataartsstudio_01_1153>`

   Unified permission governance has requirements on the data connection agent, data source version, and user permissions. Before using it, you need to check and prepare related configurations.

#. :ref:`Synchronize IAM users to the data source. <dataartsstudio_01_1154>`

   Synchronize user information from IAM to data sources so that users' access to the data sources can be managed based on user information.

#. :ref:`Configure workspace permission sets. <dataartsstudio_01_1155>`

   As the largest permission set in a DataArts Studio workspace, the workspace permission set defines the resources that can be accessed by users in the workspace.

#. :ref:`Configure permission sets. <dataartsstudio_01_1156>`

   A permission set associates users with permissions. You can create multiple permission sets to associate users in different scenarios with different permissions. Permissions can be managed through permission synchronization (association of permission sets with roles are more recommended in actual applications.)

#. :ref:`Configure common roles. <dataartsstudio_01_1157>`

   Create roles in the data source to associate users and permissions. In this way, you can manage permissions more intuitively.

#. :ref:`Configure managed roles. <dataartsstudio_01_1157>`

   Manage the existing roles in the MRS data source and inherit the MRS data source permissions of the existing roles.

#. :ref:`Configure row-level access control. <dataartsstudio_01_1163>`

   DataArts Security allows you to view the permissions of workspace members, and manage roles and permission sets.

#. :ref:`Synchronize MRS Hive and Hetu permissions. <dataartsstudio_01_1164>`

   DataArts Security allows you to view the permissions of workspace members, and manage roles and permission sets.

#. :ref:`Apply for permissions. <dataartsstudio_01_1159>`

   During access permission management, you can grant permissions to users through permission sets or roles, or apply for permissions and approve permission applications.

#. :ref:`Review permission requests. <dataartsstudio_01_1159>`

   The approver is the administrator of the permission set or role. The requested permission takes effect immediately after being approved.

#. :ref:`Enable fine-grained authentication. <dataartsstudio_01_1160>`

   After fine-grained authentication is enabled, data sources no longer use the accounts of the data connections during script execution, job tests, and job scheduling in DataArts Factory of DataArts Studio. Instead, the current user is used for authentication. In this way, different users have different data permissions, and the permissions of roles, permission sets, and queues can be managed.

**Service resource management process**

#. .. _dataartsstudio_01_1151__li61811313153914:

   :ref:`Configure queue permissions. <dataartsstudio_01_1162>`

   Queue permissions can be used to allocate MRS Yarn and DLI queues to the current workspace and configure queue permission policies for user groups or users.

   -  After queues are allocated to the workspace, they can be selected during the job node configuration in DataArts Factory.
   -  After queue permission policies are configured for user groups or users, they have the permissions specified in the policies.

#. :ref:`Configure workspace resource permission policies. <dataartsstudio_01_1161>`

   DataArts Security supports management of workspace resources, such as data connections and agencies. Unauthorized users cannot view or use the resources.

**Ranger permission management process**

#. .. _dataartsstudio_01_1151__li193578247573:

   :ref:`Configure resource permissions. <dataartsstudio_01_1006>`

   You can create permission policies for MRS components and use the Ranger component to manage permissions.

#. :ref:`View permission reports. <dataartsstudio_01_1007>`

   You can view resource permission policies and their details through a comprehensive permission report.

.. _dataartsstudio_01_1151__en-us_topic_0000001678748550_section47668147310:

Data Permission Management
--------------------------

The current data permission control uses the allowlist mechanism, which adds operation conditions to the users to be authorized without affecting the permissions the users already have. If you only want to make the permissions granted by the data permission control take effect, you need to revoke the original permissions of the users to be authorized. By default, DataArts Studio users have the following permissions:

-  For DLI data sources, the DARTS Administrator or DARTS User has the DLI Service Admin permission by default. Therefore, the users to be authorized have all the data permissions of DLI database tables by default. To remove the default permissions of an authorized user, you need to delete the DLI Service Admin permission of the user.
-  For GaussDB(DWS) data sources, even if the DARTS Administrator or DARTS User has the GaussDB(DWS) Administrator permission by default, the GaussDB(DWS) database permissions are isolated from the IAM permissions on the console. Therefore, the users to be authorized do not have the data permissions of GaussDB(DWS) database tables by default. Only the data permission granted by the current data permission control takes effect.
-  For MRS data sources, DARTS Administrator or DARTS User has the MRS Administrator permission by default and will be assigned the corresponding role after it is synchronized to MRS. For details, see "Synchronizing IAM Users to MRS" in *MapReduce Service (MRS) User Guide*. The Ranger component provides the default policy bypass permissions. For details, see "Using Ranger (MRS 3.x)" > "Adding a Ranger Permission Policy" in *MapReduce Service (MRS) User Guide*. If you want to revoke the default permissions of the users to be authorized, perform the following operations to remove the **public** user group from the default system policies on the Ranger component:

   #. Log in to MRS Manager as user **admin**.

   #. On the Manager page, choose **Cluster** > **Services** > **Ranger**. On the Ranger overview page, click **RangerAdmin** to go to the Ranger WebUI.


      .. figure:: /_static/images/en-us_image_0000002234238528.png
         :alt: **Figure 2** Accessing the Ranger WebUI

         **Figure 2** Accessing the Ranger WebUI

   #. Log out of the current account and use the Ranger administrator account to log in again. For a common cluster, the admin account for the Manager page can be used as the Ranger administrator account. For a security cluster, **rangeradmin** is the Ranger administrator account. For details about the default password of **rangeradmin**, see "FusionInsight Manager Operation Guide" > "Security Management" > "Security Overview" > "User Account List" in *MapReduce Service (MRS) x.x.x* *User* *Guide*.


      .. figure:: /_static/images/en-us_image_0000002269197945.png
         :alt: **Figure 3** Logging out of the current account

         **Figure 3** Logging out of the current account

   #. On the home page, click the component plug-in name in the **HADOOP SQL** area, for example, **Hive**.

   #. On the **Access** tab page, locate the default policies whose **Groups** column contains **public** (that is, the policy whose value in the **Default Policy** column is **True**) and remove the **public** user group from the policies.


      .. figure:: /_static/images/en-us_image_0000002548269001.png
         :alt: **Figure 4** Policy list

         **Figure 4** Policy list
