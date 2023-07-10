:original_name: dataartsstudio_01_0526.html

.. _dataartsstudio_01_0526:

Developing an MRS Flink Job
===========================

This section describes how to develop an MRS Flink job on DataArts Factory. Use an MRS Flink job to count the number of words.

Prerequisites
-------------

-  You have the permission to access OBS paths.
-  MRS has been enabled and an MRS cluster has been created.

Data Preparation
----------------

-  Download the Flink job resource package **wordcount.jar** from https://github.com/apache/flink/tree/master/flink-examples/flink-examples-streaming/src/main/java/org/apache/flink/streaming/examples/wordcount.
-  Prepare the data file **in.txt**, which contains some English words.

Procedure
---------

#. Upload the job resource package and data file to the OBS bucket.

   .. note::

      In this example, upload **WordCount.jar** to **lkj_test/WordCount.jar** and **word.txt** to **lkj_test/input/word.txt**.

#. Create an empty job named **job_MRS_Flink**.


   .. figure:: /_static/images/en-us_image_0000001373408473.png
      :alt: **Figure 1** Creating a job

      **Figure 1** Creating a job

#. Go to the job development page, drag the **MRS Flink** node to the canvas, and click the node to configure its properties.


   .. figure:: /_static/images/en-us_image_0000001321928744.png
      :alt: **Figure 2** Configuring properties for an MRS Flink node

      **Figure 2** Configuring properties for an MRS Flink node

   Parameter descriptions:

   .. code-block::

      --Flink job name
      wordcount
      --MRS cluster name
      Select an MRS cluster.
      --Program parameter
      -c    org.apache.flink.streaming.examples.wordcount.WordCount
      --Flink job resource package
      wordcount
      --Input data path
      obs://dlf-beijing2/lkj_test/input/word.txt
      --Output data path
      obs://dlf-beijing2/lkj_test/output.txt

   Specifically:

   **obs://dlf-beijing2/lkj_test/input/word.txt** is the directory where the **wordcount.jar** parameters are passed. You can pass the words to count.

   **obs://dlf-beijing2/lkj_test/output.txt** is the directory where the output parameter file is stored. (If the **output.txt** file already exists, an error is reported.)

#. Click **Test** to execute the MRS Flink job.

#. After the test is complete, click **Submit**.

#. Choose **Monitor Job** in the navigation pane and view the job execution result.

#. View the returned records in the OBS bucket. (Skip this step if the return function is not configured.)
