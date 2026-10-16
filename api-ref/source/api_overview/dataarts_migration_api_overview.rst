:original_name: apiOverview_CDM.html

.. _apiOverview_CDM:

DataArts Migration API Overview
===============================

.. table:: **Table 1** DataArts Migration API types

   +-----------------------------------------------------------------------------+-------------------------+
   | Type                                                                        | Description             |
   +=============================================================================+=========================+
   | :ref:`Cluster Management <apioverview_cdm__section_tag_child_935951948496>` | Cluster management APIs |
   +-----------------------------------------------------------------------------+-------------------------+
   | :ref:`Job Management <apioverview_cdm__section_tag_child_673567725120>`     | Job management APIs     |
   +-----------------------------------------------------------------------------+-------------------------+
   | :ref:`Link Management <apioverview_cdm__section_tag_child_178546597951>`    | Link management APIs    |
   +-----------------------------------------------------------------------------+-------------------------+

.. _apioverview_cdm__section_tag_child_935951948496:

Cluster Management
------------------

.. table:: **Table 2** Cluster Management

   +---------------------------------------------------------------+---------------------------------------------+
   | API                                                           | Description                                 |
   +===============================================================+=============================================+
   | :ref:`Querying Cluster Details <showclusterdetail>`           | This API is used to query cluster details.  |
   +---------------------------------------------------------------+---------------------------------------------+
   | :ref:`Deleting a Cluster <deletecluster>`                     | This API is used to delete a cluster.       |
   +---------------------------------------------------------------+---------------------------------------------+
   | :ref:`Restarting a Cluster <restartcluster>`                  | This API is used to restart a cluster.      |
   +---------------------------------------------------------------+---------------------------------------------+
   | :ref:`Starting a Cluster <startcluster>`                      | This API is used to start a cluster.        |
   +---------------------------------------------------------------+---------------------------------------------+
   | :ref:`Stopping a Cluster (To Be Taken Offline) <stopcluster>` | This API is used to stop a cluster.         |
   +---------------------------------------------------------------+---------------------------------------------+
   | :ref:`Creating a Cluster <createcluster>`                     | This API is used to create a cluster.       |
   +---------------------------------------------------------------+---------------------------------------------+
   | :ref:`Querying the List of Clusters <listclusters>`           | This API is used to query the cluster list. |
   +---------------------------------------------------------------+---------------------------------------------+

.. _apioverview_cdm__section_tag_child_673567725120:

Job Management
--------------

.. table:: **Table 3** Job management

   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | API                                                                                      | Description                                                       |
   +==========================================================================================+===================================================================+
   | :ref:`Querying Jobs <showjobs>`                                                          | This API is used to query jobs.                                   |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | :ref:`Deleting a Job <deletejob>`                                                        | This API is used to delete a job.                                 |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | :ref:`Modifying a Job <updatejob>`                                                       | This API is used to modify a job.                                 |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | :ref:`Creating and Executing a Job in a Random Cluster <createandstartrandomclusterjob>` | This API is used to create and execute a job in a random cluster. |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | :ref:`Stopping a Job <stopjob>`                                                          | This API is used to stop a job.                                   |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | :ref:`Creating a Job in a Specified Cluster <createjob>`                                 | This API is used to create a job in a specified cluster.          |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | :ref:`Starting a Job <startjob>`                                                         | This API is used to start a job.                                  |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | :ref:`Querying Job Status <showjobstatus>`                                               | This API is used to query the job status.                         |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | :ref:`Querying Job Execution History <showsubmissions>`                                  | This API is used to query the job execution history.              |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------+

.. _apioverview_cdm__section_tag_child_178546597951:

Link Management
---------------

.. table:: **Table 4** Link management

   ==================================== ==================================
   API                                  Description
   ==================================== ==================================
   :ref:`Creating Links <createlink>`   This API is used to create a link.
   :ref:`Querying Links <showlink>`     This API is used to query links.
   :ref:`Deleting a Link <deletelink>`  This API is used to delete a link.
   :ref:`Modifying a Link <updatelink>` This API is used to modify a link.
   ==================================== ==================================
