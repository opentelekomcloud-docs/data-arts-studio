:original_name: dataartsstudio_01_1006.html

.. _dataartsstudio_01_1006:

Configuring Resource Permissions
================================

This section describes how to create resource permission policies for Ranger to control access to MRS resources and reduce data security risks for your enterprise.

Currently, the following permission policies can be created:

-  :ref:`Creating an HDFS Permission Policy <dataartsstudio_01_1006__section176917398372>`
-  :ref:`Creating a Hive Access Permission Policy <dataartsstudio_01_1006__section46911545493>`
-  :ref:`Creating a Hive Masking Permission Policy <dataartsstudio_01_1006__section470816335274>`
-  :ref:`Creating a Hive Row-Level Filter Permission Policy <dataartsstudio_01_1006__section1351855772711>`
-  :ref:`Creating an HBase Permission Policy <dataartsstudio_01_1006__section3665185018435>`
-  :ref:`Creating a Yarn Permission Policy <dataartsstudio_01_1006__section1870375317183>`
-  :ref:`Creating a Kafka Permission Policy <dataartsstudio_01_1006__section1047712512219>`
-  :ref:`Creating a Storm Permission Policy <dataartsstudio_01_1006__section017773615238>`

Prerequisites
-------------

-  A Ranger connection has been created in Management Center, and a correct RangerAdmin service IP address and Ranger service port have been set for the connection (see :ref:`MRS Ranger Connection Parameters <dataartsstudio_01_1312>` for details).

   .. note::

      When you test the Ranger connection in Management Center, the Ranger service IP address and port will not be verified, and no error will be reported even if they are incorrect. You are advised to check them manually.

-  Ranger authentication has been enabled for the corresponding MRS cluster. In security mode, Ranger authentication is enabled by default. In common mode, Ranger authentication is disabled by default. For details, see "Enabling Ranger Authentication" in *MapReduce Service (MRS) User Guide*.

Constraints
-----------

-  Resource permission policies depend on the Ranger authentication of MRS clusters. Currently, only permissions on MRS resources can be controlled.
-  A permission policy takes effect about 1 minute after being configured.

MRS Components that Support Access Control and the Permission List
------------------------------------------------------------------

Ranger can be used to integrate components in MRS clusters of version 3.0.0 or a later version to enable fine-grained access permission control for components. :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>` lists the supported components and describes related permissions. For details, see "Using Ranger (MRS 3.x)" > "Configuring Component Permission Policies" in *MapReduce Service (MRS) User Guide*.

.. _dataartsstudio_01_1006__table23037523175:

.. table:: **Table 1** Supported components and permissions

   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Component                         | Permission                                                                                 |
   +===================================+============================================================================================+
   | HDFS                              | HDFS file permissions:                                                                     |
   |                                   |                                                                                            |
   |                                   | -  Read: the permission required for read                                                  |
   |                                   | -  Write: the permission required for write                                                |
   |                                   | -  Execute: the permission required for executing a job                                    |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Hive                              | Hive database, data table, and column permissions:                                         |
   |                                   |                                                                                            |
   |                                   | -  Select: the permission required for query                                               |
   |                                   | -  Update: the permission required for update                                              |
   |                                   | -  Create: the permission required for creation                                            |
   |                                   | -  Drop: the permission required for dropping                                              |
   |                                   | -  Alter: the permission required for alteration                                           |
   |                                   | -  All: the permissions required for all operations                                        |
   |                                   | -  Temporary UDF Admin: the permission required for managing a temporary UDF               |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Yarn                              | Yarn queue permissions:                                                                    |
   |                                   |                                                                                            |
   |                                   | -  submit-app: the permission required for submitting a queue                              |
   |                                   | -  admin-queue: the permission required for managing a queue                               |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | HBase                             | HBase column and column family permissions:                                                |
   |                                   |                                                                                            |
   |                                   | -  Read: the permission required for read                                                  |
   |                                   | -  Write: the permission required for write                                                |
   |                                   | -  Create: the permission required for creation                                            |
   |                                   | -  Admin: the permission required by an administrator                                      |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Kafka                             | Kafka topic permissions:                                                                   |
   |                                   |                                                                                            |
   |                                   | -  Publish: the permission required for production                                         |
   |                                   | -  Consume: the permission required for consumption                                        |
   |                                   | -  Configure: the permission required for expanding the capacity of a topic                |
   |                                   | -  Describe: the permission required for query                                             |
   |                                   | -  Create: the permission required for creating a topic                                    |
   |                                   | -  Delete: the permission required for deleting a topic                                    |
   |                                   | -  Describe Configs: the permission required for querying configurations                   |
   |                                   | -  Alter Configs: the permission required for modifying configurations                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Storm                             | Storm topology permissions:                                                                |
   |                                   |                                                                                            |
   |                                   | -  Submit Topology: the permission required for submitting a topology                      |
   |                                   | -  File Upload: the permission required for uploading a file                               |
   |                                   | -  File Download: the permission required for downloading a file                           |
   |                                   | -  Kill Topology: the permission required for deleting a topology                          |
   |                                   | -  Rebalance: the permission required for rebalance                                        |
   |                                   | -  Activate: the permission required for activation                                        |
   |                                   | -  Deactivate: the permission required for deactivation                                    |
   |                                   | -  Get Topology Conf: the permission required for getting the configurations of a topology |
   |                                   | -  Get Topology: the permission required for getting a topology                            |
   |                                   | -  Get User Topology: the permission required for getting a user topology                  |
   |                                   | -  Get Topology Info: the permission required for getting the information of a topology    |
   |                                   | -  Upload New Credential: the permission required for uploading a new credential           |
   +-----------------------------------+--------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_1006__section176917398372:

Creating an HDFS Permission Policy
----------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Access Permission Management** > **Resource Permission Settings** from the left navigation bar.

   .. note::

      If error message "cluster [mrs_3x_autotest_do_not_del] get service failed. due to [null response from cdm:[404 NOT FOUND]]." is displayed, check whether the RangerAdmin service IP address and Ranger service port of the Ranger connection are correct in Management Center by referring to :ref:`MRS Ranger Connection Parameters <dataartsstudio_01_1312>`.


   .. figure:: /_static/images/en-us_image_0000002234082968.png
      :alt: **Figure 1** Resource Permission Settings page

      **Figure 1** Resource Permission Settings page

#. Click **Configure** to the right of **hacluster** under the HDFS component, and click **Create** in the upper part of the page displayed.


   .. figure:: /_static/images/en-us_image_0000002234082960.png
      :alt: **Figure 2** Creating a permission policy

      **Figure 2** Creating a permission policy

#. Set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269202205.png
      :alt: **Figure 3** Assigning a permission policy

      **Figure 3** Assigning a permission policy

   .. table:: **Table 2** Parameters for configuring an HDFS permission policy

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================+
      | Policy Type                       | The policy type is automatically generated based on the selected service component. **Policy Type** can be set to **Access**, **Mask**, and **Row-level Filter**. **Mask** and **Row-level Filter** are specific to Hive.                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Status                     | If **Policy Status** is **Enabled**, the permission policy takes effect immediately. If **Policy Status** is **Disabled**, the permission policy does not take effect after being created. **Policy Status** is set to **Enabled** by default.                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Overwrite                         | If **Overwrite** is set to **Enabled**, the new policy takes effect and the old policy does not take effect. **Overwrite** is set to **Enabled** by default.                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | When you need to create a temporary access policy, enable **Overwrite** and set **Validity Period** as required. In this way, even if the temporary access policy expires, the original permission policy still takes effect.                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Audit Log                         | If **Audit Log** is set to **Enabled**, logs are recorded. The log content includes the client access time, client IP address, client user, and resource operation result.                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Policy name is mandatory. A policy name can include only letters, numbers, underscores (_), and hyphens (-). Up to 50 characters are allowed.                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the policy. Up to 256 characters are allowed.                                                                                                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Topology                          | HDFS path for access permission control.                                                                                                                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Recursion                         | If the function is enabled, the resource path is in recursive mode. If the function is disabled, the resource path is in non-recursive mode. **Policy Status** is set to **Enabled** by default.                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Validity Period                   | You can set the effective time and expiration time of a policy. You can configure multiple time ranges.                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed                           | Users and user groups that are allowed to access the resources.                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`.     |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Exceptions                        | If you select **Exceptions for Allowed**, users who are not allowed to access the system are added to the user group that is allowed to access the system.                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | If you select **Exceptions for blocked**, users who are allowed to access the system are added to the user group that is blocked from the system.                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Block all other accesses          | If you select **Block all other accesses**, only specified users or user groups are allowed to access the system.                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Blocked                           | **Blocked** is displayed when **Block all other accesses** is not selected. Users and user groups that are not allowed to access the system can be specified in the **Blocked** area.                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are not allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`. |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_1006__section46911545493:

Creating a Hive Access Permission Policy
----------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Access Permission Management** > **Resource Permission Settings** from the left navigation bar.

   .. note::

      If error message "cluster [mrs_3x_autotest_do_not_del] get service failed. due to [null response from cdm:[404 NOT FOUND]]." is displayed, check whether the RangerAdmin service IP address and Ranger service port of the Ranger connection are correct in Management Center by referring to :ref:`MRS Ranger Connection Parameters <dataartsstudio_01_1312>`.


   .. figure:: /_static/images/en-us_image_0000002234082968.png
      :alt: **Figure 4** Resource Permission Settings page

      **Figure 4** Resource Permission Settings page

#. Click **Configure** to the right of the Hive component, and click **Create** in the upper part of the page displayed.


   .. figure:: /_static/images/en-us_image_0000002269122133.png
      :alt: **Figure 5** Creating a permission policy

      **Figure 5** Creating a permission policy

#. Set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002234082900.png
      :alt: **Figure 6** Configuring a Hive policy

      **Figure 6** Configuring a Hive policy

   The following table lists the parameters of a Hive permission policy.

   .. table:: **Table 3** Parameters of a Hive permission policy

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================+
      | Policy Type                       | The policy type is automatically generated based on the selected service component. **Policy Type** can be set to **Access**, **Mask**, and **Row-level Filter**. **Mask** and **Row-level Filter** are specific to Hive.                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Status                     | If **Policy Status** is **Enabled**, the permission policy takes effect immediately. If **Policy Status** is **Disabled**, the permission policy does not take effect after being created. **Policy Status** is set to **Enabled** by default.                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Overwrite                         | If **Overwrite** is set to **Enabled**, the new policy takes effect and the old policy does not take effect. **Overwrite** is set to **Enabled** by default.                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | To create a temporary access policy, enable **Overwrite** and set **Validity Period** as required. In this way, even if the temporary access policy expires, the original permission policy still takes effect.                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Audit Log                         | If **Audit Log** is set to **Enabled**, logs are recorded. The log content includes the client access time, client IP address, client user, and resource operation result.                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Policy name is mandatory. A policy name can include only letters, numbers, underscores (_), and hyphens (-). Up to 50 characters are allowed.                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the policy. Up to 256 characters are allowed.                                                                                                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | database                          | The **database** parameter is mandatory. You can set the database whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | table                             | The **table** parameter is mandatory. You can set the table whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Column                            | The **Column** parameter is mandatory. You can set the column whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Validity Period                   | You can set the effective time and expiration time of a policy. You can configure multiple time ranges.                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed                           | Users and user groups that are allowed to access the resources.                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`.     |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Exceptions                        | If you select **Exceptions for Allowed**, users who are not allowed to access the system are added to the user group that is allowed to access the system.                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | If you select **Exceptions for blocked**, users who are allowed to access the system are added to the user group that is blocked from the system.                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Block all other accesses          | If you select **Block all other accesses**, only specified users or user groups are allowed to access the system.                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Blocked                           | **Blocked** is displayed when **Block all other accesses** is not selected. Users and user groups that are not allowed to access the system can be specified in the **Blocked** area.                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are not allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`. |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_1006__section470816335274:

Creating a Hive Masking Permission Policy
-----------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Access Permission Management** > **Resource Permission Settings** from the left navigation bar.

   .. note::

      If error message "cluster [mrs_3x_autotest_do_not_del] get service failed. due to [null response from cdm:[404 NOT FOUND]]." is displayed, check whether the RangerAdmin service IP address and Ranger service port of the Ranger connection are correct in Management Center by referring to :ref:`MRS Ranger Connection Parameters <dataartsstudio_01_1312>`.


   .. figure:: /_static/images/en-us_image_0000002234082968.png
      :alt: **Figure 7** Resource Permission Settings page

      **Figure 7** Resource Permission Settings page

#. Click **Configure** to the right of the Hive component, and click **Create** in the upper part of the **Mask** tab page.


   .. figure:: /_static/images/en-us_image_0000002516802110.png
      :alt: **Figure 8** Creating a permission policy

      **Figure 8** Creating a permission policy

#. Set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002234082924.png
      :alt: **Figure 9** Configuring a Hive policy

      **Figure 9** Configuring a Hive policy

   .. table:: **Table 4** Parameters of a Hive permission policy

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================================================+
      | Policy Type                       | The policy type is automatically generated based on the selected service component. **Policy Type** can be set to **Access**, **Mask**, and **Row-level Filter**. **Mask** and **Row-level Filter** are specific to Hive.                                                          |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Status                     | If **Policy Status** is **Enabled**, the permission policy takes effect immediately. If **Policy Status** is **Disabled**, the permission policy does not take effect after being created. **Policy Status** is set to **Enabled** by default.                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Overwrite                         | If **Overwrite** is set to **Enabled**, the new policy takes effect and the old policy does not take effect. **Overwrite** is set to **Enabled** by default.                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                    |
      |                                   | To create a temporary access policy, enable **Overwrite** and set **Validity Period** as required. In this way, even if the temporary access policy expires, the original permission policy still takes effect.                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Audit Log                         | If **Audit Log** is set to **Enabled**, logs are recorded. The log content includes the client access time, client IP address, client user, and resource operation result.                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Policy name is mandatory. A policy name can include only letters, numbers, underscores (_), and hyphens (-). Up to 50 characters are allowed.                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the policy. Up to 256 characters are allowed.                                                                                                                                                                                                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Database                          | The **Database** parameter is mandatory. You can set the database whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Table                        | The **Data Table** parameter is mandatory. You can set the table whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Column                            | The **Column** parameter is mandatory. You can set the column whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Validity Period                   | You can set the effective time and expiration time of a policy. You can configure multiple time ranges.                                                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Mask                              | The masking mode for users or user groups to access data.                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                    |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                         |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                             |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                     |
      |                                   | -  **Permission**: the permission required by users who are allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`. |
      |                                   | -  **Mask Mode**: Columns that require permission control in a Hive table are masked based on the value of this parameter.                                                                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_1006__section1351855772711:

Creating a Hive Row-Level Filter Permission Policy
--------------------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Access Permission Management** > **Resource Permission Settings** from the left navigation bar.

   .. note::

      If error message "cluster [mrs_3x_autotest_do_not_del] get service failed. due to [null response from cdm:[404 NOT FOUND]]." is displayed, check whether the RangerAdmin service IP address and Ranger service port of the Ranger connection are correct in Management Center by referring to :ref:`MRS Ranger Connection Parameters <dataartsstudio_01_1312>`.


   .. figure:: /_static/images/en-us_image_0000002234082968.png
      :alt: **Figure 10** Resource Permission Settings page

      **Figure 10** Resource Permission Settings page

#. Click **Configure** to the right of the Hive component, and click **Create** in the upper part of the **Row-level Filter** tab page.


   .. figure:: /_static/images/en-us_image_0000002234242776.png
      :alt: **Figure 11** Creating a Hive row-level filter policy

      **Figure 11** Creating a Hive row-level filter policy

#. Set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269122161.png
      :alt: **Figure 12** Configuring a Hive policy

      **Figure 12** Configuring a Hive policy

   .. table:: **Table 5** Parameters of a Hive permission policy

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================================================+
      | Policy Type                       | The policy type is automatically generated based on the selected service component. **Policy Type** can be set to **Access**, **Mask**, and **Row-level Filter**. **Mask** and **Row-level Filter** are specific to Hive.                                                          |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Status                     | If **Policy Status** is **Enabled**, the permission policy takes effect immediately. If **Policy Status** is **Disabled**, the permission policy does not take effect after being created. **Policy Status** is set to **Enabled** by default.                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Overwrite                         | If **Overwrite** is set to **Enabled**, the new policy takes effect and the old policy does not take effect. **Overwrite** is set to **Enabled** by default.                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                    |
      |                                   | To create a temporary access policy, enable **Overwrite** and set **Validity Period** as required. In this way, even if the temporary access policy expires, the original permission policy still takes effect.                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Audit Log                         | If **Audit Log** is set to **Enabled**, logs are recorded. The log content includes the client access time, client IP address, client user, and resource operation result.                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Policy name is mandatory. A policy name can include only letters, numbers, underscores (_), and hyphens (-). Up to 50 characters are allowed.                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the policy. Up to 256 characters are allowed.                                                                                                                                                                                                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Database                          | The **Database** parameter is mandatory. You can set the database whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Table                        | The **Data Table** parameter is mandatory. You can set the table whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Column                            | The **Column** parameter is mandatory. You can set the column whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Validity Period                   | You can set the effective time and expiration time of a policy. You can configure multiple time ranges.                                                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Row-level Filter                  | Users and user groups that are allowed to access the resources.                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                    |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                         |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                             |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                     |
      |                                   | -  **Permission**: the permission required by users who are allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`. |
      |                                   | -  **Row-level Filter**: Filter by field content. The parameter format is as follows: Field=Value. Example: state=1.                                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_1006__section3665185018435:

Creating an HBase Permission Policy
-----------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Access Permission Management** > **Resource Permission Settings** from the left navigation bar.

   .. note::

      If error message "cluster [mrs_3x_autotest_do_not_del] get service failed. due to [null response from cdm:[404 NOT FOUND]]." is displayed, check whether the RangerAdmin service IP address and Ranger service port of the Ranger connection are correct in Management Center by referring to :ref:`MRS Ranger Connection Parameters <dataartsstudio_01_1312>`.


   .. figure:: /_static/images/en-us_image_0000002234082968.png
      :alt: **Figure 13** Resource Permission Settings page

      **Figure 13** Resource Permission Settings page

#. Click **Configure** to the right of the HBase component, and click **Create** in the upper part of the page displayed.


   .. figure:: /_static/images/en-us_image_0000002269202229.png
      :alt: **Figure 14** Creating an HBase permission policy

      **Figure 14** Creating an HBase permission policy

#. Set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269202209.png
      :alt: **Figure 15** Configuring an HBase policy

      **Figure 15** Configuring an HBase policy

   .. table:: **Table 6** Parameters of an HBase permission policy

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================+
      | Policy Type                       | The policy type is automatically generated based on the selected service component. **Policy Type** can be set to **Access**, **Mask**, and **Row-level Filter**. **Mask** and **Row-level Filter** are specific to Hive.                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Status                     | If **Policy Status** is **Enabled**, the permission policy takes effect immediately. If **Policy Status** is **Disabled**, the permission policy does not take effect after being created. **Policy Status** is set to **Enabled** by default.                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Overwrite                         | If **Overwrite** is set to **Enabled**, the new policy takes effect and the old policy does not take effect. **Overwrite** is set to **Enabled** by default.                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | To create a temporary access policy, enable **Overwrite** and set **Validity Period** as required. In this way, even if the temporary access policy expires, the original permission policy still takes effect.                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Audit Log                         | If **Audit Log** is set to **Enabled**, logs are recorded. The log content includes the client access time, client IP address, client user, and resource operation result.                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Policy name is mandatory. A policy name can include only letters, numbers, underscores (_), and hyphens (-). Up to 50 characters are allowed.                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the policy. Up to 256 characters are allowed.                                                                                                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Table                        | The **Data Table** parameter is mandatory. You can set the table whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Column                            | The **Column** parameter is mandatory. You can set the column whose permissions need to be controlled. Fuzzy search is supported.                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Column Family                     | **Column Family** is mandatory. This parameter indicates a set of column families in an HBase cluster.                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Validity Period                   | You can set the effective time and expiration time of a policy. You can configure multiple time ranges.                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed                           | Users and user groups that are allowed to access the resources.                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`.     |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Exceptions                        | If you select **Exceptions for Allowed**, users who are not allowed to access the system are added to the user group that is allowed to access the system.                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | If you select **Exceptions for blocked**, users who are allowed to access the system are added to the user group that is blocked from the system.                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Block all other accesses          | If you select **Block all other accesses**, only specified users or user groups are allowed to access the system.                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Blocked                           | **Blocked** is displayed when **Block all other accesses** is not selected. Users and user groups that are not allowed to access the system can be specified in the **Blocked** area.                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are not allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`. |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_1006__section1870375317183:

Creating a Yarn Permission Policy
---------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Access Permission Management** > **Resource Permission Settings** from the left navigation bar.

   .. note::

      If error message "cluster [mrs_3x_autotest_do_not_del] get service failed. due to [null response from cdm:[404 NOT FOUND]]." is displayed, check whether the RangerAdmin service IP address and Ranger service port of the Ranger connection are correct in Management Center by referring to :ref:`MRS Ranger Connection Parameters <dataartsstudio_01_1312>`.


   .. figure:: /_static/images/en-us_image_0000002234082968.png
      :alt: **Figure 16** Resource Permission Settings page

      **Figure 16** Resource Permission Settings page

#. Click **Configure** to the right of the Yarn component, and click **Create** in the upper part of the page that is displayed.


   .. figure:: /_static/images/en-us_image_0000002234242744.png
      :alt: **Figure 17** Creating a Yarn permission policy

      **Figure 17** Creating a Yarn permission policy

#. Set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002234242796.png
      :alt: **Figure 18** Configuring a Yarn policy

      **Figure 18** Configuring a Yarn policy

   .. table:: **Table 7** Parameters of a Yarn permission policy

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================+
      | Policy Type                       | The policy type is automatically generated based on the selected service component. **Policy Type** can be set to **Access**, **Mask**, and **Row-level Filter**. **Mask** and **Row-level Filter** are specific to Hive.                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Status                     | If **Policy Status** is **Enabled**, the permission policy takes effect immediately. If **Policy Status** is **Disabled**, the permission policy does not take effect after being created. **Policy Status** is set to **Enabled** by default.                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Overwrite                         | If **Overwrite** is set to **Enabled**, the new policy takes effect and the old policy does not take effect. **Overwrite** is set to **Enabled** by default.                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | To create a temporary access policy, enable **Overwrite** and set **Validity Period** as required. In this way, even if the temporary access policy expires, the original permission policy still takes effect.                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Audit Log                         | If **Audit Log** is set to **Enabled**, logs are recorded. The log content includes the client access time, client IP address, client user, and resource operation result.                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Policy name is mandatory. A policy name can include only letters, numbers, underscores (_), and hyphens (-). Up to 50 characters are allowed.                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the policy. Up to 256 characters are allowed.                                                                                                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Queue                             | Resource scheduling queue in the Yarn service.                                                                                                                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Validity Period                   | You can set the effective time and expiration time of a policy. You can configure multiple time ranges.                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed                           | Users and user groups that are allowed to access the resources.                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`.     |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Exceptions                        | If you select **Exceptions for Allowed**, users who are not allowed to access the system are added to the user group that is allowed to access the system.                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | If you select **Exceptions for blocked**, users who are allowed to access the system are added to the user group that is blocked from the system.                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Block all other accesses          | If you select **Block all other accesses**, only specified users or user groups are allowed to access the system.                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Blocked                           | **Blocked** is displayed when **Block all other accesses** is not selected. Users and user groups that are not allowed to access the system can be specified in the **Blocked** area.                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are not allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`. |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_1006__section1047712512219:

Creating a Kafka Permission Policy
----------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Access Permission Management** > **Resource Permission Settings** from the left navigation bar.

   .. note::

      If error message "cluster [mrs_3x_autotest_do_not_del] get service failed. due to [null response from cdm:[404 NOT FOUND]]." is displayed, check whether the RangerAdmin service IP address and Ranger service port of the Ranger connection are correct in Management Center by referring to :ref:`MRS Ranger Connection Parameters <dataartsstudio_01_1312>`.


   .. figure:: /_static/images/en-us_image_0000002234082968.png
      :alt: **Figure 19** Resource Permission Settings page

      **Figure 19** Resource Permission Settings page

#. Click **Configure** to the right of the Kafka component, and click **Create** in the upper part of the page that is displayed.


   .. figure:: /_static/images/en-us_image_0000002269202241.png
      :alt: **Figure 20** Creating a Kafka permission policy

      **Figure 20** Creating a Kafka permission policy

#. Set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002234242804.png
      :alt: **Figure 21** Configuring a Kafka policy

      **Figure 21** Configuring a Kafka policy

   .. table:: **Table 8** Parameters of a Kafka permission policy

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================+
      | Policy Type                       | The policy type is automatically generated based on the selected service component. **Policy Type** can be set to **Access**, **Mask**, and **Row-level Filter**. **Mask** and **Row-level Filter** are specific to Hive.                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Status                     | If **Policy Status** is **Enabled**, the permission policy takes effect immediately. If **Policy Status** is **Disabled**, the permission policy does not take effect after being created. **Policy Status** is set to **Enabled** by default.                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Overwrite                         | If **Overwrite** is set to **Enabled**, the new policy takes effect and the old policy does not take effect. **Overwrite** is set to **Enabled** by default.                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | To create a temporary access policy, enable **Overwrite** and set **Validity Period** as required. In this way, even if the temporary access policy expires, the original permission policy still takes effect.                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Audit Log                         | If **Audit Log** is set to **Enabled**, logs are recorded. The log content includes the client access time, client IP address, client user, and resource operation result.                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Policy name is mandatory. A policy name can include only letters, numbers, underscores (_), and hyphens (-). Up to 50 characters are allowed.                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the policy. Up to 256 characters are allowed.                                                                                                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Conditions                 | Range of IP addresses that can access the Kafka topic.                                                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Topic                             | The message topic of a Kafka cluster.                                                                                                                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Validity Period                   | You can set the effective time and expiration time of a policy. You can configure multiple time ranges.                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed                           | Users and user groups that are allowed to access the resources.                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`.     |
      |                                   | -  **Policy Conditions**: the range of IP addresses that can access the Kafka topic.                                                                                                                                                                                                   |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Exceptions                        | If you select **Exceptions for Allowed**, users who are not allowed to access the system are added to the user group that is allowed to access the system.                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | If you select **Exceptions for blocked**, users who are allowed to access the system are added to the user group that is blocked from the system.                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Blocked                           | **Blocked** is displayed when **Block all other accesses** is not selected. Users and user groups that are not allowed to access the system can be specified in the **Blocked** area.                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are not allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`. |
      |                                   | -  **Policy Conditions**: the range of IP addresses that can access the Kafka topic.                                                                                                                                                                                                   |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_1006__section017773615238:

Creating a Storm Permission Policy
----------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Access Permission Management** > **Resource Permission Settings** from the left navigation bar.

   .. note::

      If error message "cluster [mrs_3x_autotest_do_not_del] get service failed. due to [null response from cdm:[404 NOT FOUND]]." is displayed, check whether the RangerAdmin service IP address and Ranger service port of the Ranger connection are correct in Management Center by referring to :ref:`MRS Ranger Connection Parameters <dataartsstudio_01_1312>`.


   .. figure:: /_static/images/en-us_image_0000002234082968.png
      :alt: **Figure 22** Resource Permission Settings page

      **Figure 22** Resource Permission Settings page

#. Click **Configure** to the right of the Storm component, and click **Create** in the upper part of the page displayed.


   .. figure:: /_static/images/en-us_image_0000002234082980.png
      :alt: **Figure 23** Creating a Storm permission policy

      **Figure 23** Creating a Storm permission policy

#. Set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269122177.png
      :alt: **Figure 24** Configuring a Storm policy

      **Figure 24** Configuring a Storm policy

   .. table:: **Table 9** Parameters of a Storm permission policy

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================+
      | Policy Type                       | The policy type is automatically generated based on the selected service component. **Policy Type** can be set to **Access**, **Mask**, and **Row-level Filter**. **Mask** and **Row-level Filter** are specific to Hive.                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Status                     | If **Policy Status** is **Enabled**, the permission policy takes effect immediately. If **Policy Status** is **Disabled**, the permission policy does not take effect after being created. **Policy Status** is set to **Enabled** by default.                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Overwrite                         | If **Overwrite** is set to **Enabled**, the new policy takes effect and the old policy does not take effect. **Overwrite** is set to **Enabled** by default.                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | To create a temporary access policy, enable **Overwrite** and set **Validity Period** as required. In this way, even if the temporary access policy expires, the original permission policy still takes effect.                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Audit Log                         | If **Audit Log** is set to **Enabled**, logs are recorded. The log content includes the client access time, client IP address, client user, and resource operation result.                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                       | Policy name is mandatory. A policy name can include only letters, numbers, underscores (_), and hyphens (-). Up to 50 characters are allowed.                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the policy. Up to 256 characters are allowed.                                                                                                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Topology                          | Tasks in a Storm cluster.                                                                                                                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Validity Period                   | You can set the effective time and expiration time of a policy. You can configure multiple time ranges.                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed                           | Users and user groups that are allowed to access the resources.                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`.     |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Exceptions                        | If you select **Exceptions for Allowed**, users who are not allowed to access the system are added to the user group that is allowed to access the system.                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | If you select **Exceptions for blocked**, users who are allowed to access the system are added to the user group that is blocked from the system.                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Block all other accesses          | If you select **Block all other accesses**, only specified users or user groups are allowed to access the system.                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Blocked                           | **Blocked** is displayed when **Block all other accesses** is not selected. Users and user groups that are not allowed to access the system can be specified in the **Blocked** area.                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Username**: MRS user.                                                                                                                                                                                                                                                             |
      |                                   | -  **Role**: MRS role.                                                                                                                                                                                                                                                                 |
      |                                   | -  **Group**: MRS user groups.                                                                                                                                                                                                                                                         |
      |                                   | -  **Permission**: the permission required by users who are not allowed to access the system. **Permission** and **Username** can be left blank or not left blank at the same time. For details on service permissions, see :ref:`Table 1 <dataartsstudio_01_1006__table23037523175>`. |
      |                                   | -  **Granted**: If **Granted** is selected, management permissions are assigned to appropriate users and groups. Delegated administrators can update and delete policies and create sub-policies based on the original policies.                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
