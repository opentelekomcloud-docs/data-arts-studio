:original_name: dataartsstudio_01_0125.html

.. _dataartsstudio_01_0125:

MongoDB/DDS Incremental Migration
=================================

By using CDM, you can export MongoDB or DDS data within a specified period. With the scheduled jobs of CDM, you can implement incremental migration of MongoDB and DDS.

.. note::

   If you have configured a macro variable of date and time and schedule a CDM job through DataArts Studio DataArts Factory, the system replaces the macro variable of date and time with (*Planned start time of the data development job* - *Offset*) rather than (*Actual start time of the CDM job* - *Offset*).

When creating a table/file migration job and selecting the link to MongoDB or DDS as the source link, you can set the query filters in advanced attributes.


.. figure:: /_static/images/en-us_image_0000002269197449.png
   :alt: **Figure 1** Setting query filters

   **Figure 1** Setting query filters

You can set this parameter to a :ref:`macro variable of date and time <dataartsstudio_01_0114>`, for example, **{"ts":{$gte:ISODate("${dateformat(yyyy-MM-dd'T'HH:mm:ss.SSS'Z',-1,DAY)}")}}**, which indicates searching for the values in the **ts** field that are greater than those after time macro conversion, that is, only the data generated after the previous day is exported.

After this parameter is set, CDM exports only the data generated on the previous day. In addition, you can set the job to be executed at 00:00:00 every day, so that the data generated every day can be incrementally synchronized.
