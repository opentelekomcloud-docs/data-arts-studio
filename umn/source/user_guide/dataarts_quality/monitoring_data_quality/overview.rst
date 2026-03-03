:original_name: dataartsstudio_01_0709.html

.. _dataartsstudio_01_0709:

Overview
========

DataArts Quality is a type of quality management tool used to manage the quality of data in databases. You can filter out unqualified data in a single column or across columns, rows, sources, and tables from the following perspectives: integrity, validity, timeliness, consistency, accuracy, and uniqueness. DataArts Quality can monitor offline data. When offline data changes, DataArts Quality verifies the data and blocks the production link to avoid the spread of the problem data. DataArts Quality also manages historical verification results so that you can analyze and grade data quality.

It can also automatically generate standardized quality rules based on the data standards in DataArts Architecture, and periodically monitor data.

The following table describes modules under **Quality Monitoring**.

+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Module                            | Description                                                                                                                                                                                                         |
+===================================+=====================================================================================================================================================================================================================+
| Dashboard                         | The dashboard is the homepage that displays alarming and blocking information of tables.                                                                                                                            |
|                                   |                                                                                                                                                                                                                     |
|                                   | The following information is included:                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                                     |
|                                   | -  Number of jobs, instances, and anomaly tables; distributions and changes of instance running statuses in a selected period.                                                                                      |
|                                   | -  Statistics about alarm classifications and table alarms of the current day, as well as the alarm trend and rule quantity of the latest seven days.                                                               |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Rule Template                     | Rule template is a major function of DataArts Quality. You can configure rules on the **Rule Template** page. It mainly manages functions related to rule configuration and provides built-in and custom templates. |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Quality Job                       | Quality jobs can apply rule templates or custom rules to tables for data monitoring.                                                                                                                                |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Comparison Job                    | You can create comparison jobs to apply the created rules to two existing tables to monitor their data and output the comparison results.                                                                           |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| O&M Management                    | You can view the running status of rules and handle O&M problems.                                                                                                                                                   |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Quality Report                    | The system automatically generates quality reports based on the job execution result.                                                                                                                               |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
