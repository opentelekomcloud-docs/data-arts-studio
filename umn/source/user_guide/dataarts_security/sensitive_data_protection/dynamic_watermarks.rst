:original_name: dataartsstudio_01_1039.html

.. _dataartsstudio_01_1039:

Dynamic Watermarks
==================

Dynamic watermarking means dynamically inserting watermarks into the result sets returned by data query and access requests. This section describes how to enable dynamic watermarking for DataArts Factory so that data watermarks can be dynamically inserted during the dump or download of sensitive data in DataArts Factory.

After data development dynamic watermarking is enabled for DataArts Security and a dynamic watermarking policy is created, when a user group or role specified in the policy dumps or downloads sensitive data in DataArts Factory, DataArts Factory injects an invisible watermark into the sensitive data to protect it from being disclosed.

.. note::

   The invisible watermark is the first 16 digits of the IAM user ID of the user who obtains sensitive data. To obtain the user ID, perform the following steps:

   #. Register with and log in to the management console.
   #. Hover the cursor on the username in the upper right corner and select **My Credentials** from the drop-down list.
   #. On the **API Credentials** page, obtain the account name, account ID, IAM username, and IAM user ID, and obtain the project and its ID from the project list.

Note that dynamic watermarking policies configured for a DataArts Studio instance are visible to and take effect for all the workspaces of the instance.

Prerequisites
-------------

An MRS Hive or MRS Spark connection has been created.

Constraints
-----------

-  Only the DARTS Administrator, Tenant Administrator, or data security administrator can enable or disable dynamic watermarking for DataArts Factory. The workspace administrator can create dynamic watermarking policies. Other common users do not have the permission to perform these operations.
-  Dynamic watermarking policies are only available for MRS Hive and MRS Spark data sources.
-  Adding, deleting, or modifying a dynamic watermarking policy takes about five minutes to take effect.
-  A watermark will be inserted only when more than 500 rows of data are to be dumped or downloaded. If there are less than 500 rows of data, source tracing will be impossible even if a watermark is inserted.

Creating a Dynamic Watermarking Policy
--------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **Dynamic Watermarking**.


   .. figure:: /_static/images/en-us_image_0000002269198593.png
      :alt: **Figure 1** Accessing the Dynamic Watermarking page

      **Figure 1** Accessing the Dynamic Watermarking page

#. Click |image1| to enable dynamic watermarking for DataArts Factory. Click **Create** and set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1039__en-us_topic_0000001629912500_table99188713455>`.


   .. figure:: /_static/images/en-us_image_0000002269118513.png
      :alt: **Figure 2** Setting parameters for the dynamic watermarking policy

      **Figure 2** Setting parameters for the dynamic watermarking policy

   The following table lists the parameters.

   .. _dataartsstudio_01_1039__en-us_topic_0000001629912500_table99188713455:

   .. table:: **Table 1** Policy parameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================================+
      | \*Policy Name                     | Unique identifier of the dynamic watermarking policy. It must be unique in a DataArts Studio instance.                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                            |
      |                                   | To facilitate policy management, you are advised to include the object to be watermarked and the watermark to be added in the name.                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | User Group/Role                   | User, user group, or role in the current workspace members. When a specified object queries or exports sensitive data from DataArts Factory, the system adds a dynamic watermark to the sensitive data to protect the sensitive data from being disclosed. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Source Type                | Select **MRS Hive** or **MRS Spark**.                                                                                                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Connection                 | If no data connection is available, create one by referring to :ref:`Creating a DataArts Studio Data Connection <dataartsstudio_01_1299>`.                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Cluster Name                    | You do not need to set this parameter. The data source cluster in the data connection is automatically selected.                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Database                        | Databases where the sensitive data is stored.                                                                                                                                                                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Table                      | Tables where the sensitive data is stored. You need to set one of the following table selection modes:                                                                                                                                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After setting all required parameters, click **OK**.

Related Operations
------------------

-  Extracting a watermark: After obtaining the CSV data file containing a dynamic watermark from DataArts Factory, trace the watermark by referring to :ref:`Extracting a Watermark <dataartsstudio_01_1038__en-us_topic_0000001629752668_section23271629153418>`.

-  Editing a policy: On the **Dynamic Watermarking** page, locate a policy and click **Edit** in the **Operation** column.

-  Setting the policy status: A watermarking policy is enabled by default. If the watermarking policy is disabled, it does not take effect.

   To change the status of a watermarking policy, click |image2| or |image3| to enable or disable the policy.

-  Deleting policies: On the **Dynamic Watermarking** page, locate a policy and click **Delete** in the **Operation** column. To delete multiple policies, select them and click **Delete** above the list.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.

-  Viewing policy details: On the **Dynamic Watermarking** page, locate a policy and click its name to view its details.


   .. figure:: /_static/images/en-us_image_0000002234239156.png
      :alt: **Figure 3** Viewing policy details

      **Figure 3** Viewing policy details

.. |image1| image:: /_static/images/en-us_image_0000002234239164.png
.. |image2| image:: /_static/images/en-us_image_0000002269198617.png
.. |image3| image:: /_static/images/en-us_image_0000002234239172.png
