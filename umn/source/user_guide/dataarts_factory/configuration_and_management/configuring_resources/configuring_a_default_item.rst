:original_name: dataartsstudio_01_04501.html

.. _dataartsstudio_01_04501:

Configuring a Default Item
==========================

This section describes how to configure a default item.

Scenario
--------

If a parameter is invoked by multiple jobs, you can use this parameter as the default configuration item. In this way, you do not need to set this parameter for each job.

Configuring Periodic Scheduling
-------------------------------

To configure the default action on the current job when the job it depends on fails, perform the following operations:

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration**.

   .. note::

      Three options are available. The default value is **Terminate**.

      -  **Suspend**: The current job is suspended.
      -  **Continue**: The current job continues to be executed.
      -  **Terminate**: The current job is terminated.

#. Click **Save** to save the settings.

Configuring the Multi-IF Policy
-------------------------------

To configure the policy for executing nodes with multiple IF conditions, perform the following operations:

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration**.

   .. note::

      The following two options are available:

      -  **OR**: Nodes are executed if an IF condition is met.
      -  **AND**: Nodes are executed if all IF conditions are met.

      For details, see :ref:`Configuring the Policy for Executing a Node with Multiple IF Statements <dataartsstudio_01_0583__section1626375417376>`.

#. Click **Save** to save the settings.

.. _dataartsstudio_01_04501__section140018355442:

Configuring the Hard and Soft Lock Policy
-----------------------------------------

The policy determines how you can grab the lock of a job or script. If you use a soft lock, you can grab the lock of a job or script regardless of whether you have the lock. If you use a hard lock, you can only unlock or grab the lock of a job or script for which you have the lock. Operations such as publish, execution, and scheduling are not restricted by locks.

You can configure the hard/soft policy based on your needs.

#. In the navigation pane, choose **Configuration** > **Specifications**.
#. Choose **Default Configuration**.

   .. note::

      The default policy is **Soft Lock**.

      -  **Soft lock**: You can lock or unlock jobs or scripts, regardless of whether they are locked by others.
      -  **Hard Lock**: You can lock jobs or scripts only after they have been unlocked by other users. The space administrator and the **DAYU Administrator** user can lock and unlock jobs or scripts without any limitations.

#. Click **Save** to save the settings.
