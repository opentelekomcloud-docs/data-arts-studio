:original_name: dataartsstudio_01_0438.html

.. _dataartsstudio_01_0438:

Exporting and Importing a Job
=============================

-  Exporting a job is to export the latest saved content in the development state.
-  After a job is imported, the content in the development state is overwritten and a new version is automatically submitted.

Exporting Jobs
--------------

**Method 1: Export a job on the job development page.**

#. Double-click a job name to access the development page of the job, click |image1|, and select the type of the job to be exported.

   -  **Export jobs only**: Export the connection relationships and property configurations of nodes to a local PC, excluding sensitive information such as passwords. After the export, you can use a browser to download the .zip package.
   -  **Export jobs and their dependency scripts**: Export the node connection relationships, node property configurations, job scheduling configurations, parameter configurations, dependency scripts, and resource definitions to a local PC, excluding sensitive information such as passwords. After the export, you can use a browser to download the .zip package.


   .. figure:: /_static/images/en-us_image_0000001322408252.png
      :alt: **Figure 1** Exporting a job (method 1)

      **Figure 1** Exporting a job (method 1)

#. Click **OK** to export the required job file.

**Method 2: Export one or more jobs from the job directory.**

#. Click |image2| in the job directory and select **Show Check Box**.


   .. figure:: /_static/images/en-us_image_0000001321928676.png
      :alt: **Figure 2** Clicking Show Check Box

      **Figure 2** Clicking Show Check Box

#. Select the jobs to export, click |image3|, and select **Export Job**. In the displayed dialog box, select **Export jobs only** or **Export jobs and their dependency scripts and resource definitions**. After the export is successful, you can obtain the exported .zip file.


   .. figure:: /_static/images/en-us_image_0000001373088201.png
      :alt: **Figure 3** Selecting and exporting a job

      **Figure 3** Selecting and exporting a job

Importing a Job
---------------

This function is available only if the OBS service is available. If OBS is unavailable, jobs can be imported from the local PC.

**Export one or more jobs from the job directory.**

#. Click |image4| > **Import Job** in the job directory, select the job file that has been uploaded to OBS or local directory, and rename the policy.

   .. note::

      If you select **Overwrite** for **Duplicate Name Policy** but the hard lock policy is used and the script is locked by another user, the overwriting will fail. For details about soft and hard lock policies, see :ref:`Configuring the Hard and Soft Lock Policy <dataartsstudio_01_04501__section140018355442>`.


   .. figure:: /_static/images/en-us_image_0000001373169009.png
      :alt: **Figure 4** Importing job definitions and dependencies

      **Figure 4** Importing job definitions and dependencies

#. Click **Next** to import the job as instructed.

   .. note::

      During the import, if the data connection, DLI queue, or GES graph associated with the job does not exist in DataArts Factory, the system prompts you to select one again.

Example
-------

Context:

-  A DWS data connection **doctest** is created in DataArts Factory.
-  A real-time job **doc1** is created in the job directory. Node **DWS SQL** is added to the job. The **Data Connection** of the node is set to **doctest**. **SQL Script** and **Database** are both configured.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 5** DataArts Factory

      **Figure 5** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. Search for **doc1** in the job search box, export the job to the local host, and then upload it to the OBS folder.

#. Delete the **doctest** data connection associated with the job in DataArts Factory.

#. Click |image5| > **Import Job** in the job directory, select the job file that has been uploaded to OBS, and set the duplicate name policy.

#. Click **Next** and select another data connection as prompted.

#. Click **Next** and then **Close**.

.. |image1| image:: /_static/images/en-us_image_0000001322248272.png
.. |image2| image:: /_static/images/en-us_image_0000001373408053.png
.. |image3| image:: /_static/images/en-us_image_0000001373408053.png
.. |image4| image:: /_static/images/en-us_image_0000001373088197.png
.. |image5| image:: /_static/images/en-us_image_0000001373408053.png
