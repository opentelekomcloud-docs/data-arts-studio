:original_name: dataartsstudio_01_1105.html

.. _dataartsstudio_01_1105:

Execution History
=================

This section describes how to view the execution history of scripts, jobs, and nodes over a week.

Prerequisites
-------------

This function depends on OBS buckets. For details about how to configure OBS buckets, see :ref:`Configuring an OBS Bucket <dataartsstudio_01_1106>`.

Script Execution History
------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.
#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.
#. In the navigation pane of the DataArts Factory homepage, choose **Data Development** > **Develop Script**.
#. Above the directory, click |image1| to display the script and job execution history in the past seven days.
#. Select **Scripts** from the drop-down list box to filter out the script execution history.
#. Click a record to view the script information and execution result.
#. Download the historic script execution result.

   .. note::

      -  By default, all users can download the historic execution results of scripts.
      -  You can click **Download** on the **Result** tab page.
      -  You can download the result file in CSV format. A maximum of 1,000 results can be queried and downloaded.

Job Execution History
---------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.
#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Job**.
#. Above the directory, click |image2| to display the script and job execution history in the past seven days.
#. Select **Jobs** from the drop-down list box to filter out the job execution history.
#. Click a record to view the job and log information.

   .. note::

      If only some nodes of the job were tested, the execution history only displays information and logs for these nodes.

.. |image1| image:: /_static/images/en-us_image_0000002269202721.png
.. |image2| image:: /_static/images/en-us_image_0000002269202729.png
