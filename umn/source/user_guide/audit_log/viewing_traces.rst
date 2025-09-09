:original_name: dataartsstudio_01_0127.html

.. _dataartsstudio_01_0127:

Viewing Traces
==============

Overview
--------

You can use Cloud Trace Service (CTS) to record key operation events related to DataArts Studio. The events can be used in various scenarios such as security analysis, compliance audit, resource tracing, and problem locating.

After you enable CTS, the system starts to record DataArts Studio operations. The management console of CTS stores the traces of the latest seven days.

Prerequisites
-------------

CTS has been enabled. For details about how to enable it, see section "Enabling CTS" in *Cloud Trace Service User Guide*.

Procedure
---------

#. Log in to the management console and choose **Cloud Trace Service** from the service list.

#. The trace list is displayed by default. You can filter traces.

   The sources of DataArts Studio traces include:

   -  **CDM**: traces of DataArts Migration
   -  **DLF**: traces of DataArts Factory
   -  **DLG**: traces of Management Center, DataArts Architecture, DataArts Quality, DataArts Catalog, and DataArts DataService


   .. figure:: /_static/images/en-us_image_0000002269204349.png
      :alt: **Figure 1** CDM traces

      **Figure 1** CDM traces

#. Click |image1| on the left of a trace to expand its details.

#. Click **View Trace** in the **Operation** column to view the trace structure details.

   For more information about CTS, see *Cloud Trace Service User Guide*.

.. |image1| image:: /_static/images/en-us_image_0000002234085076.png
