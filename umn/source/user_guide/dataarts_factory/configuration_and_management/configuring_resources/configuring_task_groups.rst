:original_name: dataartsstudio_01_1284.html

.. _dataartsstudio_01_1284:

Configuring Task Groups
=======================

By configuring a task group, you can control the maximum number of concurrent nodes in a task group in a more fine-grained manner.

Constraints
-----------

This function is available only for batch processing jobs.

Task groups cannot be used across workspaces.

Procedure
---------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane, choose **Configuration** > **Configure**.

#. Choose **Task Groups**.

#. Click **Create**.

#. In the displayed dialog box, set required parameters.

   .. table:: **Table 1** Parameters for creating a task group

      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                           |
      +===================================+=======================================================================================================+
      | Task Group Name                   | Name of the task group                                                                                |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Owner                             | Owner of the task group                                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Maximum number of concurrency     | Maximum number of concurrent job nodes in the current task group                                      |
      |                                   |                                                                                                       |
      |                                   | The maximum number of concurrent nodes is the current number of concurrent DataArts Studio instances. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the task group                                                                         |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   After the task group is created, go to the job development page. On the canvas of a job, click **Scheduling Setup** and select the created task group. Then the number of concurrent nodes in the current task group can be controlled in a more fine-grained manner based on the selected task group.

Follow-up Operations
--------------------

Modifying a task group: Locate a task group and click **Modify** in the **Operation** column.

Deleting a task group: Locate a task group and click **Delete** in the **Operation** column. A task group used by a job cannot be deleted.

Viewing references: Locate a task group and click **View Reference** in the **Operation** column to view the jobs that are using the task group.
