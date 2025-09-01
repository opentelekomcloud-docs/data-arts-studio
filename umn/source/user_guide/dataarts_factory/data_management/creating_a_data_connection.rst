:original_name: dataartsstudio_01_0404.html

.. _dataartsstudio_01_0404:

Creating a Data Connection
==========================

After creating a data connection, you can perform data operations on DataArts Factory, for example, managing databases, namespaces, database schema, and tables.

With one data connection, you can run multiple jobs and develop multiple scripts. If the connection information saved in the data connection changes, you only need to modify the corresponding information in Connection Management.


Creating a Data Connection
--------------------------

The data connection of DataArts Factory is created based on the data connection of Management Center. For details about how to create a data connection, see :ref:`Configuring DataArts Studio Data Connection Parameters <dataartsstudio_01_0009>`.

Viewing Connection References
-----------------------------

To view the references of a connection, perform the following steps:

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. Click |image1| to display the connection list.

#. Right-click a connection in the list and select **View Reference**.

#. In the displayed **Reference List** dialog box, view the jobs or scripts that use the connection.


   .. figure:: /_static/images/en-us_image_0000002269120705.png
      :alt: **Figure 1** Reference List

      **Figure 1** Reference List

.. |image1| image:: /_static/images/en-us_image_0000002269120701.png
