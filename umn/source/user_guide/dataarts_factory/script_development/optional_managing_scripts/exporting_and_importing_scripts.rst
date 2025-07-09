:original_name: dataartsstudio_01_0428.html

.. _dataartsstudio_01_0428:

Exporting and Importing Scripts
===============================

Exporting Scripts
-----------------

You can export one or more script files from the script directory. The exported files store the latest content in the development state.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. Click |image1| in the script directory and select **Show Check Box**.

#. Select scripts, click |image2|, and select **Export Script**. After the export is successful, you can obtain the exported .zip file.


   .. figure:: /_static/images/en-us_image_0000002305441245.png
      :alt: **Figure 1** Selecting and exporting scripts

      **Figure 1** Selecting and exporting scripts

#. In the displayed **Export Script** dialog box, set **Export Status** and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002305408213.png
      :alt: **Figure 2** Exporting scripts

      **Figure 2** Exporting scripts

Importing Scripts
-----------------

This function is available only if the OBS service is available. If OBS is unavailable, scripts can be imported from the local PC.

You can import one or more script files in the script directory. After a job is imported, the content in the development state is overwritten and a new version is automatically submitted.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. Click |image3| and select **Import Script**. In the displayed dialog box, select the file to import and set **Duplicate Name Policy**.

   .. note::

      If you select **Overwrite** for **Duplicate Name Policy** but the hard lock policy is used and the script is locked by another user, the overwriting will fail. For details about soft and hard lock policies, see :ref:`Configuring the Hard and Soft Lock Policy <dataartsstudio_01_04501__section140018355442>`.


   .. figure:: /_static/images/en-us_image_0000002305408217.png
      :alt: **Figure 3** Importing scripts

      **Figure 3** Importing scripts

#. Click **Next**.

.. |image1| image:: /_static/images/en-us_image_0000002305406205.png
.. |image2| image:: /_static/images/en-us_image_0000002305406205.png
.. |image3| image:: /_static/images/en-us_image_0000002305406205.png
