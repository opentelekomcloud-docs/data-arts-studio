:original_name: dataartsstudio_01_5100.html

.. _dataartsstudio_01_5100:

Service Process in Enterprise Mode
==================================

The DataArts Studio enterprise mode mainly involves the Management Center and DataArts Factory components. The service process is completed by the admin, developer, deployer, and operator.


.. figure:: /_static/images/en-us_image_0000002234077672.png
   :alt: **Figure 1** Enterprise mode architecture

   **Figure 1** Enterprise mode architecture

-  The admin performs operations such as preparing a data lake, configuring data connections and environment isolation, importing and exporting data, and configuring project user permissions.
-  The developer develops and tests scripts and jobs, and submits versions and release tasks in the development environment.
-  The deployer reviews the submitted tasks in the development environment.
-  The operator performs operations such as job monitoring, notification management, and backup in the production environment based on the resources released by the developer.
-  Custom role: You can customize operation permissions to meet your requirements.
-  The viewer can only read data from DataArts Studio, but cannot perform operations or modify work items or configurations. You are advised to assign this role to users who only want to view information in the workspace.

   .. table:: **Table 1** Permissions of different roles

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Role                  | Simple Workspace                                                                                                                       | Enterprise Workspace                                                                                                       |
      +=======================+========================================================================================================================================+============================================================================================================================+
      | Admin                 | Has all permissions of Management Center in the production environment, including connection configuration and data import and export. | -  Deployment-related operations                                                                                           |
      |                       |                                                                                                                                        | -  Connection configuration, environment isolation configuration, and data import and export in Management Center          |
      |                       |                                                                                                                                        | -  Configuration in DataArts Factory, such as the environment, scheduling identity, and default item configuration         |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Developer             | Has all permissions to develop jobs and scripts in the production environment.                                                         | -  Development environment: all permissions                                                                                |
      |                       |                                                                                                                                        | -  Production environment: read-only permission                                                                            |
      |                       |                                                                                                                                        | -  Deployment: packaging and viewing release items, viewing the release item list, and viewing the release package content |
      |                       |                                                                                                                                        | -  Environment information configuration: read-only permission                                                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Deployer              | None                                                                                                                                   | -  Viewing release packages                                                                                                |
      |                       |                                                                                                                                        | -  Viewing the release item list                                                                                           |
      |                       |                                                                                                                                        | -  Releasing packages: Only the deployer and admin can perform this operation.                                             |
      |                       |                                                                                                                                        | -  Canceling a release: Only the deployer and admin can perform this operation.                                            |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Operator              | Has the permissions to monitor, schedule, and perform O&M operations on the job and script instances in the production environment.    | -  Development environment: read-only permission                                                                           |
      |                       |                                                                                                                                        | -  Production environment: all permissions                                                                                 |
      |                       |                                                                                                                                        | -  Deployment: viewing the release package content                                                                         |
      |                       |                                                                                                                                        | -  Environment information configuration: read-only permission                                                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Viewer                | Read-only permission                                                                                                                   | Read-only permission                                                                                                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
