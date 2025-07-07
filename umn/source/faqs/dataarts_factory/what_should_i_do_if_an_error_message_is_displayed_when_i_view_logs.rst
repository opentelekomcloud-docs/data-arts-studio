:original_name: dataartsstudio_03_0418.html

.. _dataartsstudio_03_0418:

What Should I Do If an Error Message Is Displayed When I View Logs?
===================================================================

Symptom
-------

When you view the logs of a data development node, the error message shown in the following figure is displayed.


.. figure:: /_static/images/en-us_image_0000002270846026.png
   :alt: **Figure 1** Message displayed

   **Figure 1** Message displayed

Possible Causes
---------------

Logs of data development jobs are stored in OBS buckets. This message is displayed if the user group to which you belong does not have the OBS operation permission, or no OBS log file is available.

Solution
--------

#. Log in to the IAM console as an administrator.

#. In the navigation pane, choose **Users**. Then click your username to go to the user information page.

#. Obtain the user group to which your user belongs.


   .. figure:: /_static/images/en-us_image_0000002305717785.png
      :alt: **Figure 2** User group to which your user belongs

      **Figure 2** User group to which your user belongs

#. In the navigation pane, choose **User Groups**. Locate the row that contains the user group obtained in the previous step and click **Authorize** in the **Operation** column.

#. On the displayed **Authorize User Group** page, search for and select the **OBS OperateAccess** or **OBS Administrator** permission.


   .. figure:: /_static/images/en-us_image_0000002271181068.png
      :alt: **Figure 3** Assigning permissions to the user group

      **Figure 3** Assigning permissions to the user group

#. Click **Next** and select the scope requiring minimum authorization. The **All resources** option is selected by default.

#. Click **OK**.

   If the permissions are correct, check whether a log file exists in the OBS bucket.

Handling the Error After Running a Job
--------------------------------------

#. Log in to the IAM console as an administrator.

#. In the navigation pane, choose **Users**. Then click your username to go to the user information page.

#. Click |image1| next to **Access Type** to change the access type.

#. Select **Programmatic access** and **Management console access**.


   .. figure:: /_static/images/en-us_image_0000002305438973.png
      :alt: **Figure 4** Configuring the access type

      **Figure 4** Configuring the access type

#. Click **OK**.

   .. important::

      -  When creating a workspace on the management console, you can set the OBS path for storing job logs only to an OBS object bucket rather than a parallel file system. If you do not set the OBS path for storing job logs, DataArts Factory writes logs to the **dlf-log-**\ *{projectId}* bucket, and DataArts DataService writes logs to the **dlm-log-**\ *{projectId}* bucket by default.
      -  If you do not select an existing OBS bucket for **Job Log Path**, the default **dlf-log-**\ *{projectId}* bucket cannot be created when you run the job for the first time. As a result, logs cannot be written. To ensure that job logs can be properly written to the OBS bucket, select an existing OBS path when creating a workspace.

.. |image1| image:: /_static/images/en-us_image_0000002305438965.png
