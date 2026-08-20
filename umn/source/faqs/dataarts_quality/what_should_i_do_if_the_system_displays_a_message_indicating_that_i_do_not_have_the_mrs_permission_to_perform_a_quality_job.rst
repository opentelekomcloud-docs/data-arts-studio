:original_name: dataartsstudio_03_0092.html

.. _dataartsstudio_03_0092:

What Should I Do If the System Displays a Message Indicating that I Do Not Have the MRS Permission to Perform a Quality Job?
============================================================================================================================

Possible Causes
---------------

An error is reported when you execute a quality job. The following information is recorded in the job log: "The current user does not exist on MRS Manager. Grant the user sufficient permissions on IAM and then perform IAM user synchronization on the Dashboard tab page!".

Solution
--------

This problem occurs because the user does not have the operation permission on the MRS cluster.

If the user is newly added to a tenant, find the corresponding MRS cluster instance on the MRS cluster list page and click **Synchronize**.

The procedure is as follows:

#. Log in to the MRS console, view the existing clusters, and click a cluster name to access the cluster overview page.


   .. figure:: /_static/images/en-us_image_0000002234077036.png
      :alt: **Figure 1** MRS cluster instance

      **Figure 1** MRS cluster instance

#. In the **IAM User Sync** area, click **Click to synchronize**.


   .. figure:: /_static/images/en-us_image_0000002269196305.png
      :alt: **Figure 2** Click to synchronize

      **Figure 2** Click to synchronize

#. View the operation result in the **Operation Logs** area.


   .. figure:: /_static/images/en-us_image_0000002548272643.png
      :alt: **Figure 3** Operation log

      **Figure 3** Operation log

#. After the preceding steps are complete, the account has been synchronized. If the system still displays a message indicating that you lack the MRS permission, log in to the Manager and create an account with the same name as the current primary account.

   .. note::

      You need to create an account with the same name as the current primary account.
