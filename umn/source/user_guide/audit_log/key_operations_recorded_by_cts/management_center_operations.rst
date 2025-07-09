:original_name: dataartsstudio_01_1201.html

.. _dataartsstudio_01_1201:

Management Center Operations
============================

CTS provides records of operations on cloud service resources. With CTS, you can query, audit, and backtrack those operations.

.. table:: **Table 1** Key operations recorded by CTS

   ============================ ============= ===========================
   Operation                    Resource Type Trace Name
   ============================ ============= ===========================
   Creating data connections    dataWarehouse createDataWarehouse
   Editing data connections     dataWarehouse updateDataWarehouse
   Deleting data connections    dataWarehouse deleteDataWarehouse
   Creating workspaces          workspace     createWorkspaces
   Updating workspaces          workspace     updateWorkspaces
   Deleting workspaces          workspace     deleteWorkspaces
   Freezing workspaces          workspace     frozenWorkspaces
   Unfreezing workspaces        workspace     unfrozenWorkspaces
   Adding workspace users       User          saveWorkspaceUser
   Editing workspace users      User          updateWorkspaceUser
   Deleting workspace users     User          deleteWorkspaceUser
   Downloading files            Config        downloadFile
   Creating import/export tasks Config        createObsImportOrExportTask
   ============================ ============= ===========================
