:original_name: dataartsstudio_01_4503.html

.. _dataartsstudio_01_4503:

Developing a Python Script
==========================

You can develop, debug, and run Python scripts online. The developed scripts can be run in jobs. For details, see :ref:`Developing a Job <dataartsstudio_01_0435>`.

Prerequisites
-------------

-  A Python script has been added. For details, see :ref:`Creating a Script <dataartsstudio_01_0423>`.
-  A host connection has been created. The host is used to execute Python scripts. For details about how to create a host connection, see :ref:`Table 11 <dataartsstudio_01_0009__en-us_topic_0103403019_table2958557716244>`.
-  You have locked the script. Otherwise, you must click **Lock** so that you can develop the script. A script you create or import is locked by you by default. For details, see the :ref:`lock function <dataartsstudio_01_0901__li156131452182514>`.

Constraints
-----------

Python scripts do not support script parameters or job parameters.

Procedure
---------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 1** DataArts Factory

      **Figure 1** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory list, double-click a script that you want to develop. The script development page is displayed.

#. In the upper part of the editor, configure the host connection for executing the Python script.

#. Edit Python statements in the editor. To facilitate script development, DataArts Factory provides the following capabilities:

   -  The script editor supports the following shortcut keys, which improve the script development efficiency:

      -  **Ctrl** + **/**: Comment out or uncomment the line or code block at the cursor.
      -  **Ctrl** + **S**: Save
      -  **Ctrl** +\ **Z**: Cancel
      -  **Ctrl** + **Y**: Redo
      -  **Ctrl** + **F**: Search
      -  **Ctrl** + **Shift** + **R**: Replace
      -  **Ctrl** + **X**: Cut (cut a line when the cursor selects nothing).
      -  **Alt** + mouse dragging: Select columns to edit a block.
      -  **Ctrl** + mouse click: Select multiple lines to edit or indent them together.
      -  **Shift** + **Ctrl** + **K**: Delete the current line.
      -  **Ctrl** + **→** (or **←**): Move the cursor rightwards (or leftwards) by word.
      -  **Ctrl** + **Home** or **Ctrl** + **End**: Navigate to the beginning or end of the current file.
      -  **Home** or **End**: Navigate to the beginning or end of the current line.
      -  **Ctrl** + **Shift** + **L**: Double-click all the same character strings and add cursors to them to implement batch modification.

   -  Owner

      Click **Basic Info** to set the script owner and description.

#. In the upper part of the editor, click **Execute**. After executing the Python statement, view the execution history and result of the script in the lower part of the editor.

   .. note::

      You can perform the following operations on execution results:

      -  Double-click or right-click the name of an execution result tab to rename it. The name can contain a maximum of 16 characters.
      -  Right-click the name of an execution result tab to close the current tab, all the tabs to the left or right of the current tab, all the other tabs, or all the tabs.

#. Above the editor, click |image1| to save the script.

   If the script is created but not saved, set the parameters listed in :ref:`Table 1 <dataartsstudio_01_4503__en-us_topic_0104967365_table35383235269>`.

   .. _dataartsstudio_01_4503__en-us_topic_0104967365_table35383235269:

   .. table:: **Table 1** Script parameters

      +------------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Mandatory | Description                                                                                                                                   |
      +==================+===========+===============================================================================================================================================+
      | Script Name      | Yes       | Name of the script. It contains a maximum of 128 characters. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed. |
      +------------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Description      | No        | Descriptive information about the script.                                                                                                     |
      +------------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Select Directory | Yes       | Directory to which the script belongs. The root directory is selected by default.                                                             |
      +------------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001373168709.png
