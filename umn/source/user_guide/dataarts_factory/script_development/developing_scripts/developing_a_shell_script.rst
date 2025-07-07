:original_name: dataartsstudio_01_0425.html

.. _dataartsstudio_01_0425:

Developing a Shell Script
=========================

DataArts Factory allows you to develop, debug, and run Shell scripts online. You can run developed scripts in jobs. For details, see :ref:`Developing a Pipeline Job <dataartsstudio_01_0435>`.

Prerequisites
-------------

-  A shell script has been added. For details, see :ref:`Creating a Script <dataartsstudio_01_0423>`.
-  A host connection has been created. The Linux host is used to execute shell scripts. For details, see :ref:`Configuring a Host Connection <dataartsstudio_01_1305>`.
-  You have the permission to create and execute files in the **/tmp** directory on the host.
-  The maximum number of shell or Python scripts that can run concurrently on the ECS is determined by the value of **MaxSessions** in the **/etc/ssh/sshd_config** file on the ECS. Set **MaxSessions** based on the scheduling frequency of shell or Python scripts.
-  You have locked the script. Otherwise, you must click **Lock** so that you can develop the script. A script you create or import is locked by you by default. For details, see the :ref:`lock function <dataartsstudio_01_0912>`.

Procedure
---------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory list, double-click a script that you want to develop. The script development page is displayed.

#. In the upper part of the editor, select script properties. :ref:`Table 1 <dataartsstudio_01_0425__en-us_topic_0114018164_table5350135013499>` describes the script properties.

   .. _dataartsstudio_01_0425__en-us_topic_0114018164_table5350135013499:

   .. table:: **Table 1** Shell script properties

      =============== ========================================================
      Parameter       Description
      =============== ========================================================
      Host Connection Selects the host where a shell script is to be executed.
      =============== ========================================================

   Click **Input Parameters** and enter the parameter and interactive parameter for executing the shell script.

   .. table:: **Table 2** Shell script parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Parameter                         | Parameter transferred to the Shell script when it is executed. Parameters are separated by spaces, for example, **a b c**.                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | The parameter must be referenced by a location variable (for example, $1, $2, or $3) in the Shell script. Otherwise, the parameter is invalid. The location variable starts from 0. Variable 0 is reserved for storing the actual script name, variable 1 corresponds to the first parameter of the script, and so on. For example, $1, $2, and $3 reference parameters **a**, **b**, and **c**, respectively. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | Note: If a variable is referenced in the shell script, use the *$args* format instead of the *${args}* format. Otherwise, the variable will be replaced by a parameter with the same name in the job.                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | For example, if you enter **a b c** and run the following Shell script, **b** is displayed:                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | .. code-block::                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |    echo $2                                                                                                                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Interactive Parameter             | Interactive information (for example, passwords) provided during shell script execution. Interactive parameters are separated by spaces. The shell script reads parameter values in sequence according to the interaction situation.                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | For example, run the following interactive Shell script. Interaction parameters **1**, **2**, and **3** correspond to **begin**, **end**, and **exit**, respectively.                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | -  When the interaction parameter is set to **1**, the execution result is **start something**.                                                                                                                                                                                                                                                                                                                |
      |                                   | -  When the interaction parameter is set to **2**, the execution result is **stop something**.                                                                                                                                                                                                                                                                                                                 |
      |                                   | -  When the interaction parameter is set to **3**, the execution result is **exit**.                                                                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | .. code-block::                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |    #!/bin/bash                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   |    select Actions in "begin" "end" "exit"                                                                                                                                                                                                                                                                                                                                                                      |
      |                                   |    do                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    case $Actions in                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    "begin")                                                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |    echo "start something"                                                                                                                                                                                                                                                                                                                                                                                      |
      |                                   |    break                                                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    ;;                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    "end")                                                                                                                                                                                                                                                                                                                                                                                                      |
      |                                   |    echo "stop something"                                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    break                                                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    ;;                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    "exit")                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   |    echo "exit"                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   |    break                                                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    ;;                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    *)                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    echo "Ignorant"                                                                                                                                                                                                                                                                                                                                                                                             |
      |                                   |    ;;                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    esac                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |    done                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | The following is an example of using the read -p syntax:                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | .. code-block::                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |    read -p "Parameter 1 and parameter 2"Variable 1 Variable 2                                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Edit shell statements in the editor. To facilitate script development, DataArts Factory provides the following capabilities:

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
      -  **Shift** + **Ctrl** + **K**: Delete the current line.
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

      a. Write the script parameter name and parameter value in the shell statement. When the shell script is referenced by a job, if the parameter name configured for the job is the same as the parameter name of the shell script, the parameter value of the shell script is replaced by the parameter value of the job.

         An example is as follows:

         .. code-block::

            a=1
            echo ${a}

         In the preceding command, *a* indicates the parameter name. It can contain only letters, digits, hyphens (-), underscores (_), greater-than signs (>), and less-than signs (<), and can contain a maximum of 16 characters. The parameter name must be unique.

      b. Configure parameters in the upper part of the editor. When you execute the shell script, the configured parameters are transferred to the script. Separate parameters by spaces, for example, **a b c**. The parameter must be referenced by the shell script. Otherwise, the parameter is invalid.

         Note: If a variable is referenced in the shell script, use the *$args* format instead of the *${args}* format. Otherwise, the variable will be replaced by a parameter with the same name in the job.

   -  Owner

      Click **Basic Info** to set the script owner and description.

   -  The script cannot be larger than 16 MB.

   -  Allows you to go to the release page from the script development page in enterprise mode. Place the cursor over |image1| and click **Release**.

#. In the lower part of the editor, click **Execute**. After executing the shell statement, view the execution history and result of the script in the lower part of the editor.

   .. note::

      You can perform the following operations on execution results:

      -  Double-click or right-click the name of an execution result tab to rename it. The name can contain a maximum of 16 characters.
      -  Right-click the name of an execution result tab to close the current tab, all the tabs to the left or right of the current tab, all the other tabs, or all the tabs.
      -  The execution result of a Shell script cannot be larger than 30 MB. Otherwise, an error is reported.

#. Above the editor, click |image2| to save the script.

   If the script is created but not saved, set the parameters listed in :ref:`Table 3 <dataartsstudio_01_0425__en-us_topic_0104967365_table35383235269>`.

   .. _dataartsstudio_01_0425__en-us_topic_0104967365_table35383235269:

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

.. |image1| image:: /_static/images/en-us_image_0000002305406613.png
.. |image2| image:: /_static/images/en-us_image_0000002270790052.png
