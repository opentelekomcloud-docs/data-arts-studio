:original_name: dataartsstudio_01_0616.html

.. _dataartsstudio_01_0616:

Creating Atomic Metrics
=======================

An atomic metric is an abstract set of the statistical logic and specific algorithms. To ensure consistency between definitions and R&D, metric definitions determine the statistical logic (or the computing logic), without using ETLs to perform secondary R&D. This improves R&D efficiency and ensures consistency of statistical results.

**Atomic metrics** are generated based on dimension tables and fact tables of a multidimensional model. The objects and the finest data granularity of an atomic metric are consistent with those of the multidimensional model.

An atomic metric usually consists of one measure and attributes related to this measure, all of which aim to support agile self-service consumption of the metric. Agile self-service consumption means that business users can access and use metrics fast by themselves without relying on the IT department or data team for complex query and computation. Atomic metrics are basic and easy to understand. You can use them to create reports, query requests, and analysis requests. Using atomic metrics, you can flexibly combine and compute existing basic data to meet your requirements.

Context
-------

Atomic metrics come from fact tables and dimension tables.

-  An atomic metric is a data component defined for constructing a derivative metric required by application statistical analysis. An atomic metric can be created based on fact table details or dimension tables.
-  A derivative metric does not have a direct source table. It belongs to the source table of the original atomic metrics that are combined into the derivative metric.

Atomic metrics and derivative metrics interact in specific ways.

-  After the computing logic of an atomic metric takes effect, the related derivative metric is updated directly.
-  An atomic metric referenced by any derivative metrics cannot be deleted.
-  The code of an atomic metric referenced by any derivative metrics can be changed.
-  The change of an atomic metric affects related derivative metrics.

Constraints
-----------

A maximum of 5,000 atomic metrics can be created in a workspace.

Prerequisites
-------------

You have created and published a fact table, and the fact table has been approved. For details, see :ref:`Creating Fact Tables <dataartsstudio_01_0612>`.

.. _dataartsstudio_01_0616__en-us_topic_0169427298_section2012674313338:

Creating and Publishing an Atomic Metric
----------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Architecture**.

#. On the DataArts Architecture page, choose **Metrics** > **Technical Metrics** in the left navigation pane. On the displayed page, click the **Atomic Metrics** tab.

#. .. _dataartsstudio_01_0616__li1888114467397:

   Select a subject from the subject tree on the left and click **Create**.

#. On the **Create Atomic Metric** page, set the parameters described in :ref:`Table 1 <dataartsstudio_01_0616__table1288254693916>` and click **Publish**.


   .. figure:: /_static/images/en-us_image_0000002269121141.png
      :alt: **Figure 1** Creating an atomic metric

      **Figure 1** Creating an atomic metric

   .. _dataartsstudio_01_0616__table1288254693916:

   .. table:: **Table 1** Parameters for creating an atomic metric

      +------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Description                                                                                                                                                                                                                                                                                                                           |
      +==================+=======================================================================================================================================================================================================================================================================================================================================+
      | \*Metric Name    | Newline characters and the following characters are not allowed: \\ < > % " ' ;                                                                                                                                                                                                                                                       |
      +------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Metric Code    | Metric codes must start with letters. Only letters, numbers, and underscores (_) are allowed.                                                                                                                                                                                                                                         |
      +------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data Table     | Select a published fact table from the drop-down list box. If there are many tables, you can enter a table name in the text box to search for the desired fact table. If no fact table is available, create one. See :ref:`Creating and Publishing a Fact Table <dataartsstudio_01_0612__en-us_topic_0171848092_section21241338088>`. |
      +------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Subject        | The subject to which the atomic metric belongs. After a fact table is selected, the information about the subject to which the fact table belongs is automatically displayed. You can also click **Select** to select a subject.                                                                                                      |
      +------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Set Expression | Select the required functions and fields and set the expression. For details about the functions, see :ref:`Functions <dataartsstudio_01_0616__section1323572022818>`.                                                                                                                                                                |
      +------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description      | A description of the atomic metric to create. Up to 600 characters are supported.                                                                                                                                                                                                                                                     |
      +------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. .. _dataartsstudio_01_0616__li1188234618398:

   In the displayed dialog box, select a reviewer and click **OK** to submit a request.

   .. note::

      If you have been added as a reviewer, you can select **Auto-review** and click **OK**. After the request is approved, the status changes to **Published**.

      If you select multiple reviewers, the status changes to **Published** only after all reviewers have approved the publishing request. If any reviewer rejects the request, the status is **Rejected**.

#. (Optional) Create and publish other atomic metrics by repeating :ref:`3 <dataartsstudio_01_0616__li1888114467397>` to :ref:`5 <dataartsstudio_01_0616__li1188234618398>`.

#. Wait for the reviewer to approve the application.

   After the application is approved, the atomic metric is created.

   Click the name of an atomic metric to view its details, relationship diagram, publishing history, and review history.

   In the relationship diagram, you can view the lineage diagram of the atomic metric.

   In the release history, you can view the differences between historical versions.

Managing an Atomic Metric
-------------------------

#. On the DataArts Architecture page, choose **Metrics** > **Technical Metrics** in the left navigation pane. On the displayed page, click the **Atomic Metrics** tab.


   .. figure:: /_static/images/en-us_image_0000002234241764.png
      :alt: **Figure 2** Managing an atomic metric

      **Figure 2** Managing an atomic metric

#. Manage your atomic metrics as required. Refer to the following table for details.

   .. table:: **Table 2** Operations

      +----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Operation            | Helpful Link                                                                                                          |
      +======================+=======================================================================================================================+
      | Create               | :ref:`Creating and Publishing an Atomic Metric <dataartsstudio_01_0616__en-us_topic_0169427298_section2012674313338>` |
      +----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Edit                 | :ref:`3 <dataartsstudio_01_0616__li2054015512277>`                                                                    |
      +----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Publish              | :ref:`4 <dataartsstudio_01_0616__li1354145162717>`                                                                    |
      +----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | View Publish History | :ref:`5 <dataartsstudio_01_0616__li228701155712>`                                                                     |
      +----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Suspend              | :ref:`6 <dataartsstudio_01_0616__li65410542714>`                                                                      |
      +----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Delete               | :ref:`7 <dataartsstudio_01_0616__li95419562710>`                                                                      |
      +----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Import               | :ref:`8 <dataartsstudio_01_0616__li1366810124116>`                                                                    |
      +----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Export               | :ref:`9 <dataartsstudio_01_0616__li192260171313>`                                                                     |
      +----------------------+-----------------------------------------------------------------------------------------------------------------------+

#. .. _dataartsstudio_01_0616__li2054015512277:

   Edit an atomic metric.

   a. Click **Edit** to the right of the target atomic metric.
   b. On the page displayed, edit the atomic metric as required.
   c. Click **Publish**. If you do not want to immediately publish the atomic metric that you edited, click **Save** and you can publish it later.

#. .. _dataartsstudio_01_0616__li1354145162717:

   Publish an atomic metric.

   a. Click **Publish** to the right of the target atomic metric.
   b. In the **Submit for Publication** dialog box displayed, select a reviewer from the drop-down list box.
   c. Click **OK**.

#. .. _dataartsstudio_01_0616__li228701155712:

   View the publish history.

   a. Select the target atomic metric in the list and choose **More** > **View History**.
   b. On the **History** tab page, you can view the publish history and version comparison information of the metric.

#. .. _dataartsstudio_01_0616__li65410542714:

   Suspend an atomic metric.

   a. Click **Suspend** to the right of the target atomic metric.
   b. In the **Submit for Suspension** dialog box displayed, select a reviewer from the drop-down list box.
   c. Click **OK**.

      .. note::

         Atomic metrics cannot be suspended or deleted if they are referenced by any derivative metrics.

#. .. _dataartsstudio_01_0616__li95419562710:

   Delete an atomic metric.

   a. Select the target atomic metric and choose **More** > **Delete** in the upper left corner.
   b. In the dialog box displayed, confirm the information and click **Yes**.

#. .. _dataartsstudio_01_0616__li1366810124116:

   Import

   You can import atomic metrics to the system quickly.

   a. Above the atomic metric list, click **More** and select **Import**.


      .. figure:: /_static/images/en-us_image_0000002269201209.png
         :alt: **Figure 3** Importing atomic metrics

         **Figure 3** Importing atomic metrics

   b. Download the atomic metric template, and edit and save it.

   c. Choose whether to update existing data.

      .. note::

         If a code in the template already exists in the system, the data is considered duplicate.

      -  **No**: If the data to be imported already exists in the system, the existing data in the system will not be replaced.
      -  **Yes**: If the data to be imported already exists in the system:

         -  If the existing data in the system is in draft state, the data will be replaced and new draft data will be generated.
         -  If the existing data in the system is in published state, expanded data will be generated.

   d. Click **Select File** and select the edited template to import.

   e. Click **Upload**. When the template is uploaded, the **Last Import** page is displayed. You can view the imported data.

   f. Click **Close**.

#. .. _dataartsstudio_01_0616__li192260171313:

   Export atomic metrics.

   You can export atomic metrics to a local file.

   a. In the atomic metric list, select the metric to be exported.
   b. Above the atomic metric list, click **More** and select **Export**.

   .. note::

      -  You can export all the atomic metrics of a subject by selecting the subject in the subject list on the left.
      -  You can export all the atomic metrics of a workspace, as long as there are no more than 5,000 atomic metrics in the workspace.

.. _dataartsstudio_01_0616__section1323572022818:

Functions
---------

When creating an atomic metric, you need to set an expression based on functions. :ref:`Table 3 <dataartsstudio_01_0616__table1121205810561>` lists some aggregate functions.

.. _dataartsstudio_01_0616__table1121205810561:

.. table:: **Table 3** Aggregate functions

   +------------------------+---------------+----------------------------------------------------------------------+
   | Function               | Expression    | Description                                                          |
   +========================+===============+======================================================================+
   | avg(col)               | avg()         | Returns the average value.                                           |
   +------------------------+---------------+----------------------------------------------------------------------+
   | corr(col1, col2)       | corr()        | Returns the coefficient of correlation of a pair of numeric columns. |
   +------------------------+---------------+----------------------------------------------------------------------+
   | count(``*``)           | count()       | Returns the total number of records.                                 |
   +------------------------+---------------+----------------------------------------------------------------------+
   | covar_pop(col1, col2)  | covar_pop()   | Returns the covariance of a pair of numeric columns.                 |
   +------------------------+---------------+----------------------------------------------------------------------+
   | covar_samp(col1, col2) | covar_samp()  | Returns the sample covariance of a pair of numeric columns.          |
   +------------------------+---------------+----------------------------------------------------------------------+
   | max(col)               | max()         | Returns the maximum value.                                           |
   +------------------------+---------------+----------------------------------------------------------------------+
   | min(col)               | min()         | Returns the minimum value.                                           |
   +------------------------+---------------+----------------------------------------------------------------------+
   | stddev_pop(col)        | stddev_pop()  | Returns the deviation of a specified column.                         |
   +------------------------+---------------+----------------------------------------------------------------------+
   | stddev_samp(col)       | stddev_samp() | Returns the sample deviation of a specified column.                  |
   +------------------------+---------------+----------------------------------------------------------------------+
   | sum(col)               | sum()         | Returns the sum of the values in a column.                           |
   +------------------------+---------------+----------------------------------------------------------------------+
   | var_samp(col)          | var_samp()    | Returns the sample variance of a specified column.                   |
   +------------------------+---------------+----------------------------------------------------------------------+

You can click functions in the **Function** column next to **Set Expression** on the **Basic Settings** page on the **Create Atomic Metric** page.


.. figure:: /_static/images/en-us_image_0000002269201193.png
   :alt: **Figure 4** Functions

   **Figure 4** Functions
