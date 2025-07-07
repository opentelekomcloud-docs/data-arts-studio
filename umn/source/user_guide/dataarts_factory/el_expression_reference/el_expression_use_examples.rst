:original_name: dataartsstudio_01_0502.html

.. _dataartsstudio_01_0502:

EL Expression Use Examples
==========================

With this example, you can understand how to use EL expressions in the following applications:

-  Using variables in the SQL script of DataArts Factory
-  Transferring parameters to SQL script variables?
-  Using EL expressions in parameters?

Context
-------

Use the job orchestration and job scheduling functions to generate daily transaction statistics reports according to transaction details tables.

The tables involved in this example are as follows:

-  trade_log: This table records data generated in each transaction.
-  trade_report: This table is generated based on trade_log and records the daily transaction summary.

Prerequisites
-------------

-  A DLI data connection named **dli_demo** has been created.

   If this data connection is not created, create one. For details, see :ref:`Managing Data Connections <dataartsstudio_01_0009>`.

-  A database named **dli_db** has been created in DLI.

   If this database is not created, create one. For details, see :ref:`Creating a Database <dataartsstudio_01_0405>`.

-  Tables **trade_log** and **trade_report** have been created in the **dli_db** database.

   If the tables are not created, create them. For details, see :ref:`Creating a Table <dataartsstudio_01_0416>`.

Procedure
---------

#. .. _dataartsstudio_01_0502__en-us_topic_0133127285_li659355023719:

   Create and develop a SQL script.

   a. In the left navigation pane of the DataArts Factory console, choose **Data Development** > **Develop Script** and click **+ DLI**.

   b. Go to the SQL script development page and set the data connection, database, and resource queue on the script property bar.

   c. Enter the following SQL statements in the script editor:

      .. code-block::

         INSERT OVERWRITE TABLE trade_report
         SELECT
           sum(trade_count),
           '${yesterday}'
         FROM
           trade_log
         where
           date_format(trade_time, 'yyyy-MM-dd') = '${yesterday}'

   d. Click |image1| and set the script name to **generate_trade_report**.

#. Create and develop a job.

   a. In the left navigation pane on the DataArts Factory console, choose **Data Development** > **Develop Job** and click **Create Job** to create an empty job named **job**.

   b. Go to the job development page, drag the DLI SQL node to the canvas, click the icon, and configure node properties.

      Description of key properties:

      -  SQL Script: SQL script **generate_trade_report** that is developed in :ref:`1 <dataartsstudio_01_0502__en-us_topic_0133127285_li659355023719>`.

      -  Database Name: Database configured in SQL script **generate_trade_report**.

      -  Queue Name: Resource queue configured in SQL script **generate_trade_report**.

      -  Script Parameter: Parameter **yesterday** configured in SQL script **generate_trade_report**. Enter the following EL expression as the parameter values:

         .. code-block::

            #{Job.getYesterday("yyyy-MM-dd")}

         Expression Description: The job object uses the getYesterday method to obtain the time of the day before the job plan execution time. The time format is yyyy-MM-dd.

         If the job plan time is 2018/9/26 01:00:00, the calculation result of this expression is 2018-09-25. The calculation result will replace the value of parameter ${yesterday} in the SQL script. The SQL statements after the replacement are as follows:

         .. code-block::

            INSERT OVERWRITE TABLE trade_report
            SELECT
              sum(trade_count),
              '2018-09-25'
            FROM
              trade_log
            where
              date_format(trade_time, 'yyyy-MM-dd') = '2018-09-25'

   c. Click |image2| to test the running job.

   d. After the job test is complete, click |image3| to save the job configuration.

.. |image1| image:: /_static/images/en-us_image_0000002305406585.png
.. |image2| image:: /_static/images/en-us_image_0000002270789856.png
.. |image3| image:: /_static/images/en-us_image_0000002305406585.png
