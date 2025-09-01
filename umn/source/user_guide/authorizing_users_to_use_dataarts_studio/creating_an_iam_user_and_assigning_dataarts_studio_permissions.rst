:original_name: dataartsstudio_01_0004.html

.. _dataartsstudio_01_0004:

Creating an IAM User and Assigning DataArts Studio Permissions
==============================================================

Identity and Access Management (IAM) can be used for fine-grained permissions management on your DataArts Studio resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing DataArts Studio resources.
-  Grant users only the permissions required to perform a given task based on their job responsibilities.
-  Entrust a cloud account or cloud service to perform efficient O&M on your DataArts Studio resources.

If you do not require individual IAM users for permissions management, skip this topic.

This section describes the procedure for granting permissions. See :ref:`Procedure <dataartsstudio_01_0004__en-us_topic_0223009156_section9135134520119>` for details.

Context
-------

-  Before assigning permissions to a user group, you need to understand the permission system of so that you can select the permissions that meet your needs.


   .. figure:: /_static/images/en-us_image_0000002391028724.png
      :alt: **Figure 1** Permission system

      **Figure 1** Permission system

Notes and Constraints
---------------------

-  The DARTS User system role provides the permissions related to instances, workspaces, and dependent services. The operation permissions in workspaces are provided by workspace roles.

-  IAM provides the following two authorization mechanisms: Note that DataArts Studio supports only the IAM role-based authorization and does not support the IAM policy-based authorization.

   -  **IAM Roles**: IAM initially provides a coarse-grained authorization mechanism to define permissions based on users' job responsibilities. Only a limited number of service-level roles are available. However, traditional IAM roles are not an ideal choice for fine-grained authorization and secure access control.
   -  **IAM Policies**: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This type of authorization is more flexible and is ideal for least privilege access.

.. _dataartsstudio_01_0004__en-us_topic_0223009156_section9135134520119:

Procedure
---------

#. .. _dataartsstudio_01_0004__li39771248101915:

   Create a user group and assign a system role to the group.

   Log in to the IAM console using a cloud account, create a user group and assign a DataArts Studio system role to the group. For example, the system role can be DARTS Administrator or DARTS User.

   For details, see "User Groups and Authorization" > "Creating a User Group and Assigning Permissions" in *Identity and Access Management User Guide*.

   .. note::

      -  When configuring DataArts Studio permissions for a user group, enter **DARTS** in the search box to search for the permissions and select the permissions to be granted to the user group, for example, **DARTS User**.
      -  DataArts Studio is a project-level service deployed in specific physical regions. If you select **All resources** for **Scope**, the permission takes effect in all projects of all regions. If you select **Region-specific projects** for **Scope**, the permission takes effect only for a specified project. When accessing DataArts Studio, the IAM user must switch to the region where they have been assigned the required permissions.

#. Create a user and add the user to the user group.

   Create users on the IAM console and add them to the group created in :ref:`Step 1 <dataartsstudio_01_0004__li39771248101915>`.

   For details, see "IAM Users" > "Creating an IAM User" in *Identity and Access Management User Guide*.

   .. note::

      An IAM user can pass the authentication and access DataArts Studio through an API or SDK only if **Programmatic access** is selected for **Access Type** during the creation of the IAM user.

#. Create a custom workspace role for DARTS User, add it as a workspace member, and assign a role to the member.

   DataArts Studio workspace roles determine the permissions of DARTS User in a workspace. There are five preset roles: admin, developer, deployer, operator, and viewer. If these preset roles can meet your requirements, you do not need to create a custom workspace role. Instead, you can add the user as a workspace member and assign a preset role to the member. Otherwise, you need to create a custom role, add the users as a workspace member, and assign a custom role to the member. For details about how to create a custom workspace role, see :ref:`(Optional) Defining a Workspace Role <dataartsstudio_01_0107>`\ For details about how to add a workspace member and assign a role, see :ref:`Adding Workspace Members and Assigning Roles <dataartsstudio_01_0117>`.

   For details about the permissions of the roles, see "Permissions" in *Service Overview*.

#. Log in to the console and verify permissions.

   Log in to the console using the created user and verify permissions of the user.

   -  Choose **Service List** > **DataArts Studio**. Locate a DataArts Studio instance and click **Access**. Check whether the workspace list is displayed.
   -  Access a service module (for example, Management Center) to which your current user has been added and check whether you can perform the operations allowed for the workspace role assigned to you.
