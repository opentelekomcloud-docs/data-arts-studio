:original_name: dataartsstudio_01_1153.html

.. _dataartsstudio_01_1153:

Checking the Cluster Version and Permissions
============================================

Unified permission governance has requirements on the data connection agent, data source version, and user permissions. Before using it, you need to check and prepare related configurations based on :ref:`Table 1 <dataartsstudio_01_1153__en-us_topic_0000001726747665_table134511476391>`.

.. note::

   DLI permission management involves only :ref:`Authorizing dlg_agency <dataartsstudio_01_1152>` and does not involve cluster version and permissions check.

Checklist
---------

.. _dataartsstudio_01_1153__en-us_topic_0000001726747665_table134511476391:

.. table:: **Table 1** Checklist

   +-------------------------------------------------+------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Check Item                                      | Mandatory                                            | Check Content                                                                                                  | Configuration Guide                                                                                                                                                                                                                                                                                                                                             |
   +=================================================+======================================================+================================================================================================================+=================================================================================================================================================================================================================================================================================================================================================================+
   | Data connection agent version                   | Mandatory for MRS/GaussDB(DWS) permission management | The CDM cluster version is 2.10.0.300 or later.                                                                | Log in to the CDM console and click **Cluster Management**. In the cluster list, locate the required cluster and click the cluster name. On the **Basic Information** page, view the cluster version.                                                                                                                                                           |
   |                                                 |                                                      |                                                                                                                |                                                                                                                                                                                                                                                                                                                                                                 |
   |                                                 |                                                      |                                                                                                                | If the version is not the required one, create another CDM cluster of the latest version or contact customer service or technical support.                                                                                                                                                                                                                      |
   +-------------------------------------------------+------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Ranger component configuration                  | Mandatory for MRS permission management              | LDAP user synchronization is enabled for the Ranger component of an MRS non-security cluster.                  | In a non-security MRS cluster, the Ranger component synchronizes Unix users by default, but does not synchronize users, user groups, or roles on Manager. Therefore, you need to switch the user synchronization policy. For details, see :ref:`Configuring the Ranger Component <dataartsstudio_01_1153__en-us_topic_0000001726747665_section25191347172613>`. |
   +-------------------------------------------------+------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Ranger connection user permission               |                                                      | The user for the connection has the admin permission of the Ranger component.                                  | The user for the Ranger connection must have the admin permission of the Ranger component. For details, see :ref:`Preparing a Ranger Admin User <dataartsstudio_01_1153__en-us_topic_0000001726747665_section2482162072810>`.                                                                                                                                   |
   +-------------------------------------------------+------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | guest_agent version of the GaussDB(DWS) cluster | Mandatory for GaussDB(DWS) permission management     | The guest_agent version of the GaussDB(DWS) cluster is 8.2.1, or later than 8.2.1 and earlier than 9.0.0.      | You can view the guest_agent version of the GaussDB(DWS) cluster using a developer debugging tool. For details, see :ref:`Viewing the guest_agent Version of a GaussDB(DWS) Cluster <dataartsstudio_01_1153__section1153213235185>`.                                                                                                                            |
   +-------------------------------------------------+------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | GaussDB(DWS) connection user permissions        |                                                      | -  In the non-RSM mode, the user for the connection must have at least the dbadmin permission of the database. | -  In the non-RSM mode, set the dbadmin administrator by referring to "Developer Guide" > "Database Security Management" > "Managing Users and Their Permissions" > "Database Users" in *GaussDB(DWS)* *User* *Guide*.                                                                                                                                          |
   |                                                 |                                                      | -  In the RSM mode, the user must have the system administrator permissions.                                   | -  In the RSM mode, set the system administrator by referring to "Cluster Security Management" > "Configuring Separation of Permissions" in *GaussDB(DWS)* *User* *Guide*.                                                                                                                                                                                      |
   +-------------------------------------------------+------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_1153__section1153213235185:

Viewing the guest_agent Version of a GaussDB(DWS) Cluster
---------------------------------------------------------

#. Log in to the GaussDB (DWS) console, choose **Clusters**, and locate a cluster.

#. Press **F12** to open the developer debugging tool and click the **Network** tab.


   .. figure:: /_static/images/en-us_image_0000002234084880.png
      :alt: **Figure 1** Network

      **Figure 1** Network

#. Click the name of the cluster to go to the **Basic Information** page. On the **Network** tab page, locate and click the long string starting with **clusters?type=xxxxxx**. In the right pane, click **Preview** and search for the **guest_agent_version** field, whose value is the guest_agent version of the GaussDB(DWS) cluster.


   .. figure:: /_static/images/en-us_image_0000002269124121.png
      :alt: **Figure 2** Locating the guest_agent_version field

      **Figure 2** Locating the guest_agent_version field

#. If the version is not your required one, contact the customer service or technical support of GaussDB(DWS).

.. _dataartsstudio_01_1153__en-us_topic_0000001726747665_section25191347172613:

Configuring the Ranger Component
--------------------------------

In a non-security MRS cluster, the Ranger component synchronizes Unix users by default, but does not synchronize users, user groups, or roles on FusionInsight Manager. Therefore, you need to switch the user synchronization policy. The procedure is as follows:

.. note::

   By default, the Ranger component of an MRS security cluster synchronizes LDAP users. No additional operation is required. If the default configuration is changed, you can change the user synchronization policy by referring to this section.

#. Log in to MRS Manager as user **admin**.

#. On the Manager page, choose **Cluster** > **Services** > **Ranger** > **Configurations** > **Basic Configurations**, search for **ranger.usersync.config.expandor** in the search box, and set its name to **ranger.usersync.sync.source** and value to **ldap**.

   .. note::

      By default, this parameter is unavailable for MRS clusters of old versions (for example, MRS 3.1.0). You can contact the customer service or technical support of MRS for support.


   .. figure:: /_static/images/en-us_image_0000002234084904.png
      :alt: **Figure 3** Configuring the ranger.usersync.config.expandor parameter

      **Figure 3** Configuring the ranger.usersync.config.expandor parameter

#. After the parameter is set, click **Save** in the upper left corner and then **OK** in the dialog box to save the configuration.

#. After the configuration is saved, switch to the **Instances** tab page, select the **UserSync** instance that has expired, click **More**, and select **Instance Rolling Restart** to make the configuration take effect.


   .. figure:: /_static/images/en-us_image_0000002234244740.png
      :alt: **Figure 4** Performing a rolling instance restart

      **Figure 4** Performing a rolling instance restart

.. _dataartsstudio_01_1153__en-us_topic_0000001726747665_section2482162072810:

Preparing a Ranger Admin User
-----------------------------

The user for the Ranger connection must have the admin permission of the Ranger component. The procedure is as follows:

#. Log in to MRS Manager as user **admin**.

#. Choose **System** > **Permission** > **User**. On the page displayed, click **Create** to add a dedicated human-machine user as the Kerberos authentication user. Select user groups **superGroup** and **hive** for the user, and assign the **Manager_administrator** role to the user.

#. Log in to MRS Manager as the new user and change the initial password.

#. On the Manager page, choose **Cluster** > **Services** > **Ranger**. On the Ranger overview page, click **RangerAdmin** to go to the Ranger WebUI.


   .. figure:: /_static/images/en-us_image_0000002234238528.png
      :alt: **Figure 5** Accessing the Ranger WebUI

      **Figure 5** Accessing the Ranger WebUI

#. Log out of the current account and use the Ranger administrator account to log in again. For a common cluster, the admin account for the Manager page can be used as the Ranger administrator account. For a security cluster, **rangeradmin** is the Ranger administrator account. For details about the default password of **rangeradmin**, see "FusionInsight Manager Operation Guide" > "Security Management" > "Security Overview" > "User Account List" in *MapReduce Service (MRS) x.x.x* *User* *Guide*.


   .. figure:: /_static/images/en-us_image_0000002269197945.png
      :alt: **Figure 6** Logging out of the current account

      **Figure 6** Logging out of the current account

#. Change the role of the new user from Ranger to Admin. Find the name of the new user in **Settings** > **Users/Groups/Roles** > **Users**.

   .. note::

      If the new user is not found on Ranger, wait for about five minutes until Ranger automatically synchronizes the MRS cluster role.


   .. figure:: /_static/images/en-us_image_0000002269124097.png
      :alt: **Figure 7** Searching for the username

      **Figure 7** Searching for the username

#. Click the username to go to the details page, change the user role to **Admin**, and click **Save**.


   .. figure:: /_static/images/en-us_image_0000002269124129.png
      :alt: **Figure 8** Changing the user role

      **Figure 8** Changing the user role
