:original_name: dataartsstudio_04_0031.html

.. _dataartsstudio_04_0031:

Scenario
========

In this practice, you will learn how to use Cloud Data Migration (CDM), DataArts Factory of DataArts Studio, and GaussDB(DWS) to analyze movie scores and find out the 10 best and most frequently scored movies. You will learn the data migration function of DataArts Migration, and the script development, job development, and job scheduling functions of DataArts Factory, as well as basic SQL syntax of GaussDB(DWS).

.. note::

   This practice involves the DataArts Migration, Management Center, and DataArts Factory modules of DataArts Studio. All DataArts Studio versions can meet requirements.

The procedure is as follows:

#. Make preparations, including :ref:`Preparations <dataartsstudio_04_0032__section485519219101>`, :ref:`preparing data sources <dataartsstudio_04_0032__section28742371270>`, :ref:`preparing a data lake <dataartsstudio_04_0032__section7296123818418>`, and :ref:`preparing authentication data <dataartsstudio_04_0032__section134011417816>`.
#. Create a job to migrate data from OBS to DWS. For details, see :ref:`Migrating Data from OBS to DWS <dataartsstudio_04_0033__section24245155311>`.
#. Develop data, including creating DWS SQL scripts and a job.

   -  :ref:`Creating DWS SQL Script top_rating_movie for Storing 10 Top-rated Movies <dataartsstudio_04_0034__section811455214811>`
   -  :ref:`Creating DWS SQL Script top_active_movie for Storing 10 Most Frequently Scored Movies <dataartsstudio_04_0034__section746015474175>`
   -  :ref:`Developing and Scheduling a Job <dataartsstudio_04_0034__section845855811817>`. After orchestrating the job and configuring scheduling policies to periodically execute the job, you can obtain the latest top 10 movies every day.
