:original_name: dataartsstudio_01_0402.html

.. _dataartsstudio_01_0402:

Data Management Process
=======================

The data management function helps you quickly establish data models and provides you with data entities for script and job development. With data management, you can:

-  Manage multiple types of data lakes, such as DWS, DLI, and MRS Hive.
-  Use the GUI and DDL to manage database tables. If an MRS API connection is used, you cannot view or manage the databases, data tables, and fields of the connection in a visualized manner.
-  Click |image1| to view the databases, data tables, and fields in the data connection directory tree. The directory tree is only available for DWS SQL, DLI SQL, and Hive connections using an agent.

.. note::

   If you have created a data connection, a database, and a data table, you can skip this section and go to :ref:`Script Development <dataartsstudio_01_0422>` or :ref:`Job Development <dataartsstudio_01_0432>`.

The following figure shows the process for using the data management function.


.. figure:: /_static/images/en-us_image_0000002305441473.png
   :alt: **Figure 1** Data management process

   **Figure 1** Data management process

#. Create a data connection to connect to a data lake base service. For details, see :ref:`Creating a Data Connection <dataartsstudio_01_0404>`.
#. Create a database based on the service type. For details, see :ref:`Creating a Database <dataartsstudio_01_0405>`.
#. If the connection type is DWS, create a database schema and a table. If the connection type is not DWS, create a table. For details, see :ref:`(Optional) Creating a Database Schema <dataartsstudio_01_0412>`.
#. Create a table. For details, see :ref:`Creating a Table <dataartsstudio_01_0416>`.

.. |image1| image:: /_static/images/en-us_image_0000002270791672.png
