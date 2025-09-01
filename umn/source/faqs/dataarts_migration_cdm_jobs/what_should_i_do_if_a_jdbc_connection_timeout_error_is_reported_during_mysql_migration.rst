:original_name: dataartsstudio_03_0110.html

.. _dataartsstudio_03_0110:

What Should I Do If a JDBC Connection Timeout Error Is Reported During MySQL Migration?
=======================================================================================

Symptom
-------

The following error message is displayed during MySQL migration: "Unable to connect to the database server. Cause: connect timed out"

Possible Cause
--------------

The table has a large data volume, and the source end uses the where statement to filter data. However, the column is not an index column or the column values are not discrete. As a result, the entire table is scanned during the query, causing a JDBC connection timeout.

Solution
--------

#. Contact the DBA to modify the table structure, set the columns to be filtered as index columns, and try again.

   If the failure persists because the data is not discrete, perform :ref:`2 <dataartsstudio_03_0110__en-us_topic_0000001117256694_li171918501191>` to :ref:`4 <dataartsstudio_03_0110__en-us_topic_0000001117256694_li391823117132>` and increase the JDBC timeout duration.

#. .. _dataartsstudio_03_0110__en-us_topic_0000001117256694_li171918501191:

   Locate the MySQL link name based on the job and obtain the link information.

#. Click the **Links** tab and click **Edit** to edit the link.


   .. figure:: /_static/images/en-us_image_0000002269196341.png
      :alt: **Figure 1** Editing the link

      **Figure 1** Editing the link

#. .. _dataartsstudio_03_0110__en-us_topic_0000001117256694_li391823117132:

   Click **Show Advanced Attributes**, add parameters **connectTimeout** and **socketTimeout** and their values in **Link Attributes** , and click **Save**.


   .. figure:: /_static/images/en-us_image_0000002269196349.png
      :alt: **Figure 2** Editing advanced attributes

      **Figure 2** Editing advanced attributes
