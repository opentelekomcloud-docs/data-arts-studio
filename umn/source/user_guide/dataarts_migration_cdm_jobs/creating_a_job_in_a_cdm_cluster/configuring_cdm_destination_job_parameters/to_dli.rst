:original_name: dataartsstudio_01_0072.html

.. _dataartsstudio_01_0072:

To DLI
======

If the destination link of a job is a :ref:`DLI link <dataartsstudio_01_0036>`, configure the destination job parameters based on :ref:`Table 1 <dataartsstudio_01_0072__en-us_topic_0108275441_table5046103815165>`.

.. caution::

   When data is migrated to DLI using CDM, DLI generates data files in the *dli-trans\** temporary OBS bucket. Therefore, you need to grant the user who uses the AK/SK the permissions to read and write the *dli-trans\** bucket and create directories. Otherwise, the migration will fail. For details about how to add permission policies for temporary bucket *dli-trans\**, see :ref:`Adding an Authorization Policy for the dli-trans* Temporary Bucket <dataartsstudio_01_0072__en-us_topic_0108275441_section4208185214711>`.

.. _dataartsstudio_01_0072__en-us_topic_0108275441_table5046103815165:

.. table:: **Table 1** Parameter description

   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Parameter                     | Description                                                                                                                    | Example Value          |
   +===============================+================================================================================================================================+========================+
   | Resource Queue                | Resource queue to which the destination table belongs                                                                          | cdm                    |
   |                               |                                                                                                                                |                        |
   |                               | The default queue of DLI cannot be used for migration jobs. You need to create a SQL queue in DLI.                             |                        |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Database Name                 | Name of the database to which data will be written                                                                             | dli                    |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Table Name                    | Name of the table to which data will be written                                                                                | car_detail             |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Clear Data Before Import      | Whether to clear data in the destination table before data import                                                              | No                     |
   |                               |                                                                                                                                |                        |
   |                               | If this parameter is set to **Yes**, data in the destination table will be cleared before the task is started.                 |                        |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Convert empty strings to null | If this parameter is set to **Yes**, an empty string is regarded as null.                                                      | No                     |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Data Clearing Mode            | This parameter is available when **Clear Data Before Import** is set to **Yes**.                                               | TRUNCATE               |
   |                               |                                                                                                                                |                        |
   |                               | **TRUNCATE**: deletes standard data.                                                                                           |                        |
   |                               |                                                                                                                                |                        |
   |                               | **INSERT_OVERWRITE**: overwrites existing data with inserted data.                                                             |                        |
   |                               |                                                                                                                                |                        |
   |                               | .. note::                                                                                                                      |                        |
   |                               |                                                                                                                                |                        |
   |                               |    If the source link is a Kafka link and **Clear Data Before Import** is set to **Yes**, **INSERT_OVERWRITE** is unavailable. |                        |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Partition                     | This parameter is available when **Clear Data Before Import** is set to **Yes**.                                               | year=2020,location=sun |
   |                               |                                                                                                                                |                        |
   |                               | When you enter partitions, data in these partitions will be cleared.                                                           |                        |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+

.. _dataartsstudio_01_0072__en-us_topic_0108275441_section4208185214711:

Adding an Authorization Policy for the *dli-trans\** Temporary Bucket
---------------------------------------------------------------------

#. Log in to the IAM console.

#. In the navigation pane, choose **Permissions** > **Policies/Roles** and click **Create Custom Policy** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000002269114785.png
      :alt: **Figure 1** Creating a custom policy

      **Figure 1** Creating a custom policy

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
      :alt: **Figure 2** Creating custom policy **obs\_dli-trans**

      **Figure 2** Creating custom policy **obs\_dli-trans**

#. Click **OK**.

#. In the navigation pane, choose **User Groups**, locate the user group to which the DLI link user using the AK/SK belongs, and click **Authorize** to assign the custom **obs\_dli-trans** policy to the user.


   .. figure:: /_static/images/en-us_image_0000002269114801.png
      :alt: **Figure 3** Assigning the custom **obs\_dli-trans** policy to a user group

      **Figure 3** Assigning the custom **obs\_dli-trans** policy to a user group
