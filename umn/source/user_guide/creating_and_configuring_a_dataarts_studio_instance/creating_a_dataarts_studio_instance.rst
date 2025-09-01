:original_name: dataartsstudio_01_0115.html

.. _dataartsstudio_01_0115:

Creating a DataArts Studio Instance
===================================

Context
-------

-  Only users with **DARTS** **Administrator** or **Tenant Administrator** permissions can create DataArts Studio instances or incremental packages.

   .. note::

      Users with **Tenant Administrator** permissions can perform all operations except IAM user management. For security purposes, you are not advised to grant **Tenant Administrator** permissions to IAM users.

-  Only users with **Security Administrator** permissions can create cloud service agencies. Cloud service agencies allow DataArts Studio to perform operations such as task scheduling and resource O&M on other cloud services on your behalf.

Prerequisites
-------------

You have obtained a VPC, subnet, and security group. You can also apply for them when you create a DataArts Studio instance.

Logging In to the DataArts Studio Console
-----------------------------------------

#. Log in to the cloud console.
#. In the upper left corner of the console, click |image1|, and choose to access the DataArts Studio console.

create a DataArts Studio Basic Package
--------------------------------------

#. On the DataArts Studio console, click **create Instance**.

#. On the displayed page, set the parameters listed in :ref:`Table 1 <dataartsstudio_01_0115__en-us_topic_0196002071_table19841917172111>`.

   .. _dataartsstudio_01_0115__en-us_topic_0196002071_table19841917172111:

   .. table:: **Table 1** DataArts Studio instance parameters

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Example Value         | Description                                                                                                                                                                                                                                                                                                                                             |
      +=======================+=======================+=========================================================================================================================================================================================================================================================================================================================================================+
      | Region                | N/A                   | Region where the instance resides. Resources in different regions cannot communicate with each other.                                                                                                                                                                                                                                                   |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project    | default               | Enterprise project associated with the default workspace of the DataArts Studio instance.                                                                                                                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                         |
      |                       |                       | This parameter is available only when an enterprise project has been created. If you want to connect the DataArts Studio instance to an instance of another cloud service, such as GaussDB(DWS), MRS, and RDS, ensure that the enterprise project of the DataArts Studio instance's workspace is the same as that of the target cloud service instance. |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                         |
      |                       |                       | -  You can create only one DataArts Studio instance for an enterprise project.                                                                                                                                                                                                                                                                          |
      |                       |                       | -  If you want to enable communication between DataArts Studio and another cloud service, ensure that the enterprise project of DataArts Studio is the same as that of the target cloud service.                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                         |
      |                       |                       | .. note::                                                                                                                                                                                                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                         |
      |                       |                       |    If the enterprise project function is not enabled, only one DataArts Studio instance can be created for each IAM project.                                                                                                                                                                                                                            |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Instance Name         | DataArts Studio-test  | Name of the DataArts Studio instance. After the instance is created, its name cannot be changed.                                                                                                                                                                                                                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Confirm the settings and click **create Now**.

#. When you return to the DataArts Studio console, the **Authorize Access** dialog box is displayed, prompting you to authorize the listed services. DataArts Studio interacts with these cloud services. You must create a cloud service agency to delegate permissions to DataArts Studio so that DataArts Studio can use these cloud services and perform task scheduling and resource O&M on your behalf.

   .. important::

      Only users with **Security Administrator** permissions can create cloud service agencies. Cloud service agencies allow DataArts Studio to perform operations such as task scheduling and resource O&M on other cloud services on your behalf.

   Cloud service agencies include permissions related to DWS, MRS, RDS, OBS, SMN, and KMS. You can access the IAM agency page to view the agency scope. You do not need to apply for an agency for users. The agency of the account is used.

   Select all services and click **Authorize**. The system automatically creates the default dlg_agency.

   -  After the authorization is complete, the **Authorize Access** dialog box will not be displayed when you access the DataArts Studio console homepage next time.
   -  If you select only some services for authorization, this dialog box will be displayed again next time you access the DataArts Studio console, prompting you to authorize access to the unauthorized cloud services.

#. In the list of instances, locate your instance and click **Access** to access the DataArts Studio console.

.. |image1| image:: /_static/images/en-us_image_0000002269119541.png
