:original_name: dataartsstudio_01_0901.html

.. _dataartsstudio_01_0901:

Submitting a Version
====================

Submitting a version depends on the version management function of DataArts Factory.

Version management traces script and job changes, and supports version comparison and rollback. The system retains 100 latest version records. In addition, version management can be used to distinguish the development state and production state.

-  Development state: Scripts or jobs have not been submitted and are used for debugging. In the development state, you can edit, save, and run scripts or jobs without affecting those being scheduled. In addition, when a job is being associated with a script or job dependency is being configured, the associated script or job will read the configuration in the development state.
-  Production state: Script or jobs have been submitted and are used for formal scheduling. In formal scheduling, the latest submitted versions of scripts or jobs will be used in scenarios such as script invocation, instance rerunning, and job dependency and patch data configuration.

Prerequisites
-------------

A script has been developed.

Submitting a Script Version
---------------------------

If you submit a version, the latest script in the development state will be saved and submitted and overwrite the previous script version.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory, double-click the developed script to access the script development page.

#. Above the script editor, click **Submit** to submit a version. In the displayed dialog box, select the reviewer, enter the change description (a maximum of 128 characters allowed), and select the check box below. If you do not select this option, you cannot click **OK**. When submitting a version, you can click **Compare Version** to view the differences between the current version and the last version.


   .. figure:: /_static/images/en-us_image_0000002234076428.png
      :alt: **Figure 1** Submitting a version

      **Figure 1** Submitting a version

   .. note::

      -  If review is enabled on the **Review Center** page, your submitted version will be reviewed by the reviewer on the **Pending Review** tab page on the **Review Center** page. The version is submitted successfully only after it is approved by the reviewer. For details, see :ref:`Approval Settings <dataartsstudio_01_1820__section1416816392412>`. If review is disabled, the version can be directly submitted.

         To revoke a submitted request, go to the **Review Center** page and click the **My Applications** tab. Then you can submit an application again.

      -  If review is enabled, the following operations need to be reviewed: submitting scripts, deleting scripts, and importing submitted scripts.

      -  Before disabling the review function, ensure that there are no requests pending review in the current workspace.

      -  The enterprise mode does not support the review function.

Version Rollback
----------------

After submitting the version, you can view it in the version list. (Currently, a maximum of 100 latest versions are saved.) Click **Roll Back** to roll back to any submitted version.

The rollback involves the following contents:

-  DLI: data connections, databases, resource queues, and script contents
-  DWS: data connections, databases, and script contents
-  HIVE: data connections, databases, resource queues, and script contents
-  SPARK: data connections, databases, and script contents
-  SHELL: host connections, parameters, interactive parameters, and script contents
-  RDS: data connections, databases, and script contents
-  PRESTO: data connections, modes, and script contents
-  PYTHON: host connections, parameters, interactive parameters, and script content
-  FLINK: script content

The procedure is as follows:

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory list, double-click a script that you want to develop. The script development page is displayed.

#. On the right of the page, click the **Versions** tab and view the version submission records. Select the version to be rolled back and click **Roll Back**.

   If the content in the development state is not submitted, the content will be overwritten after the rollback. In this case, you must submit the rollback version again to make it take effect. By default, the latest submitted version is used for scheduling.


   .. figure:: /_static/images/en-us_image_0000002269115641.png
      :alt: **Figure 2** Rolling back a version

      **Figure 2** Rolling back a version

Version Comparison
------------------

You can compare the script contents of two different versions. If you select only one version, the system compares the script content of the selected version with that in the development state. If you select two versions, the system compares the script contents of two different versions.

The procedure is as follows:

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory list, double-click a script that you want to develop. The script development page is displayed.

#. On the right of the page, click the **Versions** tab and view the version submission records. Select the versions to be compared and click **Compare Version**.


   .. figure:: /_static/images/en-us_image_0000002234076436.png
      :alt: **Figure 3** Comparing versions

      **Figure 3** Comparing versions

#. A new page is displayed, showing the script content of different versions on the left and right separately. The differences between the two versions have been marked. You can use the |image1| and |image2| buttons in the upper right corner to go to the previous or next change.


   .. figure:: /_static/images/en-us_image_0000002234236252.png
      :alt: **Figure 4** Version comparison details

      **Figure 4** Version comparison details

.. |image1| image:: /_static/images/en-us_image_0000002271689457.png
.. |image2| image:: /_static/images/en-us_image_0000002271769549.png
