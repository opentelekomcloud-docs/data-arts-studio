:original_name: dataartsstudio_01_4505.html

.. _dataartsstudio_01_4505:

Viewing Data Quality Reports
============================

You can query the quality reports of business metrics and data objects to determine whether their quality meets the requirements.

.. note::

   Quality reports include technical reports and business reports.

   Technical reports measure the execution results of quality jobs and contain data connections, databases, table names, and scores.

   Business reports measure the execution results of quality jobs associated with subjects in DataArts Architecture and contain subject area groups, subject areas, business objects, table names, and scores.

Viewing Data Quality Scores in a Technical Report
-------------------------------------------------

The full quality score can be set to 5, 10, or 100 points. By default, a five-point scale is used for quality scoring based on table-associated rules. Scores in different dimensions, such as tables and databases, are calculated based on the weighted average values of rule scores in different dimensions.

You can query the scores of databases, tables, and table-associated rules. For details on the calculation formulas, see :ref:`Table 1 <dataartsstudio_01_4505__table47512091019>`.

.. _dataartsstudio_01_4505__table47512091019:

.. table:: **Table 1** Formulas for calculating scores

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Object                            | Formula                                                                                                                                                                                                                                                     |
   +===================================+=============================================================================================================================================================================================================================================================+
   | Rule                              | When a quality job that contains a percentage-related rule (either built-in or custom) is created, a quality report can be generated.                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                             |
   |                                   | -  Percentage-related rules can be classified into positive rules and negative rules. For a positive rule, the higher the percentage is, the better the data quality is. For a negative rule, the higher the percentage is, the poorer the data quality is. |
   |                                   |                                                                                                                                                                                                                                                             |
   |                                   |    Rules that contain the unique value percentage, duplicate value percentage, and valid percentage are positive rules, and rules that contain the null value percentage are negative rules.                                                                |
   |                                   |                                                                                                                                                                                                                                                             |
   |                                   | -  Positive rule score = Number of data rows that meet the rule/Total number of data rows x 5.                                                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                                             |
   |                                   | -  Negative rule score = (1 - Number of data rows that meet the rule/Total number of data rows) x 5.                                                                                                                                                        |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table                             | The table score is calculated as follows: ∑(Scores of all rules associated with the table x Rule weight)/∑Rule weight.                                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Database                          | Weighted average value of the scores of all data tables in the database, that is, ∑Scores of all data tables in the database/Number of tables.                                                                                                              |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data connection                   | Weighted average value of the scores of all databases in the data connection, that is, ∑Scores of all databases in the data connection/Number of databases.                                                                                                 |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. On the DataArts Studio console, locate a workspace and click **DataArts Quality**.

#. Choose **Quality Monitoring** > **Quality Job** in the left navigation bar.

#. On the **Technical Reports** page, select a data connection and set a time range (a maximum of 30 days).


   .. figure:: /_static/images/en-us_image_0000002234079760.png
      :alt: **Figure 1** Selecting a data connection

      **Figure 1** Selecting a data connection

   .. note::

      -  Take the full score 5 points as an example. Points 4 to 5: excellent; 3 to 4: good; 2 to 3: unqualified; 1 to 2: poor; 0 to 1: very poor.
      -  The quality score data of a day is generated in the early morning of the next day.
      -  In the **Quality Scoring Changes** area, the solid line consists of the quality scores of the end date and the previous seven days, and the dashed line indicates the average quality score of these days.
      -  If the job is executed multiple times on a day, the last score is used as the quality score of the day.

#. Click the score link in the **Table Score** column to expand the scores of the rules associated with the table.


   .. figure:: /_static/images/en-us_image_0000002234079756.png
      :alt: **Figure 2** Viewing the rule score

      **Figure 2** Viewing the rule score

   .. note::

      The rule name is the name of the running instance. If a job runs multiple times, the name of the latest instance is used. If a running instance contains multiple sub-instances, each sub-instance has a record.

#. Click the score link in the **Rule Score** column to expand the scores of the fields associated with the rule.


   .. figure:: /_static/images/en-us_image_0000002269199013.png
      :alt: **Figure 3** Table-associated rule scores

      **Figure 3** Table-associated rule scores

Viewing Business Quality Scores in a Business Report
----------------------------------------------------

The full quality score can be set to 5, 10, or 100 points. By default, a five-point scale is used for quality scoring based on table-associated rules. The scores in different dimensions, such as tables, business objects, and subject areas, are calculated based on the weighted average values of rule scores in different dimensions.

You can query the quality scores of subject area groups, subject areas, business objects, tables, and table-associated rules. For details on the calculation formulas, see :ref:`Table 2 <dataartsstudio_01_4505__table13961141518393>`.

.. _dataartsstudio_01_4505__table13961141518393:

.. table:: **Table 2** Formulas for calculating scores

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Object                            | Formula                                                                                                                                                                                                                                                     |
   +===================================+=============================================================================================================================================================================================================================================================+
   | Rule                              | When a quality job that contains a percentage-related rule (either built-in or custom) is created, a quality report can be generated.                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                             |
   |                                   | -  Percentage-related rules can be classified into positive rules and negative rules. For a positive rule, the higher the percentage is, the better the data quality is. For a negative rule, the higher the percentage is, the poorer the data quality is. |
   |                                   |                                                                                                                                                                                                                                                             |
   |                                   |    Rules that contain the unique value percentage, duplicate value percentage, and valid percentage are positive rules, and rules that contain the null value percentage are negative rules.                                                                |
   |                                   |                                                                                                                                                                                                                                                             |
   |                                   | -  Positive rule score = Number of data rows that meet the rule/Total number of data rows x Full score (5, 10, or 100 points).                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                                             |
   |                                   | -  Negative rule score = (1 - Number of data rows that meet the rule/Total number of data rows) x Full score (5, 10, or 100 points).                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                             |
   |                                   | -  If the table is empty (the total number of rows is 0), the positive rule score is fixed at the full score and the negative rule score is fixed at 0 points.                                                                                              |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table                             | The table score is calculated as follows: ∑(Scores of all rules associated with the table x Rule weight)/∑Rule weight.                                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Business object                   | Weighted average value of the scores of all tables under the business object, that is, ∑Scores of all tables under the business object/Number of tables.                                                                                                    |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Subject area                      | Weighted average value of scores of all business objects in the subject area, that is, ∑Scores of all business objects in the subject area/Number of business objects.                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Subject area group                | Average weighted value of the scores of all subject areas in the group, that is, ∑Scores of all subject areas in the group/Number of subject areas.                                                                                                         |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. On the DataArts Studio console, locate a workspace and click **DataArts Quality**.

#. Choose **Quality Monitoring** > **Quality Job** in the left navigation bar.

#. Click the **Business Reports** tab, and select a subject and an end date to query the quality scores of the end date and the previous seven days, as shown in :ref:`Figure 4 <dataartsstudio_01_4505__fig216416433485>`.

   .. _dataartsstudio_01_4505__fig216416433485:

   .. figure:: /_static/images/en-us_image_0000002269199041.png
      :alt: **Figure 4** Business object

      **Figure 4** Business object

   .. note::

      -  Take the full score 5 points as an example. Points 4 to 5: excellent; 3 to 4: good; 2 to 3: fair; 1 to 2: qualified; 0 to 1: unqualified.
      -  The quality score data of a day is generated in the early morning of the next day.
      -  In the **Quality Scoring Changes** area, the solid line consists of the quality scores of the end date and the previous seven days, and the dashed line indicates the average quality score of these days.
      -  If the job is executed multiple times on a day, the last score is used as the quality score of the day.

#. Click the score link in the **Table Score** column to expand the scores of the rules associated with the table.

#. Click the score link in the **Rule Score** column to expand the scores of the fields associated with the rule.


   .. figure:: /_static/images/en-us_image_0000002234239580.png
      :alt: **Figure 5** Table-associated rule scores

      **Figure 5** Table-associated rule scores

Exporting Quality Reports
-------------------------

You can export a quality report in either of the following ways:

-  If the OBS service is available, the data is exported to the associated OBS bucket by default.

   .. note::

      -  As quality reports contain a large amount of data, a single exported file can contain a maximum of 2,000 fields. Therefore, there may be multiple exported files in the OBS bucket.
      -  The exported report is available only in the current workspace.

-  If the OBS service is unavailable, the data is exported to a local path by default.

#. On the DataArts Studio console, locate a workspace and click **DataArts Quality**.

#. Choose **Quality Monitoring** > **Quality Job** in the left navigation bar.


   .. figure:: /_static/images/en-us_image_0000002234079768.png
      :alt: **Figure 6** Quality Reports page

      **Figure 6** Quality Reports page

#. In the upper right corner of the page, click **Export**.


   .. figure:: /_static/images/en-us_image_0000002234079724.png
      :alt: **Figure 7** Export

      **Figure 7** Export


   .. figure:: /_static/images/en-us_image_0000002234239564.png
      :alt: **Figure 8** Export to OBS

      **Figure 8** Export to OBS

#. Click the **Export Records** tab to view the export result. You can click **Download** to download a report. If the exported report file is too large, you can directly download the file.


   .. figure:: /_static/images/en-us_image_0000002234239556.png
      :alt: **Figure 9** Export Records

      **Figure 9** Export Records

Refreshing Data Immediately
---------------------------

After a quality job and a comparison job are complete, you can refresh data immediately to obtain the temporary data quality report from 00:00 to the current time. In the early morning of the next day, the quality report scheduling task starts to be executed, which generates the full data quality report for the previous day.

#. On the DataArts Studio console, locate a workspace and click **DataArts Quality**.

#. Choose **Quality Monitoring** > **Quality Job** in the left navigation bar.

#. Click **Refresh Now** in the upper right corner. The page displays the temporary data generated from 00:00 to the current time. You can immediately obtain the data quality report of the current day.


   .. figure:: /_static/images/en-us_image_0000002234079748.png
      :alt: **Figure 10** Refresh Now

      **Figure 10** Refresh Now
