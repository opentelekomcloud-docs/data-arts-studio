:original_name: dataartsstudio_01_0423.html

.. _dataartsstudio_01_0423:

Creating a Script
=================

DataArts Factory allows you to create, edit, debug, and run SQL, Python, and Shell scripts. Before developing a script, you must create one.

Prerequisites
-------------

You have completed operations in :ref:`Creating a Data Connection <dataartsstudio_01_0404>` and :ref:`Creating a Database <dataartsstudio_01_0405>`.

Procedure
---------

**Creating a Directory (If a directory already exists, you do not need to create one.)**

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory list, right-click a directory and choose **Create Directory** from the shortcut menu.

#. In the displayed dialog box, configure directory parameters. :ref:`Table 1 <dataartsstudio_01_0423__en-us_topic_0104967364_table198901741223>` describes the directory parameters.

   .. _dataartsstudio_01_0423__en-us_topic_0104967364_table198901741223:

   .. table:: **Table 1** Script directory parameters

      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Description                                                                                                                                         |
      +==================+=====================================================================================================================================================+
      | Directory Name   | Name of the script directory. The name must contain 1 to 64 characters, including only letters, numbers, underscores (**\_**), and hyphens (**-**). |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Select Directory | Parent directory of the script directory. The parent directory is the root directory by default.                                                    |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

**Creating a Script**

#. In the script directory list, right-click a directory and select **Create** *Script type* **Script** from the shortcut menu.
#. Go to the script development page. For details, see :ref:`Developing an SQL Script <dataartsstudio_01_0424>`, :ref:`Developing a Shell Script <dataartsstudio_01_0425>`, and :ref:`Developing a Python Script <dataartsstudio_01_4503>`.

   .. note::

      A maximum of five temporary scripts of the same type can be created. If you close a temporary script without saving it and create a script of the same type, the closed temporary script will be opened again.
