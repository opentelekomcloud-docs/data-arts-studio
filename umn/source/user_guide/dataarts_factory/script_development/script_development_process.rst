:original_name: dataartsstudio_01_0422.html

.. _dataartsstudio_01_0422:

Script Development Process
==========================

The script development function provides the following capabilities:

-  Provides an online script editor for developing and debugging SQL, Python, and Shell scripts.
-  Supports script import and export.
-  Allows use of variables and functions.
-  Provides editing locks for collaborative development.
-  Supports script version management and generation of saved and submitted versions.

   .. note::

      If you save a script multiple times within a minute, only one version is recorded. If the intermediate data is important, you can click **Save new version** to save and add a version.

-  Allows you to copy long script names. Click |image1|, perform fuzzy search to query matched scripts, and click the copy button next to a long script name to copy it.
-  Allows you to right-click a script to quickly copy the script name and to quickly close an opened script tab page.
-  Provides a link in the execution results of MRS Spark SQL and MRS Hive SQL scripts that use a connection of the MRS API type. Through this link, you can switch to MRS Yarn to view execution logs.
-  Allows you to switch to the task release page by placing the cursor on |image2| and clicking **Release** when developing a script in enterprise mode.
-  Allows you to filter submitted and unsubmitted scripts. Unsubmitted scripts are marked in red.
-  Displays script parameters in a dialog box. Parameter values can be changed, but parameter names cannot. You can click **Test Parameters** to view (but not modify) the parameters referenced by the script and the environment variables configured in the environment. Parameters in the SQL statement can be sorted by name.
-  Supports configuration of the SQL editor style. Move the cursor to |image3| and click **Style Configuration** to configure the editor, icon display, annotation templates, and shortcut keys that can be used in the SQL script editor.
-  Allows you to view SQL query results in a table or list. You can click **Style Configuration** and set **SQL Query Result Display Mode** on the **Configure Editor** tab page.
-  Allows you to go to the release page from the script development page in enterprise mode. Place the cursor over |image4| and click **Release** to go to the task release page.
-  Allows you to view tables of Hive SQL, DLI SQL, RDS SQL, and DWS SQL scripts. You can expand a table name to view the column names, field types, and descriptions in the table.

The following figure shows the process of script development.


.. figure:: /_static/images/en-us_image_0000002270790456.png
   :alt: **Figure 1** Script development process

   **Figure 1** Script development process

#. Create a script of the corresponding type. For details, see :ref:`Creating a Script <dataartsstudio_01_0423>`.
#. Develop the script: Develop, debug, and execute the script online. For details, see :ref:`Developing Scripts <dataartsstudio_01_0406>`.
#. Submit a version and unlock the script: After performing this step, the script can be scheduled by jobs and modified by other developers. For details, see :ref:`Submitting a Version <dataartsstudio_01_0901>`.
#. (Optional) Manage the script: After the script development is complete, you can manage the script as required. For details, see :ref:`(Optional) Managing Scripts <dataartsstudio_01_0407>`.
#. Release the script. This step is required in enterprise mode. For details, see :ref:`Releasing a Script Task <dataartsstudio_01_1902>`.

.. |image1| image:: /_static/images/en-us_image_0000002270847322.png
.. |image2| image:: /_static/images/en-us_image_0000002305407205.png
.. |image3| image:: /_static/images/en-us_image_0000002305407201.png
.. |image4| image:: /_static/images/en-us_image_0000002305407193.png
