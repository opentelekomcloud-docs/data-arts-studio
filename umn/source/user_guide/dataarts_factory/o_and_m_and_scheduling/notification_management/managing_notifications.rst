:original_name: dataartsstudio_01_0514.html

.. _dataartsstudio_01_0514:

Managing Notifications
======================

You can configure job notification tasks to notify you of job success or failures.

.. _dataartsstudio_01_0514__en-us_topic_0114591806_section6973441876:

Configuring a Notification
--------------------------

Before configuring a notification for a job:

-  Message notification has been enabled and a topic has been configured.
-  A job not in **Not Activated** status has been submitted.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.

#. On the **Manage Notification** tab page, click **Configure Notification**. In the displayed dialog box, configure parameters. :ref:`Table 1 <dataartsstudio_01_0514__en-us_topic_0114591806_table63861718143217>` describes the parameters.


   .. figure:: /_static/images/en-us_image_0000002269119697.png
      :alt: **Figure 1** Configuring notifications

      **Figure 1** Configuring notifications

   .. _dataartsstudio_01_0514__en-us_topic_0114591806_table63861718143217:

   .. table:: **Table 1** Notification parameters

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                                                                    |
      +=======================+=======================+================================================================================================================================================================================================================================================================================================+
      | Job Name              | Yes                   | Name of the job.                                                                                                                                                                                                                                                                               |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Notification Type     | Yes                   | Type of the notification.                                                                                                                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       | -  When **Notification Scope** is **One job**, available options for this parameter include:                                                                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |    -  **Abnormal**: When a job is not running properly or fails, a notification is sent to notify the user of the abnormality.                                                                                                                                                                 |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |       You can set **Max. Notifications** and **Min. Notification Interval (min)**. After a job encounters an exception or fails and before it is recovered, you can send the interval for sending alarm notifications.                                                                         |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |       .. note::                                                                                                                                                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |          You can set **Max. Notifications** to a value from 1 to 50. If the default value **1** is used, **Min. Notification Interval (min)** is unavailable.                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |          You can set **Min. Notification Interval (min)** to a value from 5 to 60.                                                                                                                                                                                                             |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |    -  **Successful**: When a job runs successfully, a notification is sent to notify the user of the success.                                                                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |    -  **Uncompleted**: This function supports only the jobs scheduled by day. If the job execution time is later than the configured time by which the job has not finished, a notification is sent.                                                                                           |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |    -  **Cancellation**: When a job is canceled, a notification is sent.                                                                                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |       .. note::                                                                                                                                                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |          An alarm notification is sent when a job being scheduled or a running job instance is manually stopped.                                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |          If a user except the job executor cancels a job, a job cancellation alarm notification is sent.                                                                                                                                                                                       |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |    -  **Successful rerun of a failed job**                                                                                                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |       .. note::                                                                                                                                                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |          A notification will be sent after the successful rerun of a failed job only when a failure alarm was sent when the job failed.                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |    -  Job modification                                                                                                                                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |       A notification is sent when a job is modified or deleted, or the script used by the job is modified or deleted by a user except the job owner. If the job owner is empty, no alarm notification will be sent if the job is modified.                                                     |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |    -  **Busy resources**: If the DLI resource queue is busy during job execution, the job execution takes a long time or fails. As a result, an alarm is generated and a notification is sent.                                                                                                 |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       | .. note::                                                                                                                                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |    -  For a real-time job, a notification is allowed to be sent only when the real-time job is in the **Run abnormally** or **Failed** state. For a batch job, a notification can be sent no matter when the batch job is in the **Run normally**, **Run abnormally**, or **Failed** state.    |
      |                       |                       |    -  If you choose the default DLI resource queue, you may not be able to obtain the resources needed to perform operations because the queue is busy and other users may preempt resources. If this occurs, you may try again during off-peak hours or create a queue to run your workloads. |
      |                       |                       |    -  When a PatchData or test job is successfully executed, no notification is sent to avoid email or SMS bombing. In addition, no notification is sent when a PatchData job instance is recovered.                                                                                           |
      |                       |                       |    -  If a job is re-executed and succeeds after it fails, a job instance recovery notification is sent.                                                                                                                                                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Topic Name            | Yes                   | Select a notification topic.                                                                                                                                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       | Click **View Topic** to go to the SMN page and view topics.                                                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       | .. note::                                                                                                                                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                                                                                                |
      |                       |                       |    Currently, only SMS, email, or HTTP are supported to subscribe to topics.                                                                                                                                                                                                                   |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Notification          | Yes                   | Whether to enable the notification function. The function is enabled by default.                                                                                                                                                                                                               |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Editing a Notification
----------------------

After a notification is created, you can modify the notification parameters as required.

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.

#. Click the **Manage Notification** tab.

#. In the **Operation** column of a notification, click **Edit**. In the displayed dialog box, edit notification parameters. :ref:`Table 1 <dataartsstudio_01_0514__en-us_topic_0114591806_table63861718143217>` lists the notification parameters.


   .. figure:: /_static/images/en-us_image_0000002234080432.png
      :alt: **Figure 2** Editing a job

      **Figure 2** Editing a job

#. Click **Yes**.

Disabling a Notification
------------------------

You can disable the notification function on the **Edit Notification** page or in the notification list.

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.

#. Click the **Manage Notification** tab.

#. In the **Notification** column, click |image1|. When it changes to |image2|, the notification function is disabled.


   .. figure:: /_static/images/en-us_image_0000002234080476.png
      :alt: **Figure 3** Disabling a Notification

      **Figure 3** Disabling a Notification

Viewing a Notification
----------------------

You can view all notification information on the **Notification Records** tab page.

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.

#. Click the **Notification Records** tab. You can only view data of the last 30 days.


   .. figure:: /_static/images/en-us_image_0000002269119681.png
      :alt: **Figure 4** Viewing notification records

      **Figure 4** Viewing notification records

Deleting a Notification
-----------------------

If you no longer need a notification, perform the following operations to delete it:

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.

#. Click the **Manage Notification** tab.

#. You can delete a notification in either of the following ways:


   .. figure:: /_static/images/en-us_image_0000002269119629.png
      :alt: **Figure 5** Deleting a notification

      **Figure 5** Deleting a notification

   -  In the **Operation** column of a notification, click **Delete**.
   -  Select the notifications to delete and click **Batch Delete** above the notification list.

#. In the displayed dialog box, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002234240288.png
.. |image2| image:: /_static/images/en-us_image_0000002269119645.png
