:original_name: dataartsstudio_01_0412.html

.. _dataartsstudio_01_0412:

(Optional) Creating a Database Schema
=====================================

After creating a DWS data connection, you can manage the database schemas under the DWS data connection.

Prerequisites
-------------

-  A DWS data connection has been created. For details, see :ref:`Creating a Data Connection <dataartsstudio_01_0404>`.
-  A DWS database has been created. For details, see :ref:`Creating a Database <dataartsstudio_01_0405>`.

Creating a Database Schema
--------------------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.

#. In the menu on the left, click |image1|. Click a DWS data connection name, select the database to be configured, and expand the directory level to **schemas**. Then right-click **schemas**, and choose **Create Schema** from the shortcut menu.

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

Modifying a Database Schema
---------------------------

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.
#. Choose |image2| from the menu on the left, click the data connection name, select a database, and expand the directory level to the database schema you want to modify. Right-click the database schema name and choose **Modify** from the shortcut menu.
#. In the displayed dialog box, modify the description of the database schema.
#. Click **OK**.

Deleting a Database Schema
--------------------------

.. note::

   -  The default database schema cannot be deleted.
   -  Deleted database schemas cannot be recovered. Exercise caution when performing this operation.

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.
#. Choose |image3| from the menu on the left, click the data connection name, select a database, and expand the directory level to the database schema you want to delete. Right-click the database schema name and choose **Delete** from the shortcut menu.
#. In the displayed dialog box, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001322247912.png
.. |image2| image:: /_static/images/en-us_image_0000001322407912.png
.. |image3| image:: /_static/images/en-us_image_0000001373168661.png
