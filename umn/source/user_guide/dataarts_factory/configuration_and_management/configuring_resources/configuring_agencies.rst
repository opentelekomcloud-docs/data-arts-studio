:original_name: dataartsstudio_01_0555.html

.. _dataartsstudio_01_0555:

Configuring Agencies
====================

The following problems may occur during job execution in DataArts Factory:

-  The job execution mechanism of the DataArts Factory module is to execute the job as the user who starts the job. For a job that is executed in periodic scheduling mode, if the IAM account used to start the job is deleted during the scheduling period, the system cannot obtain the user identity authentication information. As a result, the job fails to be executed.
-  If a job is started by a low-privilege user, the job fails to be executed due to insufficient permissions.

To solve the preceding problems, configure an agency. When an agency is configured, the job interacts with other services as an agency during job execution to prevent job execution failures in the preceding scenarios.

Role of an Agency
-----------------

Cloud services interwork with each other, and some cloud services are dependent on other services. You can create an agency to delegate cloud services to access other services and perform resource O&M on your behalf.

Agency Classification
---------------------

Agencies are classified into workspace-level agencies and job-level agencies.

-  Workspace-level agencies can be globally applied to all jobs in the workspace.
-  Job-level agencies can only be applied to a single job.

The job-level agency has a higher priority than the workspace-level agency. If neither of them is configured, execute the job as the user who starts the job.

Constraints
-----------

-  To create or modify an agency, you must have the **Security Administrator** permissions.
-  To configure a workspace-level agency, you must have the **DAYU Administrator** or **Tenant** **Administrator** policy.
-  To configure a job-level agency, you must have the permission to view the list of agencies.

.. _dataartsstudio_01_0555__section17505112912402:

Creating an Agency
------------------

#. Log in to the IAM console.

#. Choose **Agencies**. On the displayed page, click **Create Agency**.

#. Enter an agency name, for example, DataArts Studio\_agency.

#. Set **Agency Type** to **Cloud service** and select **DataArts Studio** for **Cloud Service** so that DataArts Studio can perform resource O&M operations on behalf of you.

#. Set **Validity Period** to **Unlimited**.


   .. figure:: /_static/images/en-us_image_0000001497810938.png
      :alt: **Figure 1** Creating an agency

      **Figure 1** Creating an agency

#. Click **Assign Permissions** in the **Permissions** area.

#. On the displayed page, search for the **Tenant Administrator** policy, select it, and click **OK**. See :ref:`Figure 2 <dataartsstudio_01_0555__fig13792331596>`.

   -  Users assigned the **Tenant Administrator** policy have all permissions on all services except on IAMIAM. Therefore, delegate the **Tenant Administrator** policy to DataArts Studio so that DataArts Studio can access all related services.

   -  If you want to meet the security control requirements for fewer permissions, you only need to configure the **OBS OperateAccess** permissions (During job execution, execution log information needs to be written to OBS. Therefore, you need to add the **OBS OperateAccess** permissions.) . Then, configure different agency permissions based on the node type in the job. For example, if a job contains only the **Import GES** node, you can configure the **GES Administrator** and **OBS OperateAccess** permissions. For details, see :ref:`Permissions Assignment <dataartsstudio_01_0555__section1813152013116>`.

      .. _dataartsstudio_01_0555__fig13792331596:

      .. figure:: /_static/images/en-us_image_0000001322407892.jpg
         :alt: **Figure 2** Assigning permissions

         **Figure 2** Assigning permissions

#. Click **OK**.

.. _dataartsstudio_01_0555__section1813152013116:

Permissions Assignment
----------------------

After the operation permissions of an account are delegated to DataArts Studio, you must configure the permissions of the agency identity so that DataArts Studio can interact with other services.

For purposes of permissions minimization, you can configure the **Admin** permissions for services based on the node types in jobs. For details, see :ref:`Table 1 <dataartsstudio_01_0555__table18185359163814>`.

The **Admin** permissions can also be configured based on the operations, resources, and request conditions for a specific service. Based on the node types in jobs, permissions are defined by service APIs to allow for more fine-grained, secure access control of cloud resources. Configure the permissions according to :ref:`Table 2 <dataartsstudio_01_0555__table116756441498>`. For example, for a job containing the **Import GES** node, you only need to create a custom policy and select **ges:graph:getDetail** (viewing graph details), **ges:jobs:getDetail** (querying task status), and **ges:graph:access** (using graphs).

.. important::

   -  MRS-related nodes (MRS Presto SQL, MRS Spark, MRS Spark Python, MRS Flink Job, and MRS MapReduce) and directly connected nodes (MRS Spark SQL and MRS Hive SQL) do not support job submission in agency mode, therefore, jobs of these types cannot be configured with agencies.
   -  MRS clusters that support job submission in agency mode are as follows:

      -  Non-security cluster
      -  Security cluster whose version is later than 2.1.0 and which has MRS 2.1.0.1 or later

-  Configure the service-level **Admin** permissions.

   During job execution, execution log information needs to be written to OBS. Therefore, the **OBS** **OperateAccess** permissions must be added for all jobs during coarse-grained authorization.

.. _dataartsstudio_01_0555__table18185359163814:

.. table:: **Table 1** The **admin** permissions for related nodes

   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Node Name                                                                                           | System Permission           | Description                                                                                                                                                                               |
   +=====================================================================================================+=============================+===========================================================================================================================================================================================+
   | CDM Job                                                                                             | DAYU Administrator          | All DataArts Studio permissions                                                                                                                                                           |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Import GES                                                                                          | GES Administrator           | Permissions required to perform all operations on GES. This role depends on the **Tenant Guest** and **Server Administrator** roles in the same project.                                  |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | -  MRS Presto SQL, MRS Spark, MRS Spark Python, MRS Flink Job, and MRS MapReduce                    | MRS Administrator           | Users assigned the **MRS Administrator** role can perform all operations on MRS. This role depends on the **Tenant Guest** and **Server Administrator** roles in the same project.        |
   | -  MRS Spark SQL and MRS Hive SQL (connecting to MRS clusters through MRS APIs)                     |                             |                                                                                                                                                                                           |
   |                                                                                                     | KMS Administrator           | Users assigned the **KMS Administrator** role have the administrator permissions for encryption keys in DEW.                                                                              |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | MRS Spark SQL, MRS Hive SQL, MRS Kafka, and Kafka Client (connecting to the clusters in proxy mode) | DAYU Administrator          | **DAYU Administrator** has all permissions required for DataArts Studio.                                                                                                                  |
   |                                                                                                     |                             |                                                                                                                                                                                           |
   |                                                                                                     | KMS Administrator           | Users assigned the **KMS Administrator** policy have the administrator permissions for encryption keys in DEW.                                                                            |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DLI Flink Job, DLI SQL, and DLI Spark                                                               | DLI Service Admin           | All operation permissions for DLI.                                                                                                                                                        |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DWS SQL, RDS SQL (connecting to data sources in proxy mode), and Shell                              | DAYU Administrator          | **DAYU Administrator** has all permissions required for DataArts Studio.                                                                                                                  |
   |                                                                                                     |                             |                                                                                                                                                                                           |
   |                                                                                                     | KMS Administrator           | Users assigned the **KMS Administrator** policy have the administrator permissions for encryption keys in DEW.                                                                            |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CSS                                                                                                 | DAYU Administrator          | **DAYU Administrator** has all permissions required for DataArts Studio.                                                                                                                  |
   |                                                                                                     |                             |                                                                                                                                                                                           |
   |                                                                                                     | Elasticsearch Administrator | Users assigned the **Elasticsearch Administrator** policy have all permissions for CSS. This role depends on the **Tenant Guest** and **Server Administrator** roles in the same project. |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Create OBS, Delete OBS, and OBS Manager                                                             | OBS OperateAccess           | Basic object operation permissions, such as viewing buckets, uploading objects, obtaining objects, deleting objects, and obtaining object ACLs.                                           |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | SMN                                                                                                 | SMN Administrator           | All operation permissions for SMN.                                                                                                                                                        |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Configure fine-grained permissions. (Create custom policies based on the actions supported by each service.)

   For details on how to create a custom policy, see "Creating a Custom Policy" in the *Identity and Access Management User Guide*.

.. note::

   -  During job execution, you must write execution logs to OBS. When the fine-grained authorization mode is used, the following OBS permissions need to be added for all types of jobs:

      -  obs:bucket:GetBucketLocation
      -  obs:object:GetObject
      -  obs:bucket:CreateBucket
      -  obs:object:PutObject
      -  obs:bucket:ListAllMyBuckets
      -  obs:bucket:ListBucket

   -  CDM Job nodes belong to the DataArts Studio module. DataArts Studio does not support fine-grained authorization. Therefore, only the **DataArts Studio Administrator** policy can be configured for jobs containing these types of nodes.
   -  CSS does not support fine-grained authorization and requires a proxy. Therefore, the **DataArts Studio Administrator** and **Elasticsearch Administrator** policies can be configured for jobs containing these nodes.
   -  SMN does not support fine-grained authorization. Therefore, jobs containing these nodes require the **SMN Administrator** permissions.

.. _dataartsstudio_01_0555__table116756441498:

.. table:: **Table 2** Creating a custom policy

   +-----------------------------------------------------------------------------------------------------+-----------------------------------------+
   | Node Name                                                                                           | Action                                  |
   +=====================================================================================================+=========================================+
   | Import GES                                                                                          | -  ges:graph:access                     |
   |                                                                                                     | -  ges:graph:getDetail                  |
   |                                                                                                     | -  ges:jobs:getDetail                   |
   +-----------------------------------------------------------------------------------------------------+-----------------------------------------+
   | -  MRS Presto SQL, MRS Spark, MRS Spark Python, MRS Flink Job, and MRS MapReduce                    | -  mrs:job:delete                       |
   | -  MRS Spark SQL and MRS Hive SQL (connecting to MRS clusters through MRS APIs)                     | -  mrs:job:stop                         |
   |                                                                                                     | -  mrs:job:submit                       |
   |                                                                                                     | -  mrs:cluster:get                      |
   |                                                                                                     | -  mrs:cluster:list                     |
   |                                                                                                     | -  mrs:job:get                          |
   |                                                                                                     | -  mrs:job:list                         |
   |                                                                                                     | -  kms:dek:crypto                       |
   |                                                                                                     | -  kms:cmk:get                          |
   +-----------------------------------------------------------------------------------------------------+-----------------------------------------+
   | MRS Spark SQL, MRS Hive SQL, MRS Kafka, and Kafka Client (connecting to the clusters in proxy mode) | -  kms:dek:crypto                       |
   |                                                                                                     | -  kms:cmk:get                          |
   |                                                                                                     | -  DataArts Studio Administrator (role) |
   +-----------------------------------------------------------------------------------------------------+-----------------------------------------+
   | DLI Flink Job, DLI SQL, and DLI Spark                                                               | -  dli:jobs:get                         |
   |                                                                                                     | -  dli:jobs:update                      |
   |                                                                                                     | -  dli:jobs:create                      |
   |                                                                                                     | -  dli:queue:submit_job                 |
   |                                                                                                     | -  dli:jobs:list                        |
   |                                                                                                     | -  dli:jobs:list_all                    |
   +-----------------------------------------------------------------------------------------------------+-----------------------------------------+
   | DWS SQL, RDS SQL (connecting to data sources in proxy mode), and Shell                              | -  kms:dek:crypto                       |
   |                                                                                                     | -  kms:cmk:get                          |
   |                                                                                                     | -  DataArts Studio Administrator (role) |
   +-----------------------------------------------------------------------------------------------------+-----------------------------------------+
   | Create OBS, Delete OBS, and OBS Manager                                                             | -  obs:bucket:GetBucketLocation         |
   |                                                                                                     | -  obs:bucket:ListBucketVersions        |
   |                                                                                                     | -  obs:object:GetObject                 |
   |                                                                                                     | -  obs:bucket:CreateBucket              |
   |                                                                                                     | -  obs:bucket:DeleteBucket              |
   |                                                                                                     | -  obs:object:DeleteObject              |
   |                                                                                                     | -  obs:object:PutObject                 |
   |                                                                                                     | -  obs:bucket:ListAllMyBuckets          |
   |                                                                                                     | -  obs:bucket:ListBucket                |
   +-----------------------------------------------------------------------------------------------------+-----------------------------------------+

.. _dataartsstudio_01_0555__section3485198599:

Configuring a Workspace-Level Agency
------------------------------------

.. caution::

   A workspace-level agency impacts on all jobs. Some jobs contain nodes related to MRS. Exercise caution when performing this operation.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 3** DataArts Factory

      **Figure 3** DataArts Factory

#. In the navigation pane, choose **Configuration** > **Configure**.

#. Click **Agency**. On the displayed page, configure an agency.

#. You can select an agency from the agency list or create a new one. For details on how to create an agency and configure permissions, see :ref:`Creating an Agency <dataartsstudio_01_0555__section17505112912402>`.


   .. figure:: /_static/images/en-us_image_0000001373408033.jpg
      :alt: **Figure 4** Configuring a workspace-level agency

      **Figure 4** Configuring a workspace-level agency

#. Click **OK** to return to the **Agency Configuration** page. Then, click |image1| to save the settings.

.. _dataartsstudio_01_0555__section20224154881414:

Configuring a Job-level Agency
------------------------------

.. note::

   You can create a job-level agency when creating a job. You can also modify the agency of an existing job.

**Configuring an agency when creating a job**

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 5** DataArts Factory

      **Figure 5** DataArts Factory

#. In the navigation pane of the DataArts Factory homepage, choose **Development** > **Develop Job**.

#. Right-click the job directory and choose **Create Job** from the shortcut menu. The **Create Job** dialog box is displayed. If a workspace-level agency has been configured, it is used for the job by default. You can also select another agency from the agency list.


   .. figure:: /_static/images/en-us_image_0000001322247904.jpg
      :alt: **Figure 6** Configuring an agency for a job

      **Figure 6** Configuring an agency for a job

   **Modifying the agency of an existing job**

#. In the navigation pane of the DataArts Factory homepage, choose **Development** > **Develop Job**.
#. In the job directory, double-click an existing job. On the far right of the displayed page, click **Basic Info**. The dialog box of the job's basic settings is displayed. If a workspace-level agency has been configured, it is used by default. You can also select another agency from the agency list.

.. |image1| image:: /_static/images/en-us_image_0000001373288349.png
