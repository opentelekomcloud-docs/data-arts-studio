:original_name: dataartsstudio_01_1002.html

.. _dataartsstudio_01_1002:

Dashboard
=========

On the **Dashboard** page on the DataArts Security console, you can configure the data security administrator and view the number of sensitive tables, a pie chart of the security levels of sensitive tables, a pie chart of the security levels of sensitive fields, and the trends of the number of masking tasks and watermark embedding tasks.

Configuring the Security Administrator
--------------------------------------

The security administrator is specified by an account with the permissions of the DARTS Administrator system role. The security administrator has the highest permissions in the DataArts Security module of all workspaces in the DataArts Studio instance. In the DataArts Security module, only the security administrator and the DARTS Administrator system role have the permission to perform the following operations:

-  Configuring workspace permission sets
-  Configuring row-level access control using permissions
-  Synchronizing users
-  Configuring workspace resource permissions
-  Configuring fine-grained authentication
-  Configuring queue permissions

To configure the security administrator, log in to the DataArts Security console using an account with the permissions of the DARTS Administrator system role, and select an IAM user or user group on the **Dashboard** page. (If a user group is selected, all users in the user group are security administrators.)

.. note::

   -  Only the DARTS Administrator can configure a security administrator.
   -  The permissions of a security administrator take effect only for the DataArts Security component and are invalid for other components and services.


.. figure:: /_static/images/en-us_image_0000002269114945.png
   :alt: **Figure 1** Configuring the security administrator

   **Figure 1** Configuring the security administrator

Viewing Sensitive Data
----------------------

On the **Dashboard** page, you can filter data by data source and time. For example, you can view the sensitive data in the databases of GaussDB(DWS), DLI, and MRS Hive, including the number of sensitive tables, sensitive fields, masked tables, tables with watermarks, and watermarks traced.


.. figure:: /_static/images/en-us_image_0000002234075704.png
   :alt: **Figure 2** Data overview

   **Figure 2** Data overview

Data Analysis Reports
---------------------

-  Table security levels

   Create sensitive data discovery tasks to collect the number of table security levels. The security levels are customizable. The number of custom security levels and associated sensitive tables are displayed beside the pie chart.

   For details on how to create and run a sensitive data discovery task, see :ref:`Creating a Sensitive Data Discovery Task <dataartsstudio_01_1013__en-us_topic_0000001676159741_section191138181>`.


   .. figure:: /_static/images/en-us_image_0000002234235568.png
      :alt: **Figure 3** Security level pie chart

      **Figure 3** Security level pie chart

-  Field security levels

   Create sensitive data discovery tasks to detect sensitive table fields. The field security levels are customizable. The number of custom security levels and associated sensitive fields are displayed beside the pie chart.

   For details on how to create and run a sensitive data discovery task, see :ref:`Creating a Sensitive Data Discovery Task <dataartsstudio_01_1013__en-us_topic_0000001676159741_section191138181>`.


   .. figure:: /_static/images/en-us_image_0000002234075732.png
      :alt: **Figure 4** Security level pie chart

      **Figure 4** Security level pie chart

-  Masking tasks

   The number of masking tasks on each day in the last seven days is displayed. For details on how to create and run a data masking task, see :ref:`Create a Static Masking Task <dataartsstudio_01_1020__en-us_topic_0000001627560186_section191138181>`.


   .. figure:: /_static/images/en-us_image_0000002234235596.png
      :alt: **Figure 5** Changes of masking task quantity

      **Figure 5** Changes of masking task quantity

-  Watermark embedding tasks

   The number of watermark embedding tasks on each day in the last seven days is displayed.

   For details on how to create and run a watermark embedding task, see :ref:`Creating a Data Watermark Embedding Task <dataartsstudio_01_1021__en-us_topic_0000001676159785_section191138181>`.


   .. figure:: /_static/images/en-us_image_0000002269195013.png
      :alt: **Figure 6** Changes of watermark embedding task quantity

      **Figure 6** Changes of watermark embedding task quantity
