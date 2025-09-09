:original_name: dataartsstudio_01_0036.html

.. _dataartsstudio_01_0036:

DLI Link Parameters
===================

When connecting CDM to DLI, configure the parameters as described in :ref:`Table 1 <dataartsstudio_01_0036__en-us_topic_0108275410_table22075105144748>`.

.. note::

   -  Do not change the password or user when the job is running. If you do so, the password will not take effect immediately and the job will fail.

   -  When data is migrated to DLI, DLI generates data files in the *dli-trans\** temporary OBS bucket. Therefore, you need to grant the user who uses the AK/SK the permissions to read and write the *dli-trans\** bucket and create directories. Otherwise, the migration will fail. For details about how to add permission policies for temporary bucket *dli-trans\**, see :ref:`Adding an Authorization Policy for the dli-trans* Temporary Bucket <dataartsstudio_01_0036__en-us_topic_0108275410_section103343291605>`.

.. _dataartsstudio_01_0036__en-us_topic_0108275410_table22075105144748:

.. table:: **Table 1** DLI link parameters

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                                                                                                                                                          | Example Value         |
   +=======================+======================================================================================================================================================================================================================================================+=======================+
   | Name                  | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                                                                                   | dli_link              |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | AK                    | AK/SK required for authentication during access to the DLI database.                                                                                                                                                                                 | ``-``                 |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       | You need to create an access key for the current account and obtain an AK/SK pair.                                                                                                                                                                   |                       |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       | #. Log in to the management console, move the cursor to the username in the upper right corner, and select **My Credentials** from the drop-down list.                                                                                               |                       |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       | #. On the **My Credentials** page, choose **Access Keys**, and click **Create Access Key**. See :ref:`Figure 1 <dataartsstudio_01_0036__en-us_topic_0108275410_en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615>`.               |                       |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       |    .. _dataartsstudio_01_0036__en-us_topic_0108275410_en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615:                                                                                                                          |                       |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       |    .. figure:: /_static/images/en-us_image_0000002269194761.png                                                                                                                                                                                      |                       |
   |                       |       :alt: **Figure 1** Clicking Create Access Key                                                                                                                                                                                                  |                       |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       |       **Figure 1** Clicking Create Access Key                                                                                                                                                                                                        |                       |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       | #. Click **OK** and save the access key file as prompted. The access key file will be saved to your browser's configured download location. Open the **credentials.csv** file to view **Access Key Id** and **Secret Access Key**.                   |                       |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       |    .. note::                                                                                                                                                                                                                                         |                       |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       |       -  Only two access keys can be added for each user.                                                                                                                                                                                            |                       |
   |                       |       -  To ensure access key security, the access key is automatically downloaded only when it is generated for the first time and cannot be obtained from the management console later. Keep them properly.                                        |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | SK                    |                                                                                                                                                                                                                                                      | ``-``                 |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Project ID            | Project ID in the region where DLI resides                                                                                                                                                                                                           | ``-``                 |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       | A project is a group of tenant resources, and an account ID corresponds to the current account. The IAM ID corresponds to the current user. You can view the project IDs, account IDs, and user IDs in different regions on the corresponding pages. |                       |
   |                       |                                                                                                                                                                                                                                                      |                       |
   |                       | #. Register with and log in to the management console.                                                                                                                                                                                               |                       |
   |                       | #. Hover the cursor on the username in the upper right corner and select **My Credentials** from the drop-down list.                                                                                                                                 |                       |
   |                       | #. On the **API Credentials** page, obtain the account name, account ID, IAM username, and IAM user ID, and obtain the project and its ID from the project list.                                                                                     |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Batch Size            | Number of rows written each time. When the number of rows written reaches the value of **Commit Size**, the rows will be committed to the database.                                                                                                  | 50000                 |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

.. _dataartsstudio_01_0036__en-us_topic_0108275410_section103343291605:

Adding an Authorization Policy for the *dli-trans\** Temporary Bucket
---------------------------------------------------------------------

#. Log in to the IAM console.

#. In the navigation pane, choose **Permissions** > **Policies/Roles** and click **Create Custom Policy** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000002269114785.png
      :alt: **Figure 2** Creating a custom policy

      **Figure 2** Creating a custom policy

#. On the **Create Custom Policy** page, select **JSON** for **Policy View** and create custom policy **obs\_dli-trans**.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:object:GetObject",
                      "obs:object:DeleteObjectVersion",
                      "obs:bucket:GetBucketLocation",
                      "obs:object:GetAccessLabel",
                      "obs:bucket:PutEncryptionConfiguration",
                      "obs:bucket:PutBucketStoragePolicy",
                      "obs:object:DeleteAccessLabel",
                      "obs:bucket:PutBucketCustomDomainConfiguration",
                      "obs:bucket:GetLifecycleConfiguration",
                      "obs:bucket:PutBucketInventoryConfiguration",
                      "obs:bucket:DeleteDirectColdAccessConfiguration",
                      "obs:object:AbortMultipartUpload",
                      "obs:bucket:PutBucketLogging",
                      "obs:bucket:DeleteBucketWebsite",
                      "obs:object:DeleteObject",
                      "obs:bucket:PutBucketVersioning",
                      "obs:bucket:GetBucketWebsite",
                      "obs:bucket:GetBucketLogging",
                      "obs:bucket:DeleteBucketCustomDomainConfiguration",
                      "obs:object:PutObject",
                      "obs:object:RestoreObject",
                      "obs:bucket:PutReplicationConfiguration",
                      "obs:bucket:GetBucketQuota",
                      "obs:object:GetObjectVersionAcl",
                      "obs:bucket:DeleteBucket",
                      "obs:bucket:CreateBucket",
                      "obs:bucket:GetDirectColdAccessConfiguration",
                      "obs:bucket:PutDirectColdAccessConfiguration",
                      "obs:bucket:GetBucketAcl",
                      "obs:bucket:GetBucketVersioning",
                      "obs:bucket:GetBucketInventoryConfiguration",
                      "obs:bucket:GetBucketStoragePolicy",
                      "obs:bucket:GetEncryptionConfiguration",
                      "obs:bucket:PutBucketCORS",
                      "obs:bucket:PutBucketTagging",
                      "obs:bucket:GetBucketTagging",
                      "obs:bucket:PutLifecycleConfiguration",
                      "obs:bucket:GetBucketCustomDomainConfiguration",
                      "obs:object:ListMultipartUploadParts",
                      "obs:object:ModifyObjectMetaData",
                      "obs:bucket:ListBucketVersions",
                      "obs:bucket:PutBucketQuota",
                      "obs:object:PutAccessLabel",
                      "obs:bucket:ListBucket",
                      "obs:bucket:GetBucketCORS",
                      "obs:bucket:DeleteBucketInventoryConfiguration",
                      "obs:object:GetObjectVersion",
                      "obs:bucket:PutBucketWebsite",
                      "obs:bucket:DeleteReplicationConfiguration",
                      "obs:object:GetObjectAcl",
                      "obs:bucket:GetBucketNotification",
                      "obs:bucket:PutBucketNotification",
                      "obs:bucket:GetReplicationConfiguration",
                      "obs:bucket:GetBucketPolicy",
                      "obs:bucket:DeleteBucketTagging",
                      "obs:bucket:GetBucketStorage"
                  ],
                  "Resource": [
                      "OBS:*:*:object:*",
                      "OBS:*:*:bucket:dli-trans*"
                  ]
              }
          ]
      }


   .. figure:: /_static/images/en-us_image_0000002234075564.png
      :alt: **Figure 3** Creating custom policy **obs\_dli-trans**

      **Figure 3** Creating custom policy **obs\_dli-trans**

#. Click **OK**.

#. In the navigation pane, choose **User Groups**, locate the user group to which the DLI link user using the AK/SK belongs, and click **Authorize** to assign the custom **obs\_dli-trans** policy to the user.


   .. figure:: /_static/images/en-us_image_0000002269114801.png
      :alt: **Figure 4** Assigning the custom **obs\_dli-trans** policy to a user group

      **Figure 4** Assigning the custom **obs\_dli-trans** policy to a user group
