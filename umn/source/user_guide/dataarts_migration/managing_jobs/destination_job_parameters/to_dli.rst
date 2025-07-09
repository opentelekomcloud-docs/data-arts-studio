:original_name: dataartsstudio_01_0072.html

.. _dataartsstudio_01_0072:

To DLI
======

If the destination link of a job is a :ref:`DLI link <dataartsstudio_01_0036>`, configure the destination job parameters based on :ref:`Table 1 <dataartsstudio_01_0072__en-us_topic_0108275441_table5046103815165>`.

.. note::

   When you use CDM to migrate data to DLI, DLI generates data files in the *dli-trans\** temporary OBS bucket. Therefore, you need to grant the account corresponding to the AK/SK the permissions to read and write the *dli-trans\** bucket and create directories. For details about how to add OBS permission policies, see :ref:`Adding an OBS Bucket Policy <dataartsstudio_01_0072__en-us_topic_0108275441_section4208185214711>`.

.. _dataartsstudio_01_0072__en-us_topic_0108275441_table5046103815165:

.. table:: **Table 1** Parameter description

   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Parameter                     | Description                                                                                                                    | Example Value          |
   +===============================+================================================================================================================================+========================+
   | Resource Queue                | Resource queue to which the destination table belongs                                                                          | cdm                    |
   |                               |                                                                                                                                |                        |
   |                               | The default queue of DLI cannot be used for migration jobs. You need to create a SQL queue in DLI.                             |                        |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Database Name                 | Name of the database to which data will be written                                                                             | dli                    |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Table Name                    | Name of the table to which data will be written                                                                                | car_detail             |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Clear Data Before Import      | Whether to clear data in the destination table before data import                                                              | No                     |
   |                               |                                                                                                                                |                        |
   |                               | If this parameter is set to **Yes**, data in the destination table will be cleared before the task is started.                 |                        |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Convert empty strings to null | If this parameter is set to **Yes**, an empty string is regarded as null.                                                      | No                     |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Data Clearing Mode            | This parameter is available when **Clear Data Before Import** is set to **Yes**.                                               | TRUNCATE               |
   |                               |                                                                                                                                |                        |
   |                               | **TRUNCATE**: deletes standard data.                                                                                           |                        |
   |                               |                                                                                                                                |                        |
   |                               | **INSERT_OVERWRITE**: overwrites existing data with inserted data.                                                             |                        |
   |                               |                                                                                                                                |                        |
   |                               | .. note::                                                                                                                      |                        |
   |                               |                                                                                                                                |                        |
   |                               |    If the source link is a Kafka link and **Clear Data Before Import** is set to **Yes**, **INSERT_OVERWRITE** is unavailable. |                        |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Partition                     | This parameter is available when **Clear Data Before Import** is set to **Yes**.                                               | year=2020,location=sun |
   |                               |                                                                                                                                |                        |
   |                               | When you enter partitions, data in these partitions will be cleared.                                                           |                        |
   +-------------------------------+--------------------------------------------------------------------------------------------------------------------------------+------------------------+

.. _dataartsstudio_01_0072__en-us_topic_0108275441_section4208185214711:

Adding an OBS Bucket Policy
---------------------------

#. Log in to the IAM console.

#. In the navigation pane, choose **Permissions** > **Policies/Roles** and click **Create Custom Policy** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000002270790172.png
      :alt: **Figure 1** Creating a custom policy

      **Figure 1** Creating a custom policy

#. Enter a policy name and set **Policy Content**.


   .. figure:: /_static/images/en-us_image_0000002305406901.png
      :alt: **Figure 2** Configuring the policy

      **Figure 2** Configuring the policy

   |image1|

#. Enter the policy description and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002270790168.png
