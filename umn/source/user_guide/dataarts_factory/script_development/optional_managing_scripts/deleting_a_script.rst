:original_name: dataartsstudio_01_0429.html

.. _dataartsstudio_01_0429:

Deleting a Script
=================

If you do not need to use a script any more, perform the following operations to delete it.

When you delete a script, the system checks whether the script is being referenced by some jobs. **Version** in the reference list lists the job versions that reference the script. When you click **Delete**, the job and all its version information are deleted.

.. note::

   If a script to be deleted is being associated with a job, ensure that services are not affected after the script is forcibly deleted. If you want to continue to use the job, go to the **Develop Job** page and associate the job with an available script.

Prerequisites
-------------

The script that you want to delete is not used by any jobs.


Deleting a Script
-----------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory, right-click the script that you want to delete and choose **Delete** from the shortcut menu.

#. In the displayed dialog box, click **OK**.

Batch Deleting Scripts
----------------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 2** DataArts Factory

      **Figure 2** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. On the top of the script directory, click |image1| and select **Show Check Box**.

#. Select the scripts to be deleted, click |image2|, and select **Batch Delete**.

#. In the displayed dialog box, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001373408053.png
.. |image2| image:: /_static/images/en-us_image_0000001373408053.png
