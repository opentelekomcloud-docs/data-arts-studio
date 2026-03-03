:original_name: dataartsstudio_04_0034.html

.. _dataartsstudio_04_0034:

Step 3: Develop Data
====================

This step describes how to use the movie information and rating data to analyze 10 top-rated movies and 10 most frequently scored movies. Jobs are periodically executed and the results are exported to tables every day for data analysis.

.. _dataartsstudio_04_0034__section811455214811:

Creating DWS SQL Script **top_rating_movie** for Storing 10 Top-rated Movies
----------------------------------------------------------------------------

The method of finding out the 10 top-rated movies is as follows: Calculate the total score of each movie and the number of the users who participate in scoring the movies, filter out the movies that are scored by less than three users, and then return the movie names, average scores, and participant quantity.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. Create a DWS SQL script used to create data tables by entering DWS SQL statements in the editor.


   .. figure:: /_static/images/en-us_image_0000002269130013.png
      :alt: **Figure 1** Creating a script

      **Figure 1** Creating a script

#. In the SQL editor, enter the following SQL statements and click **Execute** to calculate the 10 top-rated movies from the **movies_item** and **ratings_item** tables and save the result to the **top_rating_movie** table.

   .. code-block::

      SET
          SEARCH_PATH TO dgc;
      insert
          overwrite into top_rating_movie
      select
          a.movieTitle,
          b.ratings / b.rating_user_number as avg_rating,
          b.rating_user_number
      from
          movies_item a,
          (
              select
                  movieId,
                  sum(rating) ratings,
                  count(1) as rating_user_number
              from
                  ratings_item
              group by
                  movieId
          ) b
      where
          rating_user_number > 3
          and a.movieId = b.movieId
      order by
          avg_rating desc
      limit
          10


   .. figure:: /_static/images/en-us_image_0000002234250832.png
      :alt: **Figure 2** Script (top_rating_movie)

      **Figure 2** Script (top_rating_movie)

   The key parameters are as follows:

   -  **Data Connection**: DWS data connection created in :ref:`Step 4 <dataartsstudio_04_0032__li6594811184817>`
   -  **Database**: database created in :ref:`Step 6 <dataartsstudio_04_0032__li646420431311>`

#. After debugging the script, click **Save and Submit** to submit the script and name it **top_rating_movie**. This script will be referenced later in :ref:`Developing and Scheduling a Job <dataartsstudio_04_0034__section845855811817>`.

#. After the script is saved and executed successfully, you can use the following SQL statement to view data in the **top_rating_movie** table. You can also download or dump the table data by referring to :ref:`Figure 3 <dataartsstudio_04_0034__fig1475143652816>`.

   .. code-block::

      SET SEARCH_PATH TO dgc;
      SELECT * FROM top_rating_movie

   .. _dataartsstudio_04_0034__fig1475143652816:

   .. figure:: /_static/images/en-us_image_0000002234090996.png
      :alt: **Figure 3** Viewing the data in the top_rating_movie table

      **Figure 3** Viewing the data in the top_rating_movie table

.. _dataartsstudio_04_0034__section746015474175:

Creating DWS SQL Script **top_active_movie** for Storing 10 Most Frequently Scored Movies
-----------------------------------------------------------------------------------------

The method of finding out the 10 most frequently scored movies is as follows: Calculate the 10 most frequently scored movies whose average scores are higher than 3.5.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. Create a DWS SQL script used to create data tables by entering DWS SQL statements in the editor.


   .. figure:: /_static/images/en-us_image_0000002269130013.png
      :alt: **Figure 4** Creating a script

      **Figure 4** Creating a script

#. In the SQL editor, enter the following SQL statements and click **Execute** to calculate the 10 most frequently scored movies from the **movies_item** and **ratings_item** tables and save the result to the **top_active_movie** table.

   .. code-block::

      SET
          SEARCH_PATH TO dgc;
      insert
          overwrite into top_active_movie
      select
          *
      from
          (
              select
                  a.movieTitle,
                  b.ratingSum / b.rating_user_number as avg_rating,
                  b.rating_user_number
              from
                  movies_item a,
                  (
                      select
                          movieId,
                          sum(rating) ratingSum,
                          count(1) as rating_user_number
                      from
                          ratings_item
                      group by
                          movieId
                  ) b
              where
                  a.movieId = b.movieId
          ) t
      where
          t.avg_rating > 3.5
      order by
          rating_user_number desc
      limit
          10


   .. figure:: /_static/images/en-us_image_0000002234250840.png
      :alt: **Figure 5** Script (top_active_movie)

      **Figure 5** Script (top_active_movie)

   The key parameters are as follows:

   -  **Data Connection**: DWS data connection created in :ref:`Step 4 <dataartsstudio_04_0032__li6594811184817>`
   -  **Database**: database created in :ref:`Step 6 <dataartsstudio_04_0032__li646420431311>`

#. After debugging the script, click **Save and Submit** to submit the script and name it **top_active_movie**. This script will be referenced later in :ref:`Developing and Scheduling a Job <dataartsstudio_04_0034__section845855811817>`.

#. After the script is saved and executed successfully, you can use the following SQL statement to view data in the **top_active_movie** table. You can also download or dump the table data by referring to :ref:`Figure 6 <dataartsstudio_04_0034__fig1614814155463>`.

   .. code-block::

      SET SEARCH_PATH TO dgc;
      SELECT * FROM top_active_movie

   .. _dataartsstudio_04_0034__fig1614814155463:

   .. figure:: /_static/images/en-us_image_0000002234090992.png
      :alt: **Figure 6** Viewing the data in the top_active_movie table

      **Figure 6** Viewing the data in the top_active_movie table

.. _dataartsstudio_04_0034__section845855811817:

Developing and Scheduling a Job
-------------------------------

Assume that the **movie** and **rating** tables in the OBS bucket are changing in real time. To update top 10 movies every day, use the job orchestration and scheduling functions of DataArts Factory.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. Create a batch job named **topmovie**.


   .. figure:: /_static/images/en-us_image_0000002269129969.png
      :alt: **Figure 7** Creating a job

      **Figure 7** Creating a job


   .. figure:: /_static/images/en-us_image_0000002269130197.png
      :alt: **Figure 8** Configuring the job

      **Figure 8** Configuring the job

#. Open the created job, drag two CDM Job nodes, three Dummy nodes, and two DWS SQL nodes to the canvas, select and drag |image1|, and orchestrate the job shown in :ref:`Figure 9 <dataartsstudio_04_0034__fig196701229164812>`.

   .. _dataartsstudio_04_0034__fig196701229164812:

   .. figure:: /_static/images/en-us_image_0000002269210277.png
      :alt: **Figure 9** Connecting nodes and configuring node properties

      **Figure 9** Connecting nodes and configuring node properties

   Key nodes:

   -  **Begin** (Dummy node): serves only as a start identifier.
   -  **movies_obs2dws** (CDM Job node): In **Node Properties**, select the CDM cluster in :ref:`Step 2: Integrate Data <dataartsstudio_04_0033>` and associate it with the CDM job **movies_obs2dws**.
   -  **ratings_obs2dws** (CDM Job node): In **Node Properties**, select the CDM cluster in :ref:`Step 2: Integrate Data <dataartsstudio_04_0033>` and associate it with the CDM job **ratings_obs2dws**.
   -  **Waiting** (Dummy node): No operation is performed. It is an identifier of the execution completion of the previous node.
   -  **top_rating_movie** (DWS SQL node): In **Node Properties**, associate this node with the DWS SQL script **top_rating_movie** you have created in :ref:`Creating DWS SQL Script top_rating_movie <dataartsstudio_04_0034__section811455214811>`.
   -  **top_active_movie** (DWS SQL node): In **Node Properties**, associate this node with the DWS SQL script **top_active_movie** you have created in :ref:`Creating DWS SQL Script top_active_movie <dataartsstudio_04_0034__section746015474175>`.
   -  **Finish** (Dummy node): serves only as an end identifier.

#. After configuring the job, click |image2| to test it.

#. If the job runs properly, click **Scheduling Setup** in the right pane and configure the scheduling policy for the job.


   .. figure:: /_static/images/en-us_image_0000002234091004.png
      :alt: **Figure 10** Configuring scheduling

      **Figure 10** Configuring scheduling

   Notes:

   -  **Scheduling Properties**: The job is executed at 01:00 every day from Feb 09 to Feb 28, 2022.
   -  **Dependency Properties**: You can configure a dependency job for this job. You do not need to configure it in this practice.
   -  **Cross-Cycle Dependency**: Select **Independent on the previous schedule cycle**.

#. Click **Save**, **Submit** (|image3|), and **Execute** (|image4|). Then the job will be automatically executed every day so the 10 highest scored and most frequently scored movies are automatically saved to the **top_active_movie** and **top_rating_movie** tables, respectively.

#. If you want to check the job execution result, choose **Monitoring** > **Monitor Instance** in the left navigation pane.


   .. figure:: /_static/images/en-us_image_0000002269130173.png
      :alt: **Figure 11** Viewing the job execution status

      **Figure 11** Viewing the job execution status

You can also configure notifications to be sent through SMS messages, emails, or console when a job encounters exceptions or fails.

Now you have learned the data integration and development process based on movie scores. In addition, you can analyze the ratings and browsing of different types of movies to provide valuable information for marketing decision-making, advertising, and user behavior prediction.

.. |image1| image:: /_static/images/en-us_image_0000002234250848.png
.. |image2| image:: /_static/images/en-us_image_0000002269210297.png
.. |image3| image:: /_static/images/en-us_image_0000002234091012.png
.. |image4| image:: /_static/images/en-us_image_0000002234250844.png
