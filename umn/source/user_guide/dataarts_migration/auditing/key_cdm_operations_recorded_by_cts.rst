:original_name: dataartsstudio_01_0126.html

.. _dataartsstudio_01_0126:

Key CDM Operations Recorded by CTS
==================================

CTS provides records of operations on cloud service resources. With CTS, you can query, audit, and backtrack those operations.

.. table:: **Table 1** CDM operations recorded by CTS

   ================================ ============= ================
   Operation                        Resource Type Trace Name
   ================================ ============= ================
   Creating a cluster               cluster       createCluster
   Deleting a cluster               cluster       deleteCluster
   Modifying cluster configurations cluster       modifyCluster
   Starting a cluster               cluster       startCluster
   Restarting a cluster             cluster       startStopCluster
   Importing a job                  cluster       clusterImportJob
   Binding an EIP                   cluster       bindEip
   Unbinding an EIP                 cluster       unbindEip
   Creating a link                  link          createLink
   Modifying a link                 link          modifyLink
   Deleting a link                  link          deleteLink
   Creating a job                   job           createJob
   Modifying a job                  job           modifyJob
   Deleting a job                   job           deleteJob
   Starting a job                   job           startJob
   Stopping a job                   job           stopJob
   ================================ ============= ================
