:original_name: dataartsstudio_01_0555.html

.. _dataartsstudio_01_0555:

Configuring a Scheduling Identity
=================================

The following problems may occur during job execution in DataArts Factory:

-  The job execution mechanism of the DataArts Factory module is to execute the job as the user who starts the job. For a job that is executed in periodic scheduling mode, if the IAM account used to start the job is suspended or deleted during the scheduling period, the system cannot obtain the user identity authentication information. As a result, the job fails to be executed.
-  If a job is started by a low-privilege user, the job fails to be executed due to insufficient permissions.

To address these issues, you can configure an identity for scheduling jobs. During job scheduling, this identity interacts with other services, preventing the above job execution failures.

.. note::

   During the periodic scheduling of a job, if the default user of the job is deleted and another user submits a version and schedules the job, the user who submits the version is considered as the executor of the job by default.

Classification of Scheduling Identities
---------------------------------------

Scheduling identities are classified into agencies and IAM accounts.

-  Agencies: Cloud services interwork with each other, and some cloud services are dependent on other services. You can create an agency to delegate cloud services to access other services and perform resource O&M on your behalf.

   Agencies are classified into the following types:

   -  Public agencies: They apply to all jobs in the workspace. For details about how to configure a public agency, see :ref:`Configuring a Public Agency <dataartsstudio_01_0555__section3485198599>`.
   -  Job agencies: They apply only to a single job. For details about how to configure a job agency, see :ref:`Configuring a Job-Level Agency <dataartsstudio_01_0555__section20224154881414>`.

-  IAM accounts: You can configure IAM accounts through user groups in a unified manner and manage permissions in an easier way than agencies. IAM accounts also have better compatibility and support MRS nodes (MRS Presto SQL, MRS Spark, MRS Spark Python, MRS Flink Job, and MRS MapReduce), directly connected nodes (MRS Spark SQL and MRS Hive SQL), and ETL Job nodes whose destination is DWS, so IAM accounts can be used to submit jobs for some MRS clusters and ETL Job nodes that cannot be submitted through agencies.

   IAM accounts are classified into the following types:

   -  Public IAM accounts: They apply to all jobs in the workspace. For details about how to configure a public IAM account, see :ref:`Configuring a Public IAM Account <dataartsstudio_01_0555__section11898926149>`.
   -  Execution users: They apply only to a single job. For details about how to configure an execution user, see :ref:`Configuring an Executor <dataartsstudio_01_0555__section177601853153314>`.

Priorities of Scheduling Identities
-----------------------------------

The system obtains permissions for the job agency, public agency, execution user, and public IAM account in sequence, and then executes jobs with the permissions.

By default, a job is executed by the user who starts the job. If a job is started by a user without the required permissions, the job fails to be executed due to insufficient permissions. You can configure a scheduling identity to resolve this issue.

Constraints
-----------

-  To create or modify an agency, you must have the **Security Administrator** permissions.
-  To configure a workspace-level scheduling identity, you must have the **DARTS Administrator** or **Tenant Administrator** policy.
-  To configure a job-level agency, you must have the permission to view the list of agencies.

.. _dataartsstudio_01_0555__section3485198599:

Configuring a Public Agency
---------------------------

.. caution::

   A public agency applies to all jobs in the workspace, especially those that contain MRS nodes. Exercise caution when performing this operation.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation pane, choose **Configuration** > **Configure**.

#. Choose **Scheduling Identities** and set **Public Scheduling Identity** to **Public agency**.

#. Click **+** to select an agency or create one. For how to create an agency and configure permissions, see :ref:`Reference: Creating an Agency <dataartsstudio_01_0555__section17505112912402>` and :ref:`Reference: Configuring Agency Permissions <dataartsstudio_01_0555__section1813152013116>`.


   .. figure:: /_static/images/en-us_image_0000002270790996.png
      :alt: **Figure 1** Configuring a workspace-level agency

      **Figure 1** Configuring a workspace-level agency

#. Click **OK** to return to the **Scheduling Identities** page and click |image1|.

   .. note::

      For a batch processing job, a public agency takes effect in the next cycle. For a real-time processing job, you must restart the job for a public agency to take effect.

.. _dataartsstudio_01_0555__section20224154881414:

Configuring a Job-Level Agency
------------------------------

.. note::

   You can create a job-level agency when creating a job. You can also modify the agency of an existing job.

**Configuring an agency when creating a job**

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation pane of the DataArts Factory homepage, choose **Development** > **Develop Job**.

#. Right-click the job directory and choose **Create Job** from the shortcut menu. The **Create Job** dialog box is displayed. If a workspace-level agency has been configured, it is used for the job by default. You can also select another agency from the agency list. For how to create an agency and configure permissions, see :ref:`Reference: Creating an Agency <dataartsstudio_01_0555__section17505112912402>` and :ref:`Reference: Configuring Agency Permissions <dataartsstudio_01_0555__section1813152013116>`.


   .. figure:: /_static/images/en-us_image_0000002305407745.png
      :alt: **Figure 2** Configuring an agency for a job

      **Figure 2** Configuring an agency for a job

   **Modifying the agency of an existing job**

#. In the navigation pane of the DataArts Factory homepage, choose **Development** > **Develop Job**.
#. In the job directory, double-click an existing job. On the far right of the displayed page, click **Basic Info**. The dialog box of the job's basic settings is displayed. If a workspace-level agency has been configured, it is used by default. You can also select another agency from the agency list.

.. _dataartsstudio_01_0555__section11898926149:

Configuring a Public IAM Account
--------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.
#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Scheduling Identities** and set **Public Scheduling Identity** to **Public IAM account**.
#. Enter the public IAM account in the text box.
#. Click |image2|.

.. _dataartsstudio_01_0555__section177601853153314:

Configuring an Executor
-----------------------

**Configuring a Job Executor**

#. In the job directory, double-click a job.
#. Click the **Basic Info** tab and set the executor for the job.

.. _dataartsstudio_01_0555__section17505112912402:

Reference: Creating an Agency
-----------------------------

#. Log in to the IAM console.
#. In the navigation pane, choose **Agencies** and click **Create** **Agency**.
#. Enter an agency name, for example, **DGC_agency**.
#. On the displayed page, select **Cloud service** for **Agency Type** and **Data Lake Governance Center (DGC)** for **Cloud Service**. This grants operation permissions to DataArts Studio so that DataArts Studio can use cloud services and perform O&M for you.
#. Click **Next**.
#. On the **Authorize Agency** page, search for and select the **Tenant Administrator** policy. Then click **Next**.

   -  Users assigned the **Tenant Administrator** policy have all permissions on all services except on IAMIAM. Therefore, delegate the **Tenant Administrator** policy to DataArts Studio so that DataArts Studio can access all related services.

   -  If you want to meet the security control requirements for fewer permissions, you only need to configure the **OBS OperateAccess** permissions (During job execution, execution log information needs to be written to OBS. Therefore, you need to add the **OBS OperateAccess** permissions.) Then, configure different agency permissions based on the node type in the job. For example, if a job contains only the **Import GES** node, you can configure the **GES Administrator** and **OBS OperateAccess** permissions. For details, see :ref:`Reference: Configuring Agency Permissions <dataartsstudio_01_0555__section1813152013116>`.


      .. figure:: /_static/images/en-us_image_0000002270847866.png
         :alt: **Figure 3** Assigning permissions

         **Figure 3** Assigning permissions

#. Click **OK**.

.. _dataartsstudio_01_0555__section1813152013116:

Reference: Configuring Agency Permissions
-----------------------------------------

After the operation permissions of an account are delegated to DataArts Studio, you must configure the permissions of the agency identity so that DataArts Studio can interact with other services.

For purposes of permissions minimization, you can configure the **Admin** permissions for services based on the node types in jobs. For details, see :ref:`Table 1 <dataartsstudio_01_0555__table18185359163814>`.

The **Admin** permissions can also be configured based on the operations, resources, and request conditions for a specific service. Based on the node types in jobs, permissions are defined by service APIs to allow for more fine-grained, secure access control of cloud resources. Configure the permissions according to :ref:`Table 2 <dataartsstudio_01_0555__table116756441498>`. For example, for a job containing the **Import GES** node, you only need to create a custom policy and select **ges:graph:getDetail** (viewing graph details), **ges:jobs:getDetail** (querying task status), and **ges:graph:access** (using graphs).

.. important::

   -  An MRS cluster supports job submission through an agency if either of the following conditions is met:

      -  It is a non-security cluster.
      -  It is a security cluster whose version is later than 2.1.0 and which has MRS 2.1.0.1 or later installed.

   -  If an MRS cluster does not support job submission through an agency, agencies cannot be configured for the jobs that contain the following nodes:

      MRS-related nodes (MRS Presto SQL, MRS Spark, MRS Spark Python, MRS Flink Job, and MRS MapReduce) and MRS Spark SQL and MRS Hive SQL nodes connected through APIs.

-  Configure the service-level **Admin** permissions.

   During job execution, execution log information needs to be written to OBS. Therefore, the **OBS** **OperateAccess** permissions must be added for all jobs during coarse-grained authorization.

.. _dataartsstudio_01_0555__table18185359163814:

.. table:: **Table 1** The admin permissions for related nodes

   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Node Name                                                                                           | System Permission           | Description                                                                                                                                                                               |
   +=====================================================================================================+=============================+===========================================================================================================================================================================================+
   | CDM Job                                                                                             | DARTS Administrator         | All DataArts Studio permissions                                                                                                                                                           |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Import GES                                                                                          | GES Administrator           | Permissions required to perform all operations on GES. This role depends on the **Tenant Guest** and **Server Administrator** roles in the same project.                                  |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | -  MRS Presto SQL, MRS Spark, MRS Spark Python, MRS Flink Job, and MRS MapReduce                    | MRS Administrator           | MRS Administrator: all execute permissions of MRS specified in the RBAC policy This role depends on the **Tenant Guest** and **Server Administrator** roles in the same project.          |
   | -  MRS Spark SQL and MRS Hive SQL (connecting to MRS clusters through MRS APIs)                     |                             |                                                                                                                                                                                           |
   |                                                                                                     | MRS Fullaccess              | MRS Fullaccess: MRS administrator permission specified in the fine-grained policy                                                                                                         |
   |                                                                                                     |                             |                                                                                                                                                                                           |
   |                                                                                                     | KMS Administrator           | Users assigned the **KMS Administrator** role have the administrator permissions for encryption keys in DEW.                                                                              |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | MRS Spark SQL, MRS Hive SQL, MRS Kafka, and Kafka Client (connecting to the clusters in proxy mode) | DARTS Administrator         | **DARTS Administrator** has all permissions required for DataArts Studio.                                                                                                                 |
   |                                                                                                     |                             |                                                                                                                                                                                           |
   |                                                                                                     | KMS Administrator           | Users assigned the **KMS Administrator** policy have the administrator permissions for encryption keys in DEW.                                                                            |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DLI Flink Job, DLI SQL, and DLI Spark                                                               | DLI Service Admin           | All operation permissions for DLI.                                                                                                                                                        |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DWS SQL, RDS SQL (connecting to data sources in proxy mode), and Shell                              | DARTS Administrator         | **DARTS Administrator** has all permissions required for DataArts Studio.                                                                                                                 |
   |                                                                                                     |                             |                                                                                                                                                                                           |
   |                                                                                                     | KMS Administrator           | Users assigned the **KMS Administrator** policy have the administrator permissions for encryption keys in DEW.                                                                            |
   +-----------------------------------------------------------------------------------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CSS                                                                                                 | DARTS Administrator         | **DARTS Administrator** has all permissions required for DataArts Studio.                                                                                                                 |
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

.. |image1| image:: /_static/images/en-us_image_0000002270791012.png
.. |image2| image:: /_static/images/en-us_image_0000002270847842.png
