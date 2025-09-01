:original_name: dataartsstudio_01_0412.html

.. _dataartsstudio_01_0412:

(Optional) Creating a Database Schema
=====================================

After creating a DWS data connection, you can manage the database schemas under the DWS data connection.

.. note::

   If existing database schemas meet your requirements, skip this section. Otherwise, create a database schema by following the instructions in this section.

Prerequisites
-------------

-  A DWS data connection has been created. For details, see :ref:`Creating a Data Connection <dataartsstudio_01_0404>`.
-  A DWS database has been created. For details, see :ref:`Creating a Database <dataartsstudio_01_0405>`.

Creating a Database Schema
--------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script development menu, click |image1|. Expand a DWS data connection, select the database to be configured, and expand the directory level to **schemas**. Then right-click **schemas** and select **Create Schema** from the shortcut menu.

#. In the displayed dialog box, set the schema parameters based on :ref:`Table 1 <dataartsstudio_01_0412__en-us_topic_0125929051_table152579468513>`.

   .. _dataartsstudio_01_0412__en-us_topic_0125929051_table152579468513:

   .. table:: **Table 1** Creating a database schema

      =========== ========= ==================================================
      Parameter   Mandatory Description
      =========== ========= ==================================================
      Mode Name   Yes       Name of a database schema.
      Description No        Descriptive information about the database schema.
      =========== ========= ==================================================

#. Click **OK**.

Related Operations
------------------

-  Modify a database schema: In the script development menu, click |image2|. Expand a data connection to the target database schema, right-click the database schema name, select **Edit**, and modify the database schema information.
-  Delete a database schema: In the script development menu, click |image3|. Expand a data connection to the target database schema, right-click the database schema name, select **Delete**, and click **OK** in the displayed dialog box.

   .. note::

      -  The default database schema cannot be deleted.
      -  Deleted database schemas cannot be recovered. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000002269120509.png
.. |image2| image:: /_static/images/en-us_image_0000002269200561.png
.. |image3| image:: /_static/images/en-us_image_0000002234241140.png
