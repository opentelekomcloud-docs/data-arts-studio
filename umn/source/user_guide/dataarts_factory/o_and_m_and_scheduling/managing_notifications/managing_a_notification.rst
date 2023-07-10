:original_name: dataartsstudio_01_0514.html

.. _dataartsstudio_01_0514:

Managing a Notification
=======================

You can configure DLF to notify you of job success after it is performed.

Configuring a Notification
--------------------------

Before configuring a notification for a job:

-  Message notification has been enabled and a topic has been configured.
-  A job not in **Not Activated** status has been submitted.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.

#. On the **Notification Management** tab page, click **Configure Notification**. In the displayed dialog box, configure parameters. :ref:`Table 1 <dataartsstudio_01_0514__en-us_topic_0114591806_table63861718143217>` describes the parameters.

   .. _dataartsstudio_01_0514__en-us_topic_0114591806_table63861718143217:

   .. table:: **Table 1** Notification parameters

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                                                              |
      +=======================+=======================+==========================================================================================================================================================================================================================================================================================+
      | Notification Scope    | Yes                   | Notification scope. Available options include:                                                                                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                                                                                                          |
      |                       |                       | -  **One job**: Notifications are sent for a single job.                                                                                                                                                                                                                                 |
      |                       |                       | -  **All jobs**: Notifications are sent for all jobs.                                                                                                                                                                                                                                    |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Job Name              | Yes                   | Name of the job.                                                                                                                                                                                                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Notification Type     | Yes                   | Type of the notification.                                                                                                                                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                                                                                                                          |
      |                       |                       | -  When **Notification Scope** is **One job**, available options for this parameter include:                                                                                                                                                                                             |
      |                       |                       |                                                                                                                                                                                                                                                                                          |
      |                       |                       |    -  **Run abnormally/Fail**: When a job cannot run normally or fail to run, a notification is sent to notify the user of the abnormality.                                                                                                                                              |
      |                       |                       |    -  **Run successfully**: When a job runs successfully, a notification is sent to notify the user of the success.                                                                                                                                                                      |
      |                       |                       |    -  **Uncompleted**: This function supports only the jobs scheduled by day. If the job execution time is later than the configured time by which the job has not finished, a notification is sent.                                                                                     |
      |                       |                       |    -  **Busy resources**: If resources are busy during job execution, a notification is sent.                                                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                                                                          |
      |                       |                       | -  When **Notification Scope** is **All jobs**, available options for this parameter include:                                                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                                                                          |
      |                       |                       |    -  **Run abnormally/Fail**: When a job cannot run normally or fail to run, a notification is sent to notify the user of the abnormality.                                                                                                                                              |
      |                       |                       |    -  **Busy resources**: If resources are busy during job execution, a notification is sent.                                                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                                                                          |
      |                       |                       | .. note::                                                                                                                                                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                                                                                                                          |
      |                       |                       |    For a real-time job, a notification is allowed to be sent only when the real-time job is in the **Run abnormally** or **Failed** state. For a batch job, a notification can be sent no matter when the batch job is in the **Run normally**, **Run abnormally**, or **Failed** state. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Topic Name            | Yes                   | Select a notification topic.                                                                                                                                                                                                                                                             |
      |                       |                       |                                                                                                                                                                                                                                                                                          |
      |                       |                       | .. note::                                                                                                                                                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                                                                                                                          |
      |                       |                       |    Currently, only SMS, email, or HTTP are supported to subscribe to topics.                                                                                                                                                                                                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Notification          | Yes                   | Whether to enable the notification function. The function is enabled by default.                                                                                                                                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Editing a Notification
----------------------

After a notification is created, you can modify the notification parameters as required.

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.
#. Click the **Notification Management** tab.
#. In the **Operation** column of a notification, click **Edit**. In the displayed dialog box, edit notification parameters. :ref:`Table 1 <dataartsstudio_01_0514__en-us_topic_0114591806_table63861718143217>` describes the notification parameters.
#. Click **Yes**.

Disabling a Notification
------------------------

You can disable the notification function on the **Edit Notification** page or in the notification list.

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.
#. Click the **Notification Management** tab.
#. In the **Notification Function** column, click |image1|. When it changes to |image2|, the notification function is disabled.

Viewing a Notification
----------------------

You can view all notification information on the **Notification Records** tab page.

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.
#. Click the **Notification Records** tab.

Deleting a Notification
-----------------------

If you do not need to use a notification any more, perform the following operations to delete it:

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.
#. Click the **Notification Management** tab.
#. You can delete a notification in either of the following ways:

   -  In the **Operation** column of a notification, click **Delete**.
   -  Select the notifications to delete and click **Batch Delete** above the notification list.

#. In the displayed dialog box, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001322408380.png
.. |image2| image:: /_static/images/en-us_image_0000001322248404.png
