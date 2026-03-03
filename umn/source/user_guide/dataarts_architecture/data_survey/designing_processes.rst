:original_name: dataartsstudio_01_0631.html

.. _dataartsstudio_01_0631:

Designing Processes
===================

Business Process Architecture (BPA) is developed based on value streams, and is used to guide and standardize the management of requirements and ensure the efficiency of business requirement handling, analysis, and delivery. BPA prioritizes high-value requirements, which maximizes the business value, assists in business operations, and facilitates goal achievement.

Creating a Process
------------------

Design a process that consists of three to seven levels. For details about how to change the process levels, see :ref:`Process Levels <dataartsstudio_01_0621__li3683768289>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Architecture**.

#. Choose **Data Survey** > **Processes** in the left navigation bar. Click |image1| to create a process. When creating a process for the first time, perform the operation under the root node.


   .. figure:: /_static/images/en-us_image_0000002234238020.png
      :alt: **Figure 1** Process design

      **Figure 1** Process design

#. In the dialog box displayed, set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269197457.png
      :alt: **Figure 2** Creating a process

      **Figure 2** Creating a process

   .. table:: **Table 1** Parameters for creating a process

      +----------------+-------------------------------------------------------------------------------------------------+
      | Parameter      | Description                                                                                     |
      +================+=================================================================================================+
      | Process        | Process name. Newline characters and the following characters are not allowed: / \\ < > % " ' ; |
      +----------------+-------------------------------------------------------------------------------------------------+
      | Owner          | Process owner. You can enter the name of an owner or select an existing owner.                  |
      +----------------+-------------------------------------------------------------------------------------------------+
      | Parent Process | Parent process of the process                                                                   |
      +----------------+-------------------------------------------------------------------------------------------------+
      | Description    | A description of the process.                                                                   |
      +----------------+-------------------------------------------------------------------------------------------------+

#. Repeat the preceding steps in sequence to create more processes or subprocesses. Generally, you must design processes from L1 to L3. The first layer is identified as L1, the second layer as L2, and the third layer as L3.

   The following figure shows an example.


   .. figure:: /_static/images/en-us_image_0000002234078172.png
      :alt: **Figure 3** Process design example

      **Figure 3** Process design example

.. _dataartsstudio_01_0631__section85344063613:

Exporting a Process
-------------------

You can export the processes that have been created in DataArts Architecture to files.

#. On the DataArts Architecture page, choose **Data Survey** > **Processes** in the left navigation pane.
#. Click **Export** above the process list. After a few seconds, a message is displayed in the upper right corner of the page, indicating that the process is exported. You can view the export process.

   .. note::

      A **process** has a hierarchy. You can export only data of all levels. All processes rather than the ones you select will be exported.

Importing a Process
-------------------

#. On the DataArts Architecture page, choose **Data Survey** > **Processes** in the left navigation pane.

#. Click **Import** above the process list.

#. In the dialog box displayed, set **Update Existing Data**, click **Select File**, and click **Upload**.


   .. figure:: /_static/images/en-us_image_0000002269117385.png
      :alt: **Figure 4** Importing a process

      **Figure 4** Importing a process

   .. table:: **Table 2** Parameters for importing a process

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================================================================================================================+
      | Update Existing Data              | Whether to update the existing processes of DataArts Architecture. The options are as follows:                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   | -  **No**: If you select this option, the existing process will not be updated.                                                                                                                                                                                                                   |
      |                                   | -  **Yes**: If you select this option, the existing process will be updated.                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   | During the import, only process creation and update are allowed.                                                                                                                                                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Upload File                       | Select the file to import.                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   | You can use either of the following methods to obtain the file to import:                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   | -  **Downloading the process template and filling in it**                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   |    On the **Import** tab page, click **Process Template** to download the template, set related parameters in the template based on service requirements, save the settings, and upload the file. See :ref:`Table 3 <dataartsstudio_01_0631__table7300412102511>` for template parameter details. |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   | -  **Exporting a process**                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   |    You can export the processes created in DataArts Architecture of a DataArts Studio instance to an Excel file. Then, import the Excel file. For details, see :ref:`Exporting a Process <dataartsstudio_01_0631__section85344063613>`.                                                           |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   :ref:`Table 3 <dataartsstudio_01_0631__table7300412102511>` describes the parameters in the downloaded template. Parameters whose names start with an asterisk (``*``) are mandatory, and parameters whose names do not start with an asterisk (``*``) are optional. One record is required for one process.

   .. _dataartsstudio_01_0631__table7300412102511:

   .. table:: **Table 3** Parameters in the process import template

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================+
      | Process                           | If it is a level 1 process, this field can be left blank.                                                                                                                      |
      |                                   |                                                                                                                                                                                |
      |                                   | If it is not, this field is mandatory. If there are multiple processes, separate them with slashes (/), for example, **Integrated Product Development/Development Lifecycle**. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Name                            | Process name.                                                                                                                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Owner                           | Process owner. You can enter the name of an owner or select an existing owner.                                                                                                 |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the process.                                                                                                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. The import result is displayed on the **Last Import** tab page in the **Import Process** dialog box. If the import is successful, click **Close**. If the import fails, you can view the failure cause, correct the template file, and upload it again.

Deleting a Process
------------------

You can delete the processes that are no longer used. Deleted processes cannot be recovered. Exercise caution when performing this operation. If a process has subdirectories or subprocesses, you must delete the subdirectories or subprocesses first.

#. On the DataArts Architecture page, choose **Data Survey** > **Processes** in the left navigation pane.
#. In the process list, select the target process and click **Delete** above the process list.
#. In the **Delete Process** dialog box displayed, confirm the process information and click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000002234238016.png
