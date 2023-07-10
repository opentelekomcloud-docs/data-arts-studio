:original_name: dataartsstudio_01_0402.html

.. _dataartsstudio_01_0402:

Data Management Process
=======================

The data management function helps you quickly establish data models and provides you with data entities for script and job development. With data management, you can:

-  Manage multiple types of data lakes, such as DWS and MRS Hive.
-  Use the GUI and DDL to manage database tables.

.. note::

   If you have created a data connection and a corresponding database and data table by referring to :ref:`Preparations Before Using DataArts Studio <dataartsstudio_01_0134>` before using DataArts Factory, you can skip data management operations and directly go to :ref:`Script Development <dataartsstudio_01_0422>` or :ref:`Job Development <dataartsstudio_01_0432>`.

The following figure shows the process for using the data management function.


.. figure:: /_static/images/en-us_image_0000001373408201.png
   :alt: **Figure 1** Data management process

   **Figure 1** Data management process

#. Create a data connection to connect to a data lake base service. For details, see :ref:`Creating a Data Connection <dataartsstudio_01_0404>`.
#. Create a database based on the service type. For details, see :ref:`Creating a Database <dataartsstudio_01_0405>`.
#. If the connection type is DWS, create a database schema and a table. If the connection type is not DWS, create a table. For details, see :ref:`(Optional) Creating a Database Schema <dataartsstudio_01_0412>`.
#. Create a table. For details, see :ref:`Creating a Table <dataartsstudio_01_0416>`.
