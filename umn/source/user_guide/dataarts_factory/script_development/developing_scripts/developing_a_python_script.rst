:original_name: dataartsstudio_01_4503.html

.. _dataartsstudio_01_4503:

Developing a Python Script
==========================

DataArts Factory allows you to develop, debug, and run Python scripts online. You can run developed scripts in jobs. For details, see :ref:`Developing a Pipeline Job <dataartsstudio_01_0435>`.

For details about how to develop a Python scripts, see :ref:`Developing a Python Script <dataartsstudio_01_0529>`.

Prerequisites
-------------

-  A Python script has been added. For details, see :ref:`Creating a Script <dataartsstudio_01_0423>`.
-  A host connection has been created. The Linux host is used to execute Python scripts. For details about how to create a host connection, see :ref:`Host Connection Parameters <dataartsstudio_01_1305>`.
-  You have the permission to create and execute files in the **/tmp** directory on the host.
-  The maximum number of shell or Python scripts that can run concurrently on the ECS is determined by the value of **MaxSessions** in the **/etc/ssh/sshd_config** file on the ECS. Set **MaxSessions** based on the scheduling frequency of shell or Python scripts.
-  You have locked the script. Otherwise, you must click **Lock** so that you can develop the script. A script you create or import is locked by you by default. For details, see the :ref:`lock function <dataartsstudio_01_0912>`.

Procedure
---------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory list, double-click a script that you want to develop. The script development page is displayed.

#. In the upper part of the editor, configure the Python version and the host connection for executing the Python script.

   .. table:: **Table 1** Python script properties

      +-----------------------------------+----------------------------------------------------------+
      | Parameter                         | Description                                              |
      +===================================+==========================================================+
      | Python Version                    | Select a Python version.                                 |
      |                                   |                                                          |
      |                                   | -  **Python2**: indicates Python 2.                      |
      |                                   | -  **Python3**: indicates Python 3.                      |
      +-----------------------------------+----------------------------------------------------------+
      | Host Connection                   | Select the host where a Python script is to be executed. |
      +-----------------------------------+----------------------------------------------------------+

   Click **Input Parameters** and enter the parameter and interactive parameter for executing the Python script.

   .. table:: **Table 2** Python script parameters

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                               |
      +=======================+===========================================================================================================================================================================================================================================+
      | Parameter             | Parameter transferred to the Python script when the script is executed. Parameters are separated by spaces, for example, **a b c**. The parameter must be referenced by the Python script. Otherwise, the parameter is invalid.           |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Interactive Parameter | Interactive information (for example, passwords) provided during Python script execution. Interactive parameters are separated by spaces. The Python statement reads parameter values in sequence according to the interaction situation. |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Edit Python statements in the editor. To facilitate script development, DataArts Factory provides the following capabilities:

   -  The script editor supports the following shortcut keys, which improve the script development efficiency:

      -  **F8**: Run a script.
      -  **F9**: Stop running a script.
      -  **Ctrl** + **/**: Comment out or uncomment the line or code block where the cursor resides.
      -  **Ctrl** + **S**: Save a script.
      -  **Ctrl** + **Z**: Undo an action.
      -  **Ctrl** + **F**: Search for information.
      -  **Ctrl** + **Shift** + **R**: Replace
      -  **Ctrl** + **X**: Cut (Cut a line when the cursor selects nothing.)
      -  **Alt** + mouse dragging: Select columns to edit a block.
      -  **Ctrl** + mouse click: Select multiple lines to edit or indent them together.
      -  **Ctrl** + **→** (or **←**): Move the cursor rightwards (or leftwards) by word.
      -  **Ctrl** + **Home** or **Ctrl** + **End**: Navigate to the beginning or end of the current file.
      -  **Home** or **End**: Navigate to the beginning or end of the current line.
      -  **Ctrl** + **Shift** + **L**: Double-click all the same character strings and add cursors to them to implement batch modification.
      -  **Ctrl** + **D**: Delete a line.
      -  **Shift** + **Ctrl** + **U**: Unlock a script.
      -  **Ctrl** + **Alt** + **K**: Select the word where the cursor resides.
      -  **Ctrl** + **B**: Format
      -  **Ctrl** + **Shift** + **Z**: Redo
      -  **Ctrl** + **Enter**: Execute the selected line or content.
      -  **Ctrl** + **Alt** + **F**: Flag
      -  **Ctrl** + **Shift** + **K**: Search for the previous one.
      -  **Ctrl** + **K**: Search for the next one.
      -  **Ctrl** + **Backspace**: Delete the word to the left of the cursor.
      -  **Ctrl** + **Delete**: Delete the word to the right of the cursor.
      -  **Alt** + **Backspace**: Delete all content from the beginning of the line to the cursor.
      -  **Alt** + **Delete**: Delete all content from the cursor to the end of the line.
      -  **Alt** + **Shift**\ ``-``\ **Left**: Select all content from the beginning of the line to the cursor.
      -  **Alt** + **Shift**\ ``-``\ **Right**: Select all content from the cursor to the end of the line.

   -  Script parameter function. Use this function in either of the following ways:

      a. Write the script parameter name and parameter value in the Python statement. When the Python script is referenced by a job, if the parameter name configured for the job is the same as the parameter name of the Python script, the parameter value of the Python script is replaced by the parameter value of the job.

         Transfer parameters in the script. The following is an example script:

         .. code-block::

            a=1
            print (a)
            or
            a= 'qqq'
            print (a)

         Transfer parameters outside the script. For example, if you want to transfer parameters of the Python script to a Python job which uses the Python script, enclose string parameters in single quotation marks. The following is an example script:

         .. code-block::

            a= 'zhang'
            print (${a})

         In the preceding command, *a* indicates the parameter name. It can contain only letters, digits, hyphens (-), underscores (_), greater-than signs (>), and less-than signs (<), and can contain a maximum of 16 characters. The parameter name must be unique.

      b. Click **Input Parameters** and set parameters, which will be transferred to the Python script during execution of the script. Separate parameters by spaces, for example, **a b c**. The parameter must be referenced by the Python script. Otherwise, the parameter is invalid.

   -  Owner

      Click **Basic Info** to set the script owner and description.

   -  The script cannot be larger than 16 MB.

   -  Allows you to go to the release page from the script development page in enterprise mode. Place the cursor over |image1| and click **Release**.

#. In the upper part of the editor, click **Execute**. After executing the Python statement, view the execution history and result of the script in the lower part of the editor.

   .. note::

      You can perform the following operations on execution results:

      -  Double-click or right-click the name of an execution result tab to rename it. The name can contain a maximum of 16 characters.
      -  Right-click the name of an execution result tab to close the current tab, all the tabs to the left or right of the current tab, all the other tabs, or all the tabs.
      -  The execution result of a Python script cannot be larger than 30 MB. Otherwise, an error is reported.
      -  When viewing the script execution result, you can double-click a field in any row to view the result details. You can copy the field name.
      -  You can control display of the script execution history by setting **Script Execution History** in **Default Configuration** to **Myself** or **All users**.

#. Above the editor, click **Save** to save the script.

   If the script is created but not saved, set the parameters listed in :ref:`Table 3 <dataartsstudio_01_4503__en-us_topic_0104967365_table35383235269>`.

   .. _dataartsstudio_01_4503__en-us_topic_0104967365_table35383235269:

   .. table:: **Table 3** Script parameters

      +------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Mandatory | Description                                                                                                                                        |
      +==================+===========+====================================================================================================================================================+
      | Script Name      | Yes       | Name of the script. The name contains a maximum of 128 characters, including only letters, numbers, hyphens (-), underscores (_), and periods (.). |
      +------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description      | No        | Description of the script                                                                                                                          |
      +------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Select Directory | Yes       | Directory to which the script belongs. The root directory is selected by default.                                                                  |
      +------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      If you open an unsaved script, you can restore its content from the local cache.

      After the script is saved, a version is automatically generated and displayed in **Versions**. The version can be rolled back. If you save a script multiple times within a minute, only one version is recorded. If the intermediate data is important, you can click **Save new version** to save and add a version.

.. |image1| image:: /_static/images/en-us_image_0000002269116013.png
