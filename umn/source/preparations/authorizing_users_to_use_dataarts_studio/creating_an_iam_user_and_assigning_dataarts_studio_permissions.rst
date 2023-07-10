:original_name: dataartsstudio_01_0004.html

.. _dataartsstudio_01_0004:

Creating an IAM User and Assigning DataArts Studio Permissions
==============================================================

Identity and Access Management (IAM) can be used for fine-grained permissions management on your DataArts Studio resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing DataArts Studio resources.
-  Assign users only the permissions required to perform a task.
-  Entrust a cloud platform account or cloud service to perform efficient O&M on your DataArts Studio resources.

If you do not require individual IAM users for permissions management, skip this section.

Background
----------

-  Before assigning permissions to a user group, familiarize yourself with the DataArts Studio workspace role permissions that can be added to the user group and select permissions based on actual requirements.

Procedure
---------

#. .. _dataartsstudio_01_0004__en-us_topic_0223009156_li1983016328204:

   Create a user group and assign permissions to it. Log in to the IAM console using a cloud platform account, create a user group, and grant permissions of a common user (for example, **DAYU User**) to the group.

   For details, see "User Groups and Authorization" > "Creating a User Group and Assigning Permissions" in *Identity and Access Management User Guide*.

   .. note::

      -  When configuring DataArts Studio permissions for a user group, enter **DAYU** in the search box to search for the permissions and select the permissions to be granted to the user group, for example, **DAYU User**.
      -  If an IAM user wants to create a workspace, you must assign the IAM user the **DAYU Administrator** policy. Users with the **DAYU Administrator** policy can perform all operations on DataArts Studio.
      -  DataArts Studio is a project-level service deployed in specific physical regions. If you select **All resources** for **Scope**, the permission takes effect in all projects of all regions. If you select **Region-specific projects** for **Scope**, the permission takes effect only for a specified project. When accessing DataArts Studio, the IAM user must switch to the region where they have been assigned the required permissions.

#. Create a user and add the user to the user group. Create a user on the IAM console and add the user to the group created in :ref:`1 <dataartsstudio_01_0004__en-us_topic_0223009156_li1983016328204>`.

   For details, see "IAM Users" > "Creating an IAM User" in *Identity and Access Management User Guide*.
