:original_name: dataartsstudio_01_1162.html

.. _dataartsstudio_01_1162:

Configuring Queue Permissions
=============================

This section describes how to allocate MRS Yarn and DLI queues to the current workspace and configure queue permission policies for user groups or users through queue permission management.

Currently, the whitelist mechanism is used for queue allocation and queue permission management. If no queue is allocated, no queue can be selected. If queue permissions are not granted to a user, the user cannot use the queue.

-  After queues are allocated to the workspace, they can be selected during the job node configuration in DataArts Factory.

   .. note::

      Currently, the queue list can be obtained from allocated queues when the MRS Yarn queue is selected. If no queue is allocated, only the root.default queue can be selected.

-  After queue permissions are configured for user groups or users, MRS Ranger manages the permissions of MRS queues and DLI manages the permissions of DLI queues. Only authorized users can access the queues.

   .. note::

      When you use queues in DataArts Factory, the data source uses the account of the data connection for authentication. Therefore, queue permission management still does not take effect during data development. You need to enable fine-grained authentication so that the current user is used for authentication during the use of queues in DataArts Factory. In this way, queue permission management takes effect.

Prerequisites
-------------

-  Only the DARTS Administrator, Tenant Administrator, or data security administrator has the permission to allocate available queues to the current workspace, configure MRS queue attributes (offline/real-time), and configure user permission policies for specified queues. The workspace administrator can configure queue permission policies for user groups and users.
-  Before configuring queue permissions, you have created an MRS Ranger and a DLI connection in Management Center. For details, see :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.
-  Before configuring permissions for MRS Yarn queues, you have synchronized user information from IAM to the data source based on :ref:`Synchronizing IAM Users to the Data Source <dataartsstudio_01_1154>`.
-  To make the permission policy for MRS Yarn queues take effect, you have enabled Yarn access control by setting the **yarn.acl.enable** parameter to **true**. For details, see :ref:`Reference: Configuring Strict Permission Control for Yarn <dataartsstudio_01_1162__section123461282269>`.

Constraints
-----------

-  Currently, only MRS Yarn queues can be allocated. Permission management is supported only for MRS Yarn and DLI queues. Authorization for the DLI default queue is not supported due to DLI limitations.
-  Permissions of MRS Yarn queues can be managed only when the version of the CDM cluster selected as the agent for the data connection is 2.10.0.300 or later.
-  Only the DARTS Administrator, Tenant Administrator, or data security administrator has the permission to allocate available queues to the current workspace, configure MRS queue attributes (offline/real-time), and configure user permission policies for specified queues. The workspace administrator can configure queue permission policies for user groups and users.
-  The queues allocated to the current workspace are not associated with the configured queue permissions policies which are contained in the data source configuration. Therefore, if the queues are deleted from the current workspace, the configured queue permission policies still take effect. When the queues are added again, the permissions are still available.
-  The configured queue permission policies are implemented based on the permission control capability of the data source. You can view the configured policies in the data source (such as MRS Ranger policies and DLI queue management). If you delete a queue policy from the data source, the policy will not be automatically deleted from the DataArts Security component. You need to manually delete the policy from the DataArts Security component.
-  Queue attributes (offline or real-time) can be configured only for MRS Yarn queues, and different attributes can be configured for the same queue in different workspaces.
-  Due to DLI limitations, permissions of DLI queues can be granted only to users, but not to user groups.

Allocating Queues and Granting Permissions
------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Queue Permissions**.


   .. figure:: /_static/images/en-us_image_0000002234076776.png
      :alt: **Figure 1** Queue Permissions page

      **Figure 1** Queue Permissions page

#. Click |image1| above the queue permission directory to allocate a queue to the current workspace. In the displayed **Add Queue Resource** dialog box, set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1162__en-us_topic_0000001678432349_table177118297118>` and click **Save**.

   .. _dataartsstudio_01_1162__en-us_topic_0000001678432349_table177118297118:

   .. table:: **Table 1** Parameters for adding a queue

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================================================================================================================================================================================+
      | \*Resource Type                   | Select **MRS queues** or **DLI queues**.                                                                                                                                                                                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Connection                 | Select the data connection where the queue is located. For details about how to create a data connection, see :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.                                                                                                                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Cluster Name                    | This parameter is displayed only when **Resource Type** is set to **MRS queues**. The system automatically matches the cluster name corresponding to the data connection.                                                                                                                                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Queue Name                      | Select the queue to be authorized.                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | -  If you set **Resource Type** to **MRS queues**, the available queues are from an MRS cluster. To view the available queues, go to the MRS console, click a cluster name to go to the cluster details page, and click the **Tenants** and then **Queue Configuration** tab.                                                                                                                              |
      |                                   | -  If you set **Resource Type** to **DLI queues**, the available queues are the queues purchased in DLI. To view the available queues, go to the DLI console and choose **Resources** > **Queue Management**. In addition, DLI queues are classified into SQL queues and general-purpose queues. SQL queues are used to run SQL jobs, and general-purpose queues are used to run Flink and Spark JAR jobs. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Information to make the queue easier to be identified                                                                                                                                                                                                                                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


   .. figure:: /_static/images/en-us_image_0000002269196077.png
      :alt: **Figure 2** Adding queues

      **Figure 2** Adding queues

#. Click a queue in the queue permission directory to go to the queue details page.

   You can configure attributes for MRS Yarn queues, which are mainly used for task management in DataArts Factory. Real-time queues are used to run real-time jobs, and offline queues are used to run batch jobs. By default, job types of queues are not distinguished.


   .. figure:: /_static/images/en-us_image_0000002269196069.png
      :alt: **Figure 3** MRS Yarn queue details

      **Figure 3** MRS Yarn queue details


   .. figure:: /_static/images/en-us_image_0000002269115989.png
      :alt: **Figure 4** DLI queue details

      **Figure 4** DLI queue details

#. Grant permissions to the allocated queues.

   -  **MRS Yarn queue**

      On the MRS Yarn queue details page, click **Create Policy**. In the displayed dialog box, set the parameters in :ref:`Table 2 <dataartsstudio_01_1162__table918935581611>` and click **Save**.

      .. _dataartsstudio_01_1162__table918935581611:

      .. table:: **Table 2** MRS Yarn queue policy parameters

         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                                                                         | Description                                                                                                                                                                                                                                                                                     |
         +===================================================================================+=================================================================================================================================================================================================================================================================================================+
         | Cluster Name                                                                      | The system automatically sets this parameter to the name of the cluster where the queue is located.                                                                                                                                                                                             |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Queue Name                                                                        | The system automatically sets this parameter to the current queue name.                                                                                                                                                                                                                         |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | \*Policy Name                                                                     | Name of the permission policy for the MRS Yarn queue. To facilitate policy management, you are advised to include the authorization object in the name.                                                                                                                                         |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Policy Description                                                                | Information to make the policy easier to be identified                                                                                                                                                                                                                                          |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Policy Status                                                                     | If this function is enabled, the current policy takes effect.                                                                                                                                                                                                                                   |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Audit Log                                                                         | If this function is enabled, operation logs of the current queue can be recorded. You can view the audit logs in the data source.                                                                                                                                                               |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Overwrite                                                                         | Due to the restrictions of the Ranger component, if a queue permission policy already exists for the user or user group in the Ranger component, the current policy may be considered duplicate and cannot be added.                                                                            |
         |                                                                                   |                                                                                                                                                                                                                                                                                                 |
         |                                                                                   | If this function is enabled, the system attempts to overwrite the existing queue permission policy for the user or user group in Ranger. If the overwriting fails, you need to delete the queue permission policy of the user or user group from the Ranger component and add the policy again. |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | **\*Access Authorization** (Click **Add User** to open the configuration window.) |                                                                                                                                                                                                                                                                                                 |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Username                                                                          | Select the users or user groups to be authorized. The users and user groups that have been added to the workspace are available for selection.                                                                                                                                                  |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Permission                                                                        | -  **submit-app**: the permission required for submitting queues                                                                                                                                                                                                                                |
         |                                                                                   | -  admin-queue: the permission required for managing queues                                                                                                                                                                                                                                     |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Agency                                                                            | If you want the users or user groups to be authorized to manage this policy, you can enable this option so that the users or user groups become the administrators of this policy and can update or delete the policy.                                                                          |
         +-----------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


      .. figure:: /_static/images/en-us_image_0000002234076804.png
         :alt: **Figure 5** MRS Yarn queue details

         **Figure 5** MRS Yarn queue details

   -  **DLI queue**

      On the DLI queue details page, click **Authorize**. In the displayed dialog box, set the parameters in :ref:`Table 2 <dataartsstudio_01_1162__table918935581611>` and click **Save**.

      .. table:: **Table 3** DLI queue authorization parameters

         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                      |
         +===================================+==================================================================================================================================+
         | Username                          | Select the users to be authorized. The users that have been added to the workspace are available for selection.                  |
         |                                   |                                                                                                                                  |
         |                                   | .. note::                                                                                                                        |
         |                                   |                                                                                                                                  |
         |                                   |    Permissions of DLI queues can be granted only to users, but not to user groups.                                               |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
         | Permissions                       | -  **Submitting jobs**: This permission allows you to submit jobs to this queue.                                                 |
         |                                   | -  **Terminating jobs**: This permission allows you to terminate jobs submitted to this queue.                                   |
         |                                   | -  **Deleting queues**: This permission allows you to delete the queue.                                                          |
         |                                   | -  **Granting permissions**: This permission allows you to grant queue permissions to other users.                               |
         |                                   | -  **Revoking permissions**: This permission allows you to revoke the queue permissions from other users except the queue owner. |
         |                                   | -  **Viewing other users' permissions**: This permission allows you to view the queue permissions of other users.                |
         |                                   | -  **Restarting queues**: This permission allows you to restart the queue.                                                       |
         |                                   | -  **Modifying queue specifications**: This permission allows you to modify queue specifications.                                |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------+


      .. figure:: /_static/images/en-us_image_0000002516803234.png
         :alt: **Figure 6** DLI queue details

         **Figure 6** DLI queue details

Related Operations
------------------

-  Deleting queues: In the queue permission directory, select queues and click |image2| to delete them.

   .. note::

      -  When a queue is deleted, it is not directly deleted from MRS or DLI. Instead, the queue will no longer be allocated to the workspace.
      -  After a queue is deleted, the permissions configured for the queue are still valid. For how to delete queue permissions, see :ref:`Deleting policies <dataartsstudio_01_1162__en-us_topic_0000001678432349_li1897203816355>` or :ref:`Revoking permissions <dataartsstudio_01_1162__li1121601319459>`.
      -  Yarn queues that are being used in DataArts Factory cannot be deleted in DataArts Security.

-  Editing policies: On the MRS Yarn queue details page, locate a policy and click **Edit** in the **Operation** column to edit the policy.

-  .. _dataartsstudio_01_1162__en-us_topic_0000001678432349_li1897203816355:

   Deleting policies: On the MRS Yarn queue details page, locate a policy and click **Delete** in the **Operation** column to delete the policy. To delete multiple policies at a time, select the policies and click **Delete** above the policy list.

   .. note::

      -  If you delete an MRS Ranger queue permission policy managed by DataArts Security, the policy will also be deleted from MRS Ranger.
      -  The deletion operation cannot be undone. Exercise caution when performing this operation.

-  Modifying permissions: On the DLI queue details page, locate a permission and click **Modify** in the **Operation** column.

-  .. _dataartsstudio_01_1162__li1121601319459:

   Revoking permissions: On the DLI queue details page, locate a permission and click **Revoke** in the **Operation** column.

.. _dataartsstudio_01_1162__section123461282269:

Reference: Configuring Strict Permission Control for Yarn
---------------------------------------------------------

-  The procedure is as follows:

   #. Log in to FusionInsight Manager and choose **Cluster** > **Services** > **Yarn**.

   #. On the displayed page, click the **Configuration** tab then the **All Configurations** sub-tab. On this sub-tab page, search for the **yarn.acl.enable** parameter and change its value to **true**. If the value is **true**, no further action is required.


      .. figure:: /_static/images/en-us_image_0000002234236628.png
         :alt: **Figure 7** Configuring yarn.acl.enable

         **Figure 7** Configuring yarn.acl.enable

Before configuring permissions for Yarn queues, you need to enable permission control for Yarn queues.

#. Log in to MRS FusionInsight Manager.

#. Choose **Cluster** > **Services** > **Yarn** and click **Configurations** and then **Basic Configurations**. Search for the **yarn.acl.enable** parameter and change its value to **true**. If the value is **true**, no further action is required.


   .. figure:: /_static/images/en-us_image_0000002269116017.png
      :alt: **Figure 8** Configuring the yarn.acl.enable parameter

      **Figure 8** Configuring the yarn.acl.enable parameter

#. After the parameter is set, click **Save** in the upper left corner and then **OK** in the dialog box to save the configuration.

#. After saving the configuration, switch to the **Instances** tab page, select the instance that has expired, click **More**, and select **Instance Rolling Restart** to make the configuration take effect.


   .. figure:: /_static/images/en-us_image_0000002269196097.png
      :alt: **Figure 9** Performing a rolling instance restart

      **Figure 9** Performing a rolling instance restart

.. |image1| image:: /_static/images/en-us_image_0000002234236656.png
.. |image2| image:: /_static/images/en-us_image_0000002234076768.png
