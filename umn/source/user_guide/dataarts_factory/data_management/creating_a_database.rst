:original_name: dataartsstudio_01_0405.html

.. _dataartsstudio_01_0405:

Creating a Database
===================

After creating a data connection, you can create a database on the console or using a SQL script.

-  (Recommended) Console: You can directly create a database on the DataArts Studio DataArts Factory console with no code.
-  SQL script: You can also develop and execute a SQL script for creating a database in the SQL editor of DataArts Studio's DataArts Factory module or a data lake product, and then use the script to create a database.

This section describes how to create a database on the DataArts Factory console.

Prerequisites
-------------

-  You have already enabled the corresponding cloud services.
-  A data connection has been created. For details, see :ref:`Creating a Data Connection <dataartsstudio_01_0404>`.
-  MRS API connections cannot be used to manage databases in a visualized mode. You are advised to create a database using SQL scripts.
-  Before deleting a database, ensure that the database is not in use and is not associated with any data tables.

Creating a Database on the DataArts Factory Console
---------------------------------------------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.

#. In the menu on the left, click |image1|. Right-click the data connection for which you want to create a database, and choose **Create Database** from the shortcut menu. Set the parameters based on :ref:`Table 1 <dataartsstudio_01_0405__en-us_topic_0125929047_table152579468513>`.

   .. _dataartsstudio_01_0405__en-us_topic_0125929047_table152579468513:

   .. table:: **Table 1** Creating a database

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                                                           |
      +=======================+=======================+=======================================================================================================================================================================================+
      | Database Name         | Yes                   | Name of a database. The naming rules are as follows:                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                       |
      |                       |                       | -  DLI: The value must contain only numbers, letters, and underscores (_). It cannot start with an underscore (_) or contain only numbers.                                            |
      |                       |                       | -  DWS: The value must contain only numbers, letters, and underscores (_). It cannot start with an underscore (_) or contain only numbers.                                            |
      |                       |                       | -  MRS Hive: The value must contain 1 to 128 characters, including only letters, numbers, and underscores (_). It must start with a number or letter and cannot contain only numbers. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description           | No                    | Descriptive information about the database. The requirements are as follows:                                                                                                          |
      |                       |                       |                                                                                                                                                                                       |
      |                       |                       | -  DLI: The value contains a maximum of 256 characters.                                                                                                                               |
      |                       |                       | -  DWS: The value contains a maximum of 1,024 characters.                                                                                                                             |
      |                       |                       | -  MRS Hive: The value contains a maximum of 1,024 characters.                                                                                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Modifying a Database
--------------------

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.
#. In the menu on the left, click |image2|. Expand the data connection where the database is created, right-click the database name, and choose **Modify** from the shortcut menu.
#. In the **Modify Database** dialog box displayed, modify the database information.
#. Click **Yes**.

Deleting a Database
-------------------

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Script** or **Development** > **Develop Job**.
#. In the menu on the left, click |image3|. Expand the data connection where the database is created, right-click the database name, and choose **Delete** from the shortcut menu.
#. In the displayed data connection list, click **Delete**.
#. Click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001322247912.png
.. |image2| image:: /_static/images/en-us_image_0000001373168653.png
.. |image3| image:: /_static/images/en-us_image_0000001373168653.png
