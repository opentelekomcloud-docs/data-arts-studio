:original_name: dataartsstudio_02_0006.html

.. _dataartsstudio_02_0006:

Concepts
========

-  Domain

   A domain has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions. The domain should not be used directly to perform routine management. For security purposes, create users and grant them permissions for routine management.

-  User

   A user is created in Identity and Access Management (IAM) to use cloud services. Each user has its own identity credentials (password and access keys).

   You can view the account ID and user ID in :ref:`Project ID and Account ID <projectid_accountid>`. The domain name, username, and password will be required for API authentication.

-  Project

   A project corresponds to a region. Projects group and isolate resources (including compute, storage, and network resources) across physical regions. Users can be granted permissions in a default project to access all resources in the region associated with the project. If you want more refined access control, create subprojects under a project and create resources in the subprojects. Then, grant users the permissions to access only specific resources in the subprojects.


   .. figure:: /_static/images/en-us_image_0000002234266862.png
      :alt: **Figure 1** Project isolating model

      **Figure 1** Project isolating model
