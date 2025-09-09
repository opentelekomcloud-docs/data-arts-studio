:original_name: dataartsstudio_01_0503.html

.. _dataartsstudio_01_0503:

Solution
========

Context
-------

The solution aims to provide users with convenient and systematic management operations and better meet service requirements and objectives. Each solution can contain one or more business-related jobs, and one job can be used by multiple solutions.

You can perform the following operations on a solution:

-  :ref:`Creating a Solution <dataartsstudio_01_0503__en-us_topic_0143658504_section751119493161>`
-  :ref:`Editing a Solution <dataartsstudio_01_0503__en-us_topic_0143658504_section99951423113619>`
-  :ref:`Exporting a Solution <dataartsstudio_01_0503__en-us_topic_0143658504_section8480105617166>`
-  :ref:`Importing a Solution <dataartsstudio_01_0503__en-us_topic_0143658504_section478513261118>`
-  :ref:`Upgrading a Solution <dataartsstudio_01_0503__en-us_topic_0143658504_section49091847183618>`
-  :ref:`Deleting a Solution <dataartsstudio_01_0503__en-us_topic_0143658504_section14542122131713>`

.. _dataartsstudio_01_0503__en-us_topic_0143658504_section751119493161:

Creating a Solution
-------------------

On the development page of DLF, create a solution, set the solution name, and select business-related jobs.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation tree on the left of the data development page, choose **Development** > **Develop Script** or **Data Development** > **Develop Job**.

#. Above the directory on the left, click |image1| to show the solution directory.

#. Click |image2| in the upper part of the solution directory. The **Create Solution** page is displayed. :ref:`Table 1 <dataartsstudio_01_0503__en-us_topic_0143658504_table2057118573564>` describes the solution parameters.

   .. _dataartsstudio_01_0503__en-us_topic_0143658504_table2057118573564:

   .. table:: **Table 1** Solution Parameters

      ========== ==========================================
      Parameter  Description
      ========== ==========================================
      Name       Name of the solution.
      Select Job Select the jobs contained in the solution.
      ========== ==========================================

#. Click **OK**. The new solution is displayed in the directory on the left.

.. _dataartsstudio_01_0503__en-us_topic_0143658504_section99951423113619:

Editing a Solution
------------------

In the solution directory, right-click the solution name and select **Edit** to change the name and job.

.. _dataartsstudio_01_0503__en-us_topic_0143658504_section8480105617166:

Exporting a Solution
--------------------

In the solution directory, right-click the solution name and choose **Export** from the shortcut menu to export the solution file in ZIP format to the local host.

.. _dataartsstudio_01_0503__en-us_topic_0143658504_section478513261118:

Importing a Solution
--------------------

This solution is available only if the OBS service is available. If OBS is unavailable, data can be imported from the local PC.

In the solution directory, right-click a solution and choose **Import Solution** from the shortcut menu to import the solution file that has been uploaded to OBS or from a local directory.

.. note::

   If you select **Overwrite** for **Duplicate Name Policy** but the hard lock policy is used and the script is locked by another user, the overwriting will fail. For details about soft and hard lock policies, see :ref:`Configuring the Hard and Soft Lock Policy <dataartsstudio_01_04501__section140018355442>`.

.. _dataartsstudio_01_0503__en-us_topic_0143658504_section49091847183618:

Upgrading a Solution
--------------------

In the solution directory, right-click the solution name and choose **Upgrade** from the shortcut menu to import the solution file that has been uploaded to OBS. During the solution upgrade, the running jobs are stopped. The system determines whether to restart the jobs after the upgrade based on the configured upgrade restart policy.

.. _dataartsstudio_01_0503__en-us_topic_0143658504_section14542122131713:

Deleting a Solution
-------------------

In the solution directory, right-click the solution name and choose **Delete** from the shortcut menu. A deleted solution cannot be restored. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000002269124789.png
.. |image2| image:: /_static/images/en-us_image_0000002269124797.png
