:original_name: dataartsstudio_01_0902.html

.. _dataartsstudio_01_0902:

Submitting a Version
====================

Submitting a version depends on the version management function of DataArts Factory.

Version management traces script and job changes, and supports version comparison and rollback. The system retains 100 latest version records. In addition, version management can be used to distinguish the development state and production state.

-  Development state: Scripts or jobs have not been submitted and are used for debugging. In the development state, you can edit, save, and run scripts or jobs without affecting those being scheduled. In addition, when a job is being associated with a script or job dependency is being configured, the associated script or job will read the configuration in the development state.
-  Production state: Script or jobs have been submitted and are used for formal scheduling. In formal scheduling, the latest submitted versions of scripts or jobs will be used in scenarios such as script invocation, instance rerunning, and job dependency and patch data configuration.

Prerequisites
-------------

A job has been developed.

Submitting a Job Version
------------------------

If you submit a version, the latest job in the development state will be saved and submitted and overwrite the previous job version.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click the developed job to access the job development page.

#. Above the job canvas or editor, click **Submit** to submit a version. In the displayed dialog box, select the reviewer, enter the change description (a maximum of 128 characters allowed), and select the check box below. If you do not select this option, you cannot click **OK**. When submitting a version, you can click **Compare Version** to view the differences between the current version and the last version.


   .. figure:: /_static/images/en-us_image_0000002305441221.png
      :alt: **Figure 1** Submitting a version

      **Figure 1** Submitting a version

   .. note::

      -  If review is enabled on the **Review Center** page, your submitted version will be reviewed by the workspace admin on the **Pending Review** tab page on the **Review Center** page. The version is submitted successfully only after it is approved by the admin. For details, see :ref:`Approval Settings <dataartsstudio_01_1820__li1334183317582>`.

         To revoke a submitted request, go to the **Review Center** page and click the **My Applications** tab. Then you can submit an application again.

      -  If review is enabled, the following operations need to be reviewed: submitting jobs, deleting jobs, and importing submitted jobs.

      -  Before disabling the review function, ensure that there are no requests pending review in the current workspace.

      -  The enterprise mode does not support the review function.

Version Rollback
----------------

After submitting the version, you can view it in the version list. (Currently, a maximum of 100 latest versions are saved.) Click **Roll Back** to roll back to any submitted version.

The rollback involves the following contents:

-  Job definition (such as operator properties and connection lines)
-  Basic job information, job scheduling configuration, job parameters, and lineage

The procedure is as follows:

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click a job to access the job development page.

#. On the right of the page, click the **Versions** tab and view the version submission records. Select the version to be rolled back and click **Roll Back**.


   .. figure:: /_static/images/en-us_image_0000002305408141.png
      :alt: **Figure 2** Rolling back the version

      **Figure 2** Rolling back the version

Viewing Version Details
-----------------------

You can view the submitted version information in the version list.

The procedure is as follows:

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click a job to access the job development page.

#. On the right of the page, click the **Versions** tab and view the version submission records. Select the desired version and click **View** to view its details.

   A new page is displayed, showing the job definition of the version. You cannot modify any job attributes in this window.


   .. figure:: /_static/images/en-us_image_0000002270848266.png
      :alt: **Figure 3** Viewing version details

      **Figure 3** Viewing version details

Version Comparison
------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click a job to access the job development page.

#. On the right of the page, click the **Versions** tab and view the version submission records. Select the versions to be compared and click **Compare Version**.

   If you select only one version, the selected version is compared with the JSON of the development-state job. If you select two versions, the JSON of the two versions is compared.


   .. figure:: /_static/images/en-us_image_0000002305441209.png
      :alt: **Figure 4** Comparing versions

      **Figure 4** Comparing versions
