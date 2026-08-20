:original_name: dataartsstudio_01_0715.html

.. _dataartsstudio_01_0715:

Creating a Data Quality Rule
============================

DataArts Quality can monitor offline data, in which quality rules play a vital role. There are 34 built-in rule templates, such as database-level, table-level, field-level, cross-source, and cross-field rule templates.

.. _dataartsstudio_01_0715__en-us_topic_0141836095_table764712462277:

.. table:: **Table 1** System built-in rule templates

   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Rule Type          | Dimension     | Template                                                          | Applicable Engine                                                    | Description                                                                                                                                                                                                          |
   +====================+===============+===================================================================+======================================================================+======================================================================================================================================================================================================================+
   | Database-level     | Integrity     | Database null value scan                                          | DLI, DWS, HIVE, SparkSQL, CLICKHOUSE, ORACLE, RDS, DORIS             | Calculates the number of rows with empty field values in each table in the database. The result is displayed by field.                                                                                               |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table-level        | Accuracy      | Table rows                                                        | DLI, DWS, HIVE, SparkSQL, CLICKHOUSE, HETUENGINE, ORACLE, RDS, DORIS | Calculates the number of rows in a data table.                                                                                                                                                                       |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | Integrity     | Data table null value scan                                        | DLI, DWS, HIVE, SparkSQL, CLICKHOUSE, HETUENGINE, ORACLE, RDS, DORIS | Calculates the number of rows with empty field values in each table. The result is displayed by field.                                                                                                               |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | Validity      | Fluctuation rate in the last day                                  | DLI, DWS, HIVE, SparkSQL, CLICKHOUSE, HETUENGINE, ORACLE, RDS, DORIS | Calculates the size, field groups, and related fluctuation rate of a data table in the last day.                                                                                                                     |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Fluctuation rate in the last seven days                           |                                                                      | Calculates the size, field groups, and related fluctuation rate of a data table in the last seven days.                                                                                                              |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Fluctuation rate in the last 30 days                              |                                                                      | Calculates the size, field groups, and related fluctuation rate of a data table in the last 30 days.                                                                                                                 |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Field-level        | Uniqueness    | Field with a unique value                                         | DLI, DWS, HIVE, SparkSQL, CLICKHOUSE, HETUENGINE, ORACLE, RDS, DORIS | Calculates the number of rows in a data table in which a specified field has a unique value.                                                                                                                         |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Field with duplicate values                                       |                                                                      | Calculates the number of rows in a data table in which a specified field has duplicate values. If the field has multiple different duplicate values, the total number of duplicate values is the calculation result. |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Unique combination of multiple fields                             | HIVE, SparkSQL, DLI, DWS, HETUENGINE                                 | Checks whether the combination of multiple fields in a table is unique. A maximum of 10 fields can be combined.                                                                                                      |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Multi column uniqueness verification ignore null                  |                                                                      | Checks whether the combination of multiple fields in a table is unique. A maximum of 10 fields can be combined. Null values are counted in valid rows.                                                               |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | Integrity     | Field with a null value                                           | DLI, DWS, HIVE, SparkSQL, CLICKHOUSE, HETUENGINE, ORACLE, RDS, DORIS | Calculates the number of rows in a data table in which a specified field has a null value.                                                                                                                           |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | Accuracy      | Average field value                                               | DLI, DWS, HIVE, SparkSQL, CLICKHOUSE, HETUENGINE, ORACLE, RDS, DORIS | Calculates the average value of a specified field in a data table.                                                                                                                                                   |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Total field values                                                |                                                                      | Calculates the total values of a specified field in a data table.                                                                                                                                                    |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Maximum field value                                               |                                                                      | Calculates the maximum value of a specified field in a data table.                                                                                                                                                   |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Minimum field value                                               |                                                                      | Calculates the minimum value of a specified field in a data table.                                                                                                                                                   |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | Effectiveness | ID card verification                                              | DLI, DWS, HIVE, SparkSQL, CLICKHOUSE, HETUENGINE, ORACLE, RDS, DORIS | Checks validity of a specified field in a data table based on built-in regular expression rules. If the field is empty, it is invalid.                                                                               |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Mailbox verification                                              |                                                                      | Checks validity of a specified field in a data table based on built-in regular expression rules.                                                                                                                     |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Regular expression verification                                   |                                                                      | Checks validity of a specified field in a data table based on a custom regular expression.                                                                                                                           |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | IP address verification                                           |                                                                      | Checks validity of a specified field in a data table based on built-in regular expression rules.                                                                                                                     |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Phone number format verification                                  |                                                                      | Checks validity of a specified field in a data table based on built-in regular expression rules.                                                                                                                     |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Postal code format verification                                   |                                                                      | Checks validity of a specified field in a data table based on built-in regular expression rules.                                                                                                                     |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Date format verification                                          |                                                                      | Checks validity of a specified field in a data table based on built-in regular expression rules.                                                                                                                     |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Validity verification                                             |                                                                      | Checks validity of a specified field in a data table based on a custom regular expression.                                                                                                                           |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Enumerated value verification                                     |                                                                      | Checks validity of a specified field in a data table based on a custom enumerated value.                                                                                                                             |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Field length verification                                         | DLI, DWS, HETUENGINE                                                 | Checks whether the length of a field in the table is within the allowed range.                                                                                                                                       |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Field value range verification                                    |                                                                      | Checks whether the value of a field in the table is within the allowed range.                                                                                                                                        |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Field time verification                                           |                                                                      | Checks whether the time of a field in the table is within the allowed range.                                                                                                                                         |
   |                    |               |                                                                   |                                                                      |                                                                                                                                                                                                                      |
   |                    |               |                                                                   |                                                                      | Currently, only fields of the date and timestamp types are supported. Fields of the time type are not supported.                                                                                                     |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Ignoring of null values in enumerated value verification          |                                                                      | Verifies the validity of a specified field in a data table based on a custom enumerated value. Null values are counted in valid rows.                                                                                |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Ignoring of null values in regular expression verification        |                                                                      | Checks validity of a specified field in a table based on a custom regular expression. Null values are counted in valid rows.                                                                                         |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Ignoring of case in enumerated value verification                 | DLI, DWS, HETUENGINE                                                 | Checks validity of a specified field in a table based on a custom enumerated value. Case-sensitive values are counted in valid rows.                                                                                 |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    |               | Ignoring of null values and case in enumerated value verification |                                                                      | Checks validity of a specified field in a table based on a custom enumerated value. Null and case-sensitive values are counted in valid rows.                                                                        |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cross-field level  | Consistency   | Field consistency verification                                    | DLI, DWS, HIVE, SparkSQL, CLICKHOUSE, HETUENGINE, ORACLE, RDS, DORIS | Checks whether the value of a specified field in a data table is the same as that of the reference field from the same source.                                                                                       |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | Accuracy      | Cross-field time verification                                     | DLI, DWS, HETUENGINE                                                 | Checks whether the time relationship between a specified field in a table and the reference field meets the expectation.                                                                                             |
   |                    |               |                                                                   |                                                                      |                                                                                                                                                                                                                      |
   |                    |               |                                                                   |                                                                      | Currently, only fields of the date and timestamp types are supported. Fields of the time type are not supported.                                                                                                     |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cross-source level | Consistency   | Cross-source field consistency verification                       | HETUENGINE                                                           | Checks consistency between different fields from different data sources based on a Hetu connection.                                                                                                                  |
   +--------------------+---------------+-------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

You cannot edit built-in rule templates or view their release history.

If the built-in rule templates do not meet your requirements, you can create rules in either of the following ways:

.. note::

   Developers cannot randomly modify custom rule templates because they may be used by many users. To modify custom rule templates, contact the administrator.

-  Custom template: Choose **Quality Monitoring** > **Rule Templates** and click **Create**. The created rule template is automatically allocated the corresponding rule type (table level, field level, cross-field level, or multi-table and multi-field). The template type is custom. When creating a quality/comparison job, you can select **Table rule**, **Field rule**, **Cross-field rule**, or **Multi-table and multi-field rule** for **Rule Type**, and then you can select a custom template which supports export of abnormal data but does not support quality scoring.
-  Custom rule: When creating a quality job, set **Rule Type** to **Custom rule** and enter an SQL statement to define how to monitor the quality of data objects.

   .. note::

      An SQL statement can contain multiple tables in the same database, but not tables in different databases.

This section describes how to create a rule using a custom template. For details about how to create a custom rule, see :ref:`Creating a Data Quality Job <dataartsstudio_01_0712>`.

#. (Optional) In the left navigation pane, choose **Quality Monitoring** > **Rule Templates** and create a directory. If a directory exists, you do not need to create one. Note that rule templates, quality jobs, and comparison job are in the same directory.

   Currently, you can create a directory using either of the following methods:

   Click |image1| and enter a directory name in the displayed dialog box. In this way, you can create a maximum of seven layers of directories.


   .. figure:: /_static/images/en-us_image_0000002269115301.png
      :alt: **Figure 1** Creating a directory

      **Figure 1** Creating a directory

   You can also click |image2| to synchronize the :ref:`subjects in DataArts Architecture <dataartsstudio_01_0603>` as directories. (Only published subjects can be synchronized.) The synchronized directories are consistent with the published subjects in DataArts Architecture and are displayed by layer, such as |image3| and |image4|.

   .. note::

      a. The directories you create are not affected by the synchronization. If the name of a created directory conflicts with that of a subject:

         -  If they conflict during the first synchronization, a subject layer (such as |image5| and |image6|) is added to the name of the directory.
         -  If they conflict after the subject is modified, the synchronization fails.

      b. Changes to subjects or subject layers in DataArts Architecture cannot be automatically synchronized. You must click |image7| again to synchronize them.

         If a subject or subject layer in DataArts Architecture is deleted and synchronized to DataArts Quality, the corresponding directory will not be deleted. Instead, the subject attributes will be deleted from the directory.

      c. After the synchronization is complete, the system automatically displays the synchronization result details. You can view the names of the subjects that fail to be synchronized.


   .. figure:: /_static/images/en-us_image_0000002269115429.png
      :alt: **Figure 2** Synchronizing subjects from DataArts Architecture

      **Figure 2** Synchronizing subjects from DataArts Architecture

#. On the **Rule Templates** page, click **Create**.


   .. figure:: /_static/images/en-us_image_0000002234241568.png
      :alt: **Figure 3** Rule Template page

      **Figure 3** Rule Template page

#. In the dialog box displayed, enter the rule template name, select the rule matching dimension, define the SQL template, and describe the output result.

   -  **Dimension**: You can complete single-column, cross-column, cross-row, and cross-table analysis from six dimensions: completeness, validity, timeliness, consistency, accuracy, and uniqueness. When customizing a quality rule, select a dimension for rule matching.

   -  **Directory**: Select the directory where the rule template is located.

   -  **Tag**: Select desired tags from the list of tags that were defined Data Map. If Data Map is disabled, tags do not take effect.

   -  **Description**: Enter the description of the custom template.

   -  **Relationship**: Enter an SQL statement to search for data. **${Schema_Table1}** is the table selected for the quality/comparison job. **${Column1}** is the field selected in **${Schema_Table1}**. **${Schema_Table2}** exists only when a cross-field rule is defined and indicates the reference table selected for the quality job. **${Column2}** is the field selected in **${Schema_Table2}**. The system can verify the semantics of the relationship.

      .. note::

         If you enter non-digit characters for the relationship, only the execution result is generated. Four arithmetic operations and logical operations cannot be performed, and absolute values cannot be calculated.

         The relationship of a custom rule template can be defined for a maximum of 20 fields in 10 tables.

      A custom SQL expression must meet the following requirements:

      a. A relational expression supports a maximum of five columns.
      b. The input parameters of a maximum of two tables and two fields are supported. Note: **${Column1}** is the input parameter of **${Schema_Table1}**, and **${Column2}** is the input parameter of **${Schema_Table2}**. They are specified by built-in logic.
      c. If multiple rows are found, only the data in the first row is used.
      d. Periods (.) cannot be used to connect tables or fields. For example, ${Schema_Table2}.${Column1}.${Input_String1} is incorrect.
      e. A non-multi-table, non-multi-field expression supports parameters ${Schema_Table1}, ${Schema_Table2}, ${Column1}, and ${Column2}, but does not support table aliases.
      f. A multi-table, multi-field expression supports parameters ${Schema_Table1}, ${Schema_Table2}, ${Schema_Table3}, ${Schema_Table4}, ${Schema_Table5}, ${Column1}, ${Column2}, ${Column3}, to until ${Column20}, ${Input_String1}, ${Input_String2}, ${Input_String3}, ${Input_String4}, and ${Input_String5}, but does not support table aliases.

      For example, to count the number of rows in a table, enter **select count(${Column1}) from ${Schema_Table1}**. The value of **${Column1}** is generated by clicking **Add Field Parameter**, and the value of **${Schema_Table1}** is generated by clicking **Add Database/Table Parameter**.

      Click |image8| and enable **Add Input Parameter** to flexibly configure input parameters in SQL statements.

      For example, if a field matches the number of rows in the configuration table, enter **select count(1) from ${Schema_Table1} where ${Column1} regexp ${Input_String1}**. Click **Add Field Parameter** to generate **${Column1}** and click **Add Database/Table Parameter** to generate **${Schema_Table1}**.

      .. note::

         When creating a multi-table and multi-field rule template, you can add a maximum of five database/table parameters, 20 field parameters, and five input parameters.

   -  **Output Description**: Enter the description of each column in the SQL statement execution result, which corresponds to the output defined by the relationship in sequence. Column descriptions are separated by commas (,).

      For example, if the relationship is set to **select max(${Column1}),min(${Column2}) from ${Schema_Table1}**, the output result is **Maximum value,Minimum value** (pay attention to the input order).

   -  **Scoring Formula**: Enter a scoring formula. After you enter a scoring formula, the template can be used for quality scoring. The score and rules are displayed in the quality report.

      For example,, you can enter **${1}/${2}**, where **${1}** indicates the output of the first column and **${2}** indicates that of the second column. The return value of the formula ranges from 0 to 1.

   -  **Abnormal Table Template**: You need to enter a complete SQL statement to specify the abnormal data to be exported. You can click **Add Database/Table Parameter** to generate **${Schema_Table1}** which indicates the name of the anomaly table. You can click **Add Field Parameter** to generate **${Column1}** which indicates a field in the anomaly table. You can click **Add Output Parameter** to generate **${Output_Columns}** which indicates the abnormal data to be output from the anomaly table. The system can verify the semantics of the abnormal table template.

      .. note::

         If you enable **Multi-table and multi-field rule**, **Abnormal Table Template** is unavailable.

   For example, in a table involving amount, the **is_test** field identifies whether a piece of data is test data (**0** indicates formal data and **1** indicates test data). If you want to calculate the minimum, maximum, average, and total amount of formal data, you can define the custom template as follows:

   -  **Dimension**: Select **Accuracy**.

   -  **Directory**: Retain the default value **/All/**.

   -  **Description**: Enter **Calculate the minimum, maximum, average, and total amount of formal data**.

   -  **Relationship**: Enter the following SQL statement to calculate the minimum, maximum, average, and total amount of formal data. **${Schema_Table1}** indicates the table selected in the quality job, and **${Column1}** indicates the field selected in **${Schema_Table1}**.

      .. code-block::

         select
             min(${Column1}),
             max(${Column1}),
             ROUND(avg(${Column1}),2),
             sum(${Column1})
         from ${Schema_Table1}
             where is_test='0'

   -  **Output Description**: Enter **minimum, maximum, average, and total amount**.

   -  **Abnormal Table Template**: Enter the following SQL statement to export the **${Output_Columns}** columns in which the amount is less than 10 as abnormal table data. **${Output_Columns}** indicates the field selected for the abnormal table parameter in the quality job.

      .. code-block::

         select ${Output_Columns} from ${Schema_Table1} where ${Column1}<10 and is_test='0'


   .. figure:: /_static/images/en-us_image_0000002234241524.png
      :alt: **Figure 4** Key parameters for a custom rule template

      **Figure 4** Key parameters for a custom rule template

#. After you click **Yes**, the system publishes the rule template by default. The default version is V1.0.

Editing Rule Templates
----------------------

.. note::

   Developers cannot randomly modify custom rule templates because they may be used by many users. To modify custom rule templates, contact the administrator.

You can edit and publish rule templates. You can take a historical version offline and migrate the jobs associated with the historical version to be taken offline to the new version. The operations are as follows:

.. note::

   The page for editing a rule template contains parameters **Version** and **Associated Jobs**.

#. On the DataArts Quality console, choose **Quality Monitoring** > **Rule Templates** in the left navigation pane. Locate the target rule template in the displayed list and click **Edit** in the **Operation** column to enter the rule template editing page.


   .. figure:: /_static/images/en-us_image_0000002269200985.png
      :alt: **Figure 5** Editing a rule template

      **Figure 5** Editing a rule template

#. Dimensions and output description can be modified, and relationships can be redefined.

#. Click **Publish**. In the displayed dialog box, select the version type, set the version name, and click **OK**.

   .. note::

      -  When publishing a new version, you must change the version name.
      -  When publishing the current version, you do not have to change the version name. The earlier version automatically becomes a historical version.


   .. figure:: /_static/images/en-us_image_0000002269120937.png
      :alt: **Figure 6** Publishing a new version

      **Figure 6** Publishing a new version

#. After the rule template is submitted for publishing, you can click **View Publish History** in the **Operation** column. You can view the changes of versions, change version names, and suspend versions.


   .. figure:: /_static/images/en-us_image_0000002234081672.png
      :alt: **Figure 7** Publish History page

      **Figure 7** Publish History page

#. To suspend a historical version, click **Suspend** on the right of the historical version.

   -  If the version is not associated with any job, click **OK** to suspend it.

   -  If the version has associated jobs, select a new version, associate the jobs with the new version, and click **OK**.


      .. figure:: /_static/images/en-us_image_0000002269120897.png
         :alt: **Figure 8** Migrating and suspending a version

         **Figure 8** Migrating and suspending a version

#. On the **Version Comparison** tab page, you can compare the versions to see their differences.


   .. figure:: /_static/images/en-us_image_0000002269120885.jpg
      :alt: **Figure 9** Version comparison

      **Figure 9** Version comparison

Exporting Rule Templates
------------------------

To export custom rule templates, perform the following steps (you can export a maximum of 200 rule templates at a time):

#. In the left navigation pane, choose **Quality Monitoring** > **Rule Templates**, and select the templates to export in the right pane.
#. Click **Export**. The **Export Rule Template** dialog box is displayed.
#. Click **Export** to switch to the **Export Records** tab.
#. In the list of exported files, locate an exported template and click **Download** in the **Operation** column to download the Excel file of the rule template to the local PC.

Importing Rule Templates
------------------------

You can import a file containing a maximum of 4 MB data.

#. In the left navigation pane, choose **Quality Monitoring** > **Rule Templates**. In the right pane, click **Import**.


   .. figure:: /_static/images/en-us_image_0000002234241512.png
      :alt: **Figure 10** Importing rule templates

      **Figure 10** Importing rule templates

#. On the **Import Configurations** tab page, set **Duplicate Name Policy**.

   -  **Terminate**: If template names repeat, all templates will fail to be imported.
   -  **Skip**: If template names repeat, the templates will still be imported.

#. Click **Upload** and select the prepared data file.

   .. note::

      Edit the data file using either of the following methods:

      -  (Recommended) Click **Export** to export data and import the data to the system directly or import it after modification.
      -  Click **Download Template**, fill in the template with the data to import, and import the data to the system.

#. Configure the mapped resource for the catalog and select the directory where rule template has been imported. If you do not configure the resource mapping, the original mapping is used by default.


   .. figure:: /_static/images/en-us_image_0000002269120961.png
      :alt: **Figure 11** Configuring the resource mapping

      **Figure 11** Configuring the resource mapping

#. Click **Import** to import the Excel template to the system.

#. Click the **Import Records** tab to view the import records.

.. |image1| image:: /_static/images/en-us_image_0000002234076184.png
.. |image2| image:: /_static/images/en-us_image_0000002234236024.png
.. |image3| image:: /_static/images/en-us_image_0000002269115357.png
.. |image4| image:: /_static/images/en-us_image_0000002269115421.png
.. |image5| image:: /_static/images/en-us_image_0000002269115305.png
.. |image6| image:: /_static/images/en-us_image_0000002269115401.png
.. |image7| image:: /_static/images/en-us_image_0000002234076080.png
.. |image8| image:: /_static/images/en-us_image_0000002269120949.png
