:original_name: dataartsstudio_04_0023.html

.. _dataartsstudio_04_0023:

Step 2: Develop Data
====================

This step describes how to use the data in BI reports to analyze the 10 products users like most and 10 products users dislike most. Jobs are periodically executed and the results are exported to tables every day for data analysis.

.. _dataartsstudio_04_0023__section1635916335616:

Analyze 10 Products Users Like Most
-----------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. Create a DLI SQL script used to create data tables by entering DLI SQL statements in the editor.


   .. figure:: /_static/images/en-us_image_0000002269129953.png
      :alt: **Figure 1** Creating a script

      **Figure 1** Creating a script

#. In the SQL editor, enter the following SQL statements and click **Execute** to calculate the 10 products users like most from the original data table in the OBS bucket and save the result to the **top_like_product** table.

   .. code-block::

      INSERT
        OVERWRITE table top_like_product
      SELECT
        product.brand as brand,
        COUNT(product.brand) as like_count
      FROM
        action
        JOIN product ON (action.product_id = product.product_id)
      WHERE
        action.type = 'like'
      group by
        brand
      ORDER BY
        like_count desc
      LIMIT
        10


   .. figure:: /_static/images/en-us_image_0000002269129925.png
      :alt: **Figure 2** Script for analyzing the 10 products users like most

      **Figure 2** Script for analyzing the 10 products users like most

   The key parameters are as follows:

   -  **Data Connection**: DLI data connection created in :ref:`Step 4 <dataartsstudio_04_0022__li4298133815461>`
   -  **Database**: database created in :ref:`Step 6 <dataartsstudio_04_0022__li17522165311514>`
   -  **Resource Queue**: The default resource queue **default** can be used.

      .. note::

         -  The version of the default Spark component of the default DLI queue is not up-to-date, and an error may be reported indicating that a table creation statement cannot be executed. In this case, you are advised to create a queue to run your tasks. To enable the execution of table creation statements in the default queue, contact the customer service or technical support of the DLI service.

         -  The default queue **default** of DLI is only used for trial. It may be occupied by multiple users at a time. Therefore, it is possible that you fail to obtain the resource for related operations. If the execution takes a long time or fails, you are advised to try again during off-peak hours or use a self-built queue to run the job.

#. After debugging the script, click **Save** to save the script and name it **top_like_product**. Click **Submit** to submit the script version. This script will be referenced later in :ref:`Developing and Scheduling a Job <dataartsstudio_04_0023__section517814479613>`.

#. After the script is saved and executed successfully, you can use the following SQL statement to view data in the **top_like_product** table. You can also download or dump the table data by referring to :ref:`Figure 3 <dataartsstudio_04_0023__fig1475143652816>`.

   .. code-block::

      SELECT * FROM top_like_product

   .. _dataartsstudio_04_0023__fig1475143652816:

   .. figure:: /_static/images/en-us_image_0000002269210033.png
      :alt: **Figure 3** Viewing the data in the top_like_product table

      **Figure 3** Viewing the data in the top_like_product table

.. _dataartsstudio_04_0023__section1943211391368:

Analyze 10 Products Users Dislike Most
--------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. Create a DLI SQL script used to create data tables by entering DLI SQL statements in the editor.


   .. figure:: /_static/images/en-us_image_0000002269129953.png
      :alt: **Figure 4** Creating a script

      **Figure 4** Creating a script

#. In the SQL editor, enter the following SQL statements and click **Execute** to calculate the 10 products users dislike most from the original data table in the OBS bucket and save the result to the **top_bad_comment_product** table.

   .. code-block::

      INSERT
        OVERWRITE table top_bad_comment_product
      SELECT
        DISTINCT product_id,
        comment_num,
        bad_comment_rate
      FROM
        comment
      WHERE
        comment_num > 3
      ORDER BY
        bad_comment_rate desc
      LIMIT
        10


   .. figure:: /_static/images/en-us_image_0000002269210057.png
      :alt: **Figure 5** Script for analyzing the 10 products users dislike most

      **Figure 5** Script for analyzing the 10 products users dislike most

   The key parameters are as follows:

   -  **Data Connection**: DLI data connection created in :ref:`Step 4 <dataartsstudio_04_0022__li4298133815461>`
   -  **Database**: database created in :ref:`Step 6 <dataartsstudio_04_0022__li17522165311514>`
   -  **Resource Queue**: The default resource queue **default** can be used.

      .. note::

         -  The version of the default Spark component of the default DLI queue is not up-to-date, and an error may be reported indicating that a table creation statement cannot be executed. In this case, you are advised to create a queue to run your tasks. To enable the execution of table creation statements in the default queue, contact the customer service or technical support of the DLI service.

         -  The default queue **default** of DLI is only used for trial. It may be occupied by multiple users at a time. Therefore, it is possible that you fail to obtain the resource for related operations. If the execution takes a long time or fails, you are advised to try again during off-peak hours or use a self-built queue to run the job.

#. After debugging the script, click **Save and Submit** to save the script and name it **top_bad_comment_product**. This script will be referenced later in :ref:`Developing and Scheduling a Job <dataartsstudio_04_0023__section517814479613>`.

#. After the script is saved and executed successfully, you can use the following SQL statement to view data in the **top_bad_comment_product** table. You can also download or dump the table data by referring to :ref:`Figure 6 <dataartsstudio_04_0023__fig383328104119>`.

   .. code-block::

      SELECT * FROM top_bad_comment_product

   .. _dataartsstudio_04_0023__fig383328104119:

   .. figure:: /_static/images/en-us_image_0000002269129937.png
      :alt: **Figure 6** Viewing the data in the top_bad_comment_product table

      **Figure 6** Viewing the data in the top_bad_comment_product table

.. _dataartsstudio_04_0023__section517814479613:

Developing and Scheduling a Job
-------------------------------

Assume that the BI reports in the OBS bucket are changing every day. To update the analysis result every day, use the job orchestration and scheduling functions of DataArts Factory.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. Create a batch processing job named **BI_analysis**.


   .. figure:: /_static/images/en-us_image_0000002269129969.png
      :alt: **Figure 7** Creating a job

      **Figure 7** Creating a job


   .. figure:: /_static/images/en-us_image_0000002234090784.png
      :alt: **Figure 8** Configuring the job

      **Figure 8** Configuring the job

#. Open the created job, drag two Dummy nodes and two DLI SQL nodes to the canvas, select and drag |image1|, and orchestrate the job shown in :ref:`Figure 9 <dataartsstudio_04_0023__en-us_topic_0119212931_fig196701229164812>`.

   .. _dataartsstudio_04_0023__en-us_topic_0119212931_fig196701229164812:

   .. figure:: /_static/images/en-us_image_0000002234090776.png
      :alt: **Figure 9** Connecting nodes and configuring node properties

      **Figure 9** Connecting nodes and configuring node properties

   Key nodes:

   -  **Begin** (Dummy node): serves only as a start identifier.
   -  **top_like_product** (DLI SQL node): In **Node Properties**, associates with the DLI SQL script **top_like_product** developed in :ref:`Analyze 10 Products Users Like Most <dataartsstudio_04_0023__section1635916335616>`.
   -  **top_bad_comment_product** (DLI SQL node): In **Node Properties**, associates with the DLI SQL script **top_bad_comment_product** developed in :ref:`Analyze 10 Products Users Dislike Most <dataartsstudio_04_0023__section1943211391368>`.
   -  **Finish** (Dummy node): serves only as an end identifier.

#. Click |image2| to test the job.

#. If the job runs properly, click **Scheduling Setup** in the right pane and configure the scheduling policy for the job.


   .. figure:: /_static/images/en-us_image_0000002234250624.png
      :alt: **Figure 10** Configuring scheduling

      **Figure 10** Configuring scheduling

   Note:

   -  **Scheduling Type**: Select **Run periodically**.
   -  **Scheduling Properties**: The job is executed at 01:00 every day from Feb 09 to Feb 28, 2022.
   -  **Dependency Properties**: You can configure a dependency job for this job. You do not need to configure it in this practice.
   -  **Cross-Cycle Dependency**: Select **Independent on the previous schedule cycle**.

#. Click **Save**, **Submit** (|image3|), and **Execute** (|image4|). Then the job will be automatically executed every day and the BI report analysis result is automatically saved to the **top_like_product** and **top_bad_comment_product** tables, respectively.

#. If you want to check the job execution result, choose **Monitoring** > **Monitor Instance** in the left navigation pane.


   .. figure:: /_static/images/en-us_image_0000002234090764.png
      :alt: **Figure 11** Viewing the job execution status

      **Figure 11** Viewing the job execution status

You can also configure notifications to be sent through SMS messages or emails, when a job encounters exceptions or fails.

Now you have learned the data development process based on e-commerce BI reports. In addition, you can analyze the age distribution and gender ratio of users and their browsing, purchase, and evaluation of products to provide valuable information for marketing decision-making, advertising, credit rating, brand monitoring, and user behavior prediction.

.. |image1| image:: /_static/images/en-us_image_0000002269210029.png
.. |image2| image:: /_static/images/en-us_image_0000002269210073.png
.. |image3| image:: /_static/images/en-us_image_0000002269129929.png
.. |image4| image:: /_static/images/en-us_image_0000002234250604.png
