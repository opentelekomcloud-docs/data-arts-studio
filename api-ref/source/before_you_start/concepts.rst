:original_name: dataartsstudio_02_0006.html

.. _dataartsstudio_02_0006:

Concepts
========

-  Domain

   A domain is created upon successful registration. The domain has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant users permissions. The account should not be used directly to perform routine management. For security purposes, create users and grant them permissions for routine management.

-  User

   A user is created in Identity and Access Management (IAM) to use cloud services. Each user has its own identity credentials (password and access keys).

   You can view the account ID and user ID in :ref:`Project ID and Account ID <projectid_accountid>`. The account name, username, and password will be required for API authentication.

-  Project

   Projects group and isolate resources (including compute, storage, and network resources) across physical regions. A default project is provided for each region, and subprojects can be created under each default project. Users can be granted permissions to access all resources in a specific project. If you want more refined access control, create subprojects under a project and create resources in the subprojects. Then, grant users the permissions to access only specific resources in the subprojects.


   .. figure:: /_static/images/en-us_image_0000001828945753.png
      :alt: **Figure 1** Project isolating model

      **Figure 1** Project isolating model
