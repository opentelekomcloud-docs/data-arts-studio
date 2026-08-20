:original_name: dataartsstudio_01_1023.html

.. _dataartsstudio_01_1023:

Managing Sample Libraries
=========================

DataArts Security can generate sample libraries based on your OBS or HDFS sample files. When creating a random masking algorithm or character replacement masking algorithm, you can replace sensitive data with values in the sample library file. For details, see :ref:`Creating a Masking Algorithm <dataartsstudio_01_1035__en-us_topic_0000001637778038_section17832545124211>`.

This section describes how to create a sample library.

Prerequisites
-------------

A sample file has been uploaded to OBS or HDFS. The sample file must be in TXT format. It is recommended that the file be no larger than 10 MB. Data in the file can be separated by line breaks (\\n), spaces, commas (,), or vertical bars (|).

Notes and Constraints
---------------------

-  When creating a random or character replacement masking algorithm, if you select **Sample library** for **Random Mode** or **Replacement Mode**, the sample file for testing the algorithm cannot be larger than 10 KB. This restriction applies only to the algorithm test and does not apply to real static masking tasks.
-  It is recommended that a sample file be no larger than 10 MB. Otherwise, static masking tasks for which the sample file needs to be parsed may fail.
-  OBS sample files can only be used for static DLI data masking tasks and HDFS sample files can only be used for static MRS data masking tasks. For details about the mapping between static masking scenarios and engines, see :ref:`Reference: Static Data Masking Scenarios <dataartsstudio_01_1020__en-us_topic_0000001627560186_section13163202310593>`.

Creating a Sample
-----------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the navigation pane on the left, choose **Sample Libraries**.


   .. figure:: /_static/images/en-us_image_0000002269199561.png
      :alt: **Figure 1** Sample Libraries page

      **Figure 1** Sample Libraries page

#. On the **Sample Libraries** page, click |image1| in the directory, move the cursor to the directory, click |image2|, and enter a classification name to add a sample library classification. The classification name can contain a maximum of 64 characters, including only letters, digits, and underscores (_). The excess part, if any, will be truncated. A maximum of 10 layers of sample library classifications (except the **All** layer) are supported.


   .. figure:: /_static/images/en-us_image_0000002234240128.png
      :alt: **Figure 2** Adding a sample library classification

      **Figure 2** Adding a sample library classification

#. In the right pane, click **Create**. The classification selected on the left is set for **Classification** in the **Create** dialog box.


   .. figure:: /_static/images/en-us_image_0000002234240112.png
      :alt: **Figure 3** Creating a sample

      **Figure 3** Creating a sample

#. In the displayed dialog box, set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1023__en-us_topic_0000001676159901_table029714191274>` and click **Confirm**.


   .. figure:: /_static/images/en-us_image_0000002234080276.png
      :alt: **Figure 4** Creating a sample

      **Figure 4** Creating a sample

   .. _dataartsstudio_01_1023__en-us_topic_0000001676159901_table029714191274:

   .. table:: **Table 1** Parameters for creating a sample

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================================================================================================================================================================+
      | \*Name                            | Sample name. It can contain a maximum of 64 characters, including only letters, digits, and underscores (_). The excess part, if any, will be truncated.                                                                                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the sample to be created, which can contain a maximum of 1,024 characters.                                                                                                                                                                                                                                                                 |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Classification                  | The classification selected on the left is entered by default. You can also click it to select another classification.                                                                                                                                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Sample Libraries                | Select a sample file that has been uploaded to OBS or HDFS. The sample file must be in TXT format. It is recommended that the file be no larger than 10 MB. Data in the file can be separated by line breaks (\\n), spaces, commas (,), or vertical bars (|).                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                             |
      |                                   | OBS sample files can only be used for static DLI data masking tasks and HDFS sample files can only be used for static MRS data masking tasks. For details about the mapping between static masking scenarios and engines, see :ref:`Reference: Static Data Masking Scenarios <dataartsstudio_01_1020__en-us_topic_0000001627560186_section13163202310593>`. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Delimiter                       | Delimiter of data in the sample file, which can be a link break (\\n), space, comma (,), or vertical bar (|)                                                                                                                                                                                                                                                |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Related Operations
------------------

-  Editing a sample library classification: On the **Sample Libraries** page, click |image3|, move the cursor to the classification to be edited, click |image4|, and edit the classification name.

-  Deleting a sample library classification: On the **Sample Libraries** page, click |image5|, move the cursor to the classification to be edited, and click |image6|.

   Sample library classifications that contain samples cannot be deleted. The **All** root classification cannot be deleted either.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.

-  Editing a sample: On the **Sample Libraries** page, locate a sample and click **Edit** in the **Operation** column to modify parameters of the sample.

-  Deleting a sample: On the **Sample Libraries** page, locate a sample and click **Delete** in the **Operation** column to delete the sample.

   Samples being used by masking algorithms cannot be deleted. To delete such samples, cancel the reference first.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000002269199569.png
.. |image2| image:: /_static/images/en-us_image_0000002234240120.png
.. |image3| image:: /_static/images/en-us_image_0000002234240092.png
.. |image4| image:: /_static/images/en-us_image_0000002234080288.png
.. |image5| image:: /_static/images/en-us_image_0000002234240100.png
.. |image6| image:: /_static/images/en-us_image_0000002234080268.png
