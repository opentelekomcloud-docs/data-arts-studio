:original_name: dataartsstudio_01_0115_0.html

.. _dataartsstudio_01_0115_0:

Creating a DataArts Studio Basic Package
========================================

Background
----------

Only a cloud platform account users with the **DAYU Administrator** or **Tenant Administrator** permissions can create DataArts Studio instances or DataArts Studio incremental packages.

.. note::

   Users with the **Tenant Administrator** permissions can perform all operations except IAM user management. For security purposes, you are not advised to grant the **Tenant Administrator** permissions to IAM users.

Prerequisites
-------------

You have obtained a VPC, subnet, and security group. You can also apply for them when you create a DataArts Studio instance.

Logging In to DataArts Studio Console
-------------------------------------

#. Log in to the cloud management console.
#. In the upper left corner of the console, click |image1|, and choose **DataArts Studio** to access the DataArts Studio console.


Creating a DataArts Studio Basic Package
----------------------------------------

#. On the DataArts Studio console, click **Create Instance**.

#. On the displayed page, set parameters for the DataArts Studio instance. :ref:`Table 1 <dataartsstudio_01_0115_0__en-us_topic_0196002071_table19841917172111>` provides descriptions of the parameters.

   .. _dataartsstudio_01_0115_0__en-us_topic_0196002071_table19841917172111:

   .. table:: **Table 1** DataArts Studio instance parameters

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Example               | Description                                                                                                                                                                                                                                                                                             |
      +=======================+=======================+=========================================================================================================================================================================================================================================================================================================+
      | Region                | None                  | The region where the instance resides. Resources in different regions cannot communicate with each other.                                                                                                                                                                                               |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project    | default               | The enterprise project associated with your DataArts Studio instance.                                                                                                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                                                                                         |
      |                       |                       | This parameter is available only when an enterprise project has been created. If you want to connect the DataArts Studio instance to a cloud service (such as DWS, MRS, and RDS), ensure that the enterprise project of the DataArts Studio instance is the same as that of the cloud service instance. |
      |                       |                       |                                                                                                                                                                                                                                                                                                         |
      |                       |                       | -  You can create only one DataArts Studio instance for an enterprise project.                                                                                                                                                                                                                          |
      |                       |                       | -  If you want to enable communication between DataArts Studio and another cloud service, ensure that the enterprise project of DataArts Studio is the same as that of the cloud service.                                                                                                               |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Instance Name         | DataArts Studio-test  | Name of the DataArts Studio instance                                                                                                                                                                                                                                                                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. (Optional) If you have set a tag key and a tag value, click **Add** to add the tag.

   .. note::

      -  A maximum of 20 tags can be added.
      -  Only one tag value can be added to a tag key.
      -  The key name must be unique in the same instance.

#. Confirm the settings and click **create Now**.

#. When you return to the DataArts Studio management console, the **Authorize Access** dialog box is displayed, prompting you to authorize the listed services. DataArts Studio interacts with the cloud services and needs to collaborate with them. Therefore, you need to create a cloud service agency to delegate permissions to DataArts Studio so that DataArts Studio can use these cloud services and perform task scheduling and resource O&M on behalf of you.

   Cloud service agencies include permissions related to DWS, MRS, RDS, OBS, SMN, and KMS. You can access the IAM agency page to view the agency scope. You do not need to apply for an agency for users. The agency of the account is used.

   Select all services and click **Authorize**. The platform automatically creates an agency.

   -  After the authorization is complete, the **Authorize Access** dialog box will not be displayed when you access the DataArts Studio console homepage next time.
   -  If you select only some services for authorization, the system still displays the dialog box next time you access the DataArts Studio console homepage, prompting you to authorize access to unauthorized cloud services.

#. In the list of instances, locate your instance and click **Access** to access the DataArts Studio console.

.. |image1| image:: /_static/images/en-us_image_0000001373088373.png
