:original_name: dataartsstudio_01_1160.html

.. _dataartsstudio_01_1160:

Enabling Fine-grained Authentication
====================================

If fine-grained authentication is disabled, the data source uses the account of the data connection for authentication during script execution and job tests in DataArts Factory. Therefore, user permission management enabled through roles or permission sets does not take effect for data development.

After fine-grained authentication is enabled, data sources no longer use the accounts of the data connections during script execution, job tests, and job scheduling in DataArts Factory of DataArts Studio. Instead, the current user is used for authentication. In this way, different users have different data permissions, and the permissions of roles and permission sets can be managed.

The impact of fine-grained authentication on the execution of scripts and jobs in DataArts Factory is as follows:

-  If fine-grained authentication is disabled, the account of the data connection is used for authentication during script execution and job tests and scheduling in DataArts Factory.
-  If fine-grained authentication is enabled for development mode, the current user is used for authentication during script execution and job tests in DataArts Factory, and the account of the data connection is used for authentication during job scheduling.
-  If fine-grained authentication is enabled for scheduling mode, the current user is used for authentication during script execution, job tests, and job scheduling in DataArts Factory.

Prerequisites
-------------

-  Required data permissions have been configured for the user who uses the data source to prevent service interruptions due to insufficient data permissions after fine-grained authentication is enabled. For details about how to configure permissions, see :ref:`Configuring Permission Sets <dataartsstudio_01_1156>` or :ref:`Configuring Roles <dataartsstudio_01_1157>`.
-  Before testing GaussDB(DWS) connectivity, you have synchronized users and switched the current login account to an IAM sub-user account with at least the DWS Database Access permission.
-  Proxy permissions have been configured for the users of an MRS Hive connection and MRS Spark connection. For details, see :ref:`Reference: Configuring Proxy Permissions for MRS Data Connection Users <dataartsstudio_01_1160__en-us_topic_0000001678072229_section133221581072>`.
-  The Spark2x component corresponding to the MRS Spark connection uses the multi-active instance mode. Otherwise, change the mode to the multi-active instance mode by referring to "Component Operation Guide" > "Using Spark 2x" > "Basic Operation" > "Scenario-Specific Configuration" > "Configuring the Switchover Between the Multi-active Instance Mode and the Multi-tenant Mode" in *MapReduce Service (MRS) x.x.x* *User* *Guide*.

Constraints
-----------

-  Fine-grained authentication for development mode is available only for GaussDB(DWS) and MRS Hive and MRS Spark data connections in proxy mode. Fine-grained authentication for scheduling mode is available only for the MRS Hive data connection in proxy mode.

-  Only the DARTS Administrator, Tenant Administrator, and data security administrator have the permission to configure fine-grained authentication.

-  Fine-grained authentication is supported only when the version of the CDM cluster selected for the agent in the data connection is 2.10.0.300 or later.

-  User permissions configured in a role/permission set take effect only after the role/permission set is successfully synchronized and fine-grained authentication is enabled.

-  The restrictions on the GaussDB(DWS) connectivity test are as follows:

   -  During the connectivity test, the system uses the current user to access the data source. The connectivity test will fail if the current user is a cloud platform account, because GaussDB(DWS) data cannot be accessed directly using a cloud platform account. Before testing GaussDB(DWS) connectivity, you must synchronize users and switch the current login account to an IAM sub-user account with at least the DWS Database Access permission.
   -  Fine-grained authentication is supported only when the guest_agent version of a GaussDB(DWS) cluster is 8.2.1, or later than 8.2.1 and earlier than 9.0.0. For details about how to check the guest_agent version of a GaussDB(DWS) cluster, see :ref:`Viewing the guest_agent Version of a GaussDB(DWS) Cluster <dataartsstudio_01_1153__section1153213235185>`.

-  The restrictions on the MRS Hive connectivity test are as follows:

   Fine-grained authentication is supported only when proxy permissions are configured for the users of MRS Hive data connections.

-  The restrictions on the MRS Spark connectivity test are as follows:

   -  Fine-grained authentication is supported only when proxy permissions are configured for the users of MRS Spark data connections.
   -  Fine-grained authentication is supported only when the Spark 2x component corresponding to the MRS Spark data connection uses the multi-active instance mode. For details about how to change the mode to the multi-active instance mode, see "Component Operation Guide" > "Using Spark 2x" > "Basic Operation" > "Scenario-Specific Configuration" > "Configuring the Switchover Between the Multi-active Instance Mode and the Multi-tenant Mode" in *MapReduce Service (MRS) x.x.x* *User* *Guide*.


Enabling Fine-grained Authentication
------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Permissions Applications**.

#. On the **Permission Applications** page, test the connectivity of the data connections for which you want to enable fine-grained authentication. During the connectivity test, the system uses the current user account to access the data source to ensure that the current user can access the data source.

   .. note::

      -  DWS data sources cannot be accessed using a a cloud platform account. Therefore, if you log in using a a cloud platform account, the connectivity test will fail. Before testing GaussDB(DWS) connectivity, you must synchronize users and switch the current login account to an IAM sub-user account with at least the DWS Database Access permission.


   .. figure:: /_static/images/en-us_image_0000002269118993.png
      :alt: **Figure 1** Testing connectivity

      **Figure 1** Testing connectivity

   If the connectivity is abnormal, perform the following checks:

   a. Ensure that the data source of the data connection is available.

   b. Check that the version of the CDM cluster selected as the agent for the data connection is 2.10.0.300 or later.

   c. Ensure that users have been synchronized. For details, see :ref:`Synchronizing IAM Users to the Data Source <dataartsstudio_01_1154>`.

   d. GaussDB(DWS) connection:

      #. Check whether the guest_agent version of the GaussDB(DWS) cluster connected by the data connection is 8.2.1 or later than 8.2.1 and earlier than 9.0.0. For details about how to check the guest_agent version of a GaussDB(DWS) cluster, see :ref:`Viewing the guest_agent Version of a GaussDB(DWS) Cluster <dataartsstudio_01_1153__section1153213235185>`.
      #. You have switched the current login account to an IAM sub-user account with at least the DWS Database Access permission.

   e. MRS Hive connection:

      Check whether a proxy has been configured for the user of the MRS Hive connection. If no proxy has been configured, see :ref:`Reference: Configuring Proxy Permissions for MRS Data Connection Users <dataartsstudio_01_1160__en-us_topic_0000001678072229_section133221581072>`.

   f. MRS Spark connection:

      #. Check whether a proxy has been configured for the user of the MRS Spark connection. If no proxy has been configured, see :ref:`Reference: Configuring Proxy Permissions for MRS Data Connection Users <dataartsstudio_01_1160__en-us_topic_0000001678072229_section133221581072>`.
      #. Check whether the Spark 2x component corresponding to the MRS Spark data connection uses the multi-active instance mode. Fine-grained authentication is supported only in multi-active instance mode. For details about how to change the mode to the multi-active instance mode, see "Component Operation Guide" > "Using Spark 2x" > "Basic Operation" > "Scenario-Specific Configuration" > "Configuring the Switchover Between the Multi-active Instance Mode and the Multi-tenant Mode" in *MapReduce Service (MRS) x.x.x* *User* *Guide*.

#. After the connectivity test is successful, select **Enabled for development mode** or **Enabled for scheduling mode** in the **Fine-grained Authentication Status** column, and click **Submit** to enable fine-grained authentication.


   .. figure:: /_static/images/en-us_image_0000002234239656.png
      :alt: **Figure 2** Enabling fine-grained authentication

      **Figure 2** Enabling fine-grained authentication

.. _dataartsstudio_01_1160__en-us_topic_0000001678072229_section133221581072:

Reference: Configuring Proxy Permissions for MRS Data Connection Users
----------------------------------------------------------------------

By default, when you access a data source through an MRS Hive or Spark data connection on DataArts Studio, the account configured in the data connection is used by default. If you configure Hive or Spark proxy permissions for the account in the MRS Hive or Spark data connection, you can use your own identity to perform this operation and enable fine-grained authentication. For details, see :ref:`Configuring Hive proxy permissions <dataartsstudio_01_1160__en-us_topic_0000001678072229_li107701256172613>` and :ref:`Configuring Spark proxy permissions <dataartsstudio_01_1160__en-us_topic_0000001678072229_li2023329153816>`.

**Configuring Hive proxy permissions**

#. .. _dataartsstudio_01_1160__en-us_topic_0000001678072229_li107701256172613:

   Log in to MRS FusionInsight Manager.

#. Choose **Cluster** > **Services** > **Hive** and click **Configurations** and then **Basic Configurations**. In the search box, enter **core.site.customized.configs** and set the parameter listed in :ref:`Figure 3 <dataartsstudio_01_1160__en-us_topic_0000001678072229_fig11331320153513>`.

   .. table:: **Table 1** Parameter

      +------------------------------+---------------------------------------------------------------------------+-------+
      | Parameter                    | Name                                                                      | Value |
      +==============================+===========================================================================+=======+
      | core.site.customized.configs | hadoop.proxyuser.\ **Username configured for the data connection**.users  | \*    |
      +------------------------------+---------------------------------------------------------------------------+-------+
      |                              | hadoop.proxyuser.\ **Username configured for the data connection**.groups | \*    |
      +------------------------------+---------------------------------------------------------------------------+-------+
      |                              | hadoop.proxyuser.\ **Username configured for the data connection**.hosts  | \*    |
      +------------------------------+---------------------------------------------------------------------------+-------+

   .. _dataartsstudio_01_1160__en-us_topic_0000001678072229_fig11331320153513:

   .. figure:: /_static/images/en-us_image_0000002269118989.png
      :alt: **Figure 3** Configuring the core.site.customized.configs parameter

      **Figure 3** Configuring the core.site.customized.configs parameter

#. After setting the parameter, click **Save** in the upper left corner and then **OK** in the dialog box to save the configuration.


   .. figure:: /_static/images/en-us_image_0000002234079800.png
      :alt: **Figure 4** Saving the configuration

      **Figure 4** Saving the configuration

#. After saving the configuration, switch to the **Instances** tab page, select the instance that has expired, click **More**, and select **Instance Rolling Restart** to make the configuration take effect.


   .. figure:: /_static/images/en-us_image_0000002234079792.png
      :alt: **Figure 5** Performing a rolling instance restart

      **Figure 5** Performing a rolling instance restart

**Configuring Spark proxy permissions**

#. .. _dataartsstudio_01_1160__en-us_topic_0000001678072229_li2023329153816:

   Log in to MRS FusionInsight Manager.

#. Choose **Cluster** > **Services** > **Spark** and click **Configurations** and then **Basic Configurations** or choose **Cluster** > **Services** > **Spark2x** and click **Configurations** and then **Basic Configurations**. In the search box, enter **spark.core-site.customized.configs** and set the parameter listed in :ref:`Figure 6 <dataartsstudio_01_1160__en-us_topic_0000001678072229_fig142318291381>`. The Spark component is used as an example.

   .. table:: **Table 2** Parameter

      +-----------------------+------------------------------+---------------------------------------------------------------------------+-----------------+
      | Parameter             |                              | Name                                                                      | Value           |
      +=======================+==============================+===========================================================================+=================+
      | Spark->JDBCServer     | core.site.customized.configs | hadoop.proxyuser.\ **Username configured for the data connection**.groups | \*              |
      |                       |                              |                                                                           |                 |
      | Or                    |                              |                                                                           |                 |
      |                       |                              |                                                                           |                 |
      | Spark2x->JDBCServer2x |                              |                                                                           |                 |
      +-----------------------+------------------------------+---------------------------------------------------------------------------+-----------------+
      |                       |                              | hadoop.proxyuser.\ **Username configured for the data connection**.hosts  | \*              |
      +-----------------------+------------------------------+---------------------------------------------------------------------------+-----------------+
      |                       |                              | hadoop.proxyuser.\ **Username configured for the data connection**.groups | \*              |
      +-----------------------+------------------------------+---------------------------------------------------------------------------+-----------------+
      |                       |                              | hadoop.proxyuser.\ **Username configured for the data connection**.hosts  | \*              |
      +-----------------------+------------------------------+---------------------------------------------------------------------------+-----------------+

   .. _dataartsstudio_01_1160__en-us_topic_0000001678072229_fig142318291381:

   .. figure:: /_static/images/en-us_image_0000002234079776.png
      :alt: **Figure 6** Configuring the spark.core-site.customized.configs parameter

      **Figure 6** Configuring the spark.core-site.customized.configs parameter

#. After setting the parameter, click **Save** in the upper left corner and then **OK** in the dialog box to save the configuration.


   .. figure:: /_static/images/en-us_image_0000002269118981.png
      :alt: **Figure 7** Saving the configuration

      **Figure 7** Saving the configuration

#. After saving the configuration, switch to the **Instance** tab page, select the instance that has expired, click **More**, and select **Instance Rolling Restart** to make the configuration take effect.


   .. figure:: /_static/images/en-us_image_0000002234239608.png
      :alt: **Figure 8** Performing a rolling instance restart

      **Figure 8** Performing a rolling instance restart
