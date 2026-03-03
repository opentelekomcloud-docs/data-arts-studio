:original_name: dataartsstudio_01_0603.html

.. _dataartsstudio_01_0603:

Designing Subjects
==================

A subject is a hierarchical architecture that classifies and defines data to help clarify data assets and specify relationships between subject areas and business objects.

You can design subjects in either of the following ways:

-  :ref:`Creating and Publishing a Subject <dataartsstudio_01_0603__en-us_topic_0169427296_section325565610163>`

   Create and publish a subject.

-  :ref:`Importing a Subject <dataartsstudio_01_0603__en-us_topic_0169427296_section785421345411>`

   If the subject information is complex, you are advised to import subjects in batches.

   -  You can download the provided subject design template, fill in the content, and upload the file to import the subjects in batches.
   -  You can export the subjects created in DataArts Architecture of a DataArts Studio instance to an Excel file. Then, import the Excel file. For details on how to export subjects, see :ref:`Exporting a Subject <dataartsstudio_01_0603__section17983151820549>`.

You can search for, edit, or delete subjects. For details, see :ref:`Managing a Subject <dataartsstudio_01_0603__en-us_topic_0169427296_section7856181172118>`.

Subject Design Overview
-----------------------

By default, the system provides three subject levels: Subject Area Group (L1), Subject Area (L2), and Business Object (L3).

-  **Subject Area Group**: used to group business domains based on scenarios
-  **Subject Area**: A data domain is a dataset, in which data is of the same property.
-  **Business Object** includes important information about people, events, and things that are indispensable to enterprise operations and management.

You can also customize the subject levels by referring to :ref:`Subject Processes <dataartsstudio_01_0621__section28291944122319>`.

Constraints
-----------

A maximum of 5,000 subjects can be created in a workspace.

.. _dataartsstudio_01_0603__en-us_topic_0169427296_section325565610163:

Creating and Publishing a Subject
---------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Architecture**.

#. On the **DataArts Architecture** page, choose **Data Survey** > **Subjects** in the left navigation bar. On the page displayed, click **Create** in the upper left corner.


   .. figure:: /_static/images/en-us_image_0000002269120693.png
      :alt: **Figure 1** Designing a subject

      **Figure 1** Designing a subject

#. In the dialog box displayed, set the parameters and click **OK**.

   .. table:: **Table 1** Parameters for creating a subject area group

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                 |
      +===================================+=============================================================================================================================================================+
      | \* Subject Name                   | The following characters are not allowed: / \\ < >.                                                                                                         |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \* Subject Code                   | The code of the subject area group to create. Only letters, digits, spaces, underscores (_), hyphens (-), parentheses, and ampersands (&) are allowed.      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Alias                             | The following characters are not allowed: \\ < >.                                                                                                           |
      |                                   |                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                   |
      |                                   |                                                                                                                                                             |
      |                                   |    Before configuring an alias, choose **Metrics** > **Configuration Center**, click the **Model Settings** tab, and select **Subjects** for **Use Alias**. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parent Subject                    | Parent subject of the subject area group                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Owner's Department           | The department that the data owner belongs to.                                                                                                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \* Data Owner                     | Select a data owner from the drop-down list box. You can select multiple data owners or enter custom data owners.                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the subject area group to create.                                                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+


   .. figure:: /_static/images/en-us_image_0000002234081508.png
      :alt: **Figure 2** Creating a subject

      **Figure 2** Creating a subject

#. Select the created subject area group and click **Publish**. In the displayed dialog box, select a reviewer and click **OK**. After the application is approved, the **Subjects** page is displayed. You can view the created subject area group in the list, and the status of the subject area group is **Published**. Only published subject area groups can be used.

   .. note::

      If you have been added as a reviewer, you can select **Auto-review** and click **OK**. After the application is approved, the subject area group status changes to **Published**.


   .. figure:: /_static/images/en-us_image_0000002234241336.png
      :alt: **Figure 3** Publishing a subject

      **Figure 3** Publishing a subject

#. You can create multiple subjects in a subject. Note that a subject can be published only if its upper-layer subjects have been published.

   .. note::

      When you are creating a L3 subject, that is, a business object, parameter **Subject Code** is displayed in the **Create Business Object** dialog box. You can select **Auto Generate** or **Custom**.

      -  **Auto Generate**: A code is automatically generated based on the :ref:`encoding rule <dataartsstudio_01_0621__section66767193176>` in the Configuration Center.
      -  **Custom**: Enter a code.

      In subject design, business objects at different L1 levels can have the same name.

   The number of subject levels is defined by users on the **Subject Levels** tab page on the **Configuration Center** page. By default, there are three levels in the system, Subject Area Group (L1), Subject Area (L2), and Business Object (L3).

.. _dataartsstudio_01_0603__en-us_topic_0169427296_section785421345411:

Importing a Subject
-------------------

#. On the DataArts Architecture page, choose **Data Survey** > **Subjects** in the left navigation pane.

#. Click **More** above the subject list and select **Import**.


   .. figure:: /_static/images/en-us_image_0000002234081472.png
      :alt: **Figure 4** Importing a subject

      **Figure 4** Importing a subject

#. In the dialog box displayed, set **Update Existing Data**, click **Select File**, and click **Upload**.


   .. figure:: /_static/images/en-us_image_0000002234081488.png
      :alt: **Figure 5** Importing a subject

      **Figure 5** Importing a subject

   .. table:: **Table 2** Parameters for importing subjects

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================================+
      | Update Existing Data              | Whether to update existing subject information (subject area group, subject area, or business object) during the import. When a subject is imported, the system checks whether the subject exists according to its code.                  |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | -  **No**: If you select this option, the subject information will not be updated.                                                                                                                                                        |
      |                                   | -  **Yes**: If you select this option, the subject information will be updated.                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | During the import, only subject creation and update are allowed.                                                                                                                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Upload File                       | Select the file to import.                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | You can use either of the following methods to obtain the file to import:                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | -  **Downloading the subject import template and filling in it**                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   |    In the **Import Subject** dialog box, click **Subject Template** to download the template, fill in the content, and save the settings. See :ref:`Table 3 <dataartsstudio_01_0603__table1125753216561>` for template parameter details. |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | -  **Exporting subjects to files**                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   |    You can export the subjects created in DataArts Architecture of a DataArts Studio instance to an Excel file. Then, import the Excel file. See :ref:`Exporting a Subject <dataartsstudio_01_0603__section17983151820549>` for details.  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   :ref:`Table 3 <dataartsstudio_01_0603__table1125753216561>` describes the parameters in the downloaded template. Parameters whose names start with an asterisk (``*``) are mandatory, and other parameters are optional. Enter the information about a subject in a line.

   .. _dataartsstudio_01_0603__table1125753216561:

   .. table:: **Table 3** Parameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                |
      +===================================+============================================================================================================================================================+
      | Parent Subject                    | Encoding path of the upper-level subject, which is separated by slashes (/).                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Name                            | The following characters are not allowed: / \\ < >.                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Code                            | Code of the subject to create. Only letters, digits, spaces, underscores (_), hyphens (-), parentheses, and ampersands (&) are allowed.                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Alias                             | Alias of the subject.                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the subject.                                                                                                                              |
      |                                   |                                                                                                                                                            |
      |                                   | This parameter is mandatory for the lowest-level subject. You must add the description of the lowest-level subject in the file to be imported.             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Owner's Department           | The department that the data owner belongs to.                                                                                                             |
      |                                   |                                                                                                                                                            |
      |                                   | This parameter is mandatory for the lowest-level subject. You must add the department of the owner of the lowest-level subject in the file to be imported. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Owner                        | The owner of the data. Multiple owners are supported. Separate owner names with commas (,)                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. View the import result on the **Last Import** tab page. If the import is successful, click **Close**. If the import fails, you can view the failure cause, correct the template file, and upload it again.


   .. figure:: /_static/images/en-us_image_0000002269200777.png
      :alt: **Figure 6** Last Import tab page

      **Figure 6** Last Import tab page

.. _dataartsstudio_01_0603__section17983151820549:

Exporting a Subject
-------------------

#. On the DataArts Architecture page, choose **Data Survey** > **Subjects** in the left navigation pane.
#. Click **More** above the subject list and select **Export** to export the subjects to an Excel file. Then, import the Excel file.

   .. note::

      -  If you select subjects and click **Export**, the system recursively exports the selected subjects and their child subjects.
      -  If you select subjects in the directory tree and click **Export** without selecting subjects in the subject list, the selected subjects are exported recursively. If you select a topic name on the right, the selected topic and all its subtopics are exported recursively.

.. _dataartsstudio_01_0603__en-us_topic_0169427296_section7856181172118:

Managing a Subject
------------------


.. figure:: /_static/images/en-us_image_0000002269120677.png
   :alt: **Figure 7** Subject design area

   **Figure 7** Subject design area

-  Search

   You can enter a keyword in the search box to search for all subjects in the public workspace.

-  Edit

   Locate a subject in the list and click |image1| in the **Operation** column to edit the subject. To make a published subject take effect after you have edited it, select the draft and publish it.

-  Delete

   Select a subject in the list and click **More** and select **Delete** above the list to delete the subject.

-  Move Up/Down

   Locate a subject in the list and click |image2| or |image3| in the **Operation** column to move down or up the subject.

.. |image1| image:: /_static/images/en-us_image_0000002234241348.png
.. |image2| image:: /_static/images/en-us_image_0000002234081512.png
.. |image3| image:: /_static/images/en-us_image_0000002234081480.png
