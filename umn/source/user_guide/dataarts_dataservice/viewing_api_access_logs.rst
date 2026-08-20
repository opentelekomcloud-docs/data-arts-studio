:original_name: dataartsstudio_01_0900.html

.. _dataartsstudio_01_0900:

Viewing API Access Logs
=======================

Scenario
--------

You can query logs of DataArts DataService APIs, including the request path, request parameters, and response.

.. note::

   Currently, logs are only supported for APIs in DataArts DataService Exclusive.

Configuring LTS
---------------

To view logs of DataArts DataService APIs, you need to first configure LTS. For details about how to configure LTS, see .

#. Create a log group on the LTS console.

   a. Log in to the management console.

   b. Click |image1| in the upper left corner and select a region and project.

   c. Click **Service List** and click **Log Tank Service** under **Management & Governance**.


      .. figure:: /_static/images/en-us_image_0000002269119501.png
         :alt: **Figure 1** Accessing the LTS console

         **Figure 1** Accessing the LTS console

   d. In the navigation pane on the left, choose **Log Management**.

   e. Click **Create Log Group**. In the displayed dialog box, enter a log group name.

   f. Click **OK**.

#. Create a log stream.

   a. Click the name of the created log group.
   b. Click **Create Log Stream**. In the displayed dialog box, enter a log stream name.
   c. Click **OK**.

Enabling Dump of DataArts DataService Logs
------------------------------------------

Log in to the DataArts DataService Exclusive console, enter the **Basic Details** page of a cluster, enable **Dump Log**, and select **LTS**.


.. figure:: /_static/images/en-us_image_0000002269119489.png
   :alt: **Figure 2** Enabling dump of logs to LTS

   **Figure 2** Enabling dump of logs to LTS

Viewing Access Logs
-------------------

After configuring log dump, you can view details about access logs.

On the LTS console, click the name of the corresponding log stream. On the **Raw Logs** page, you can view access logs.

The following figure shows the log format, which cannot be changed.


.. figure:: /_static/images/en-us_image_0000002234080296.png
   :alt: **Figure 3** Log format

   **Figure 3** Log format

.. |image1| image:: /_static/images/en-us_image_0000002269119493.png
