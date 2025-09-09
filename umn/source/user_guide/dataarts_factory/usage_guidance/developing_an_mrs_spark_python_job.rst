:original_name: dataartsstudio_01_0525.html

.. _dataartsstudio_01_0525:

Developing an MRS Spark Python Job
==================================

This section describes how to develop an MRS Spark Python on DataArts Factory.

Case 1: Using an MRS Spark Python Job to Count the Number of Words
------------------------------------------------------------------

**Prerequisites**

You have the permission to access OBS paths.

**Data preparation**

-  Prepare the script file **wordcount.py** with the following content:

   .. code-block::

      # -*- coding: utf-8 -*
      import sys
      from pyspark import SparkConf, SparkContext
      def show(x):
          print(x)
      if __name__ == "__main__":
          if len(sys.argv) < 2:
              print ("Usage: wordcount <inputPath> <outputPath>")
              exit(-1)
          # Create SparkConf.
          conf = SparkConf().setAppName("wordcount")
          # Create SparkContext. Pass the conf=conf parameter.
          sc = SparkContext(conf=conf)
          inputPath = sys.argv[1]
          outputPath = sys.argv[2]
          lines = sc.textFile(name = inputPath)
          # Split each line of data by space to obtain words.
          words = lines.flatMap(lambda line:line.split(" "),True)
          # Pair each word into a tuple count 1.
          pairWords = words.map(lambda word:(word,1),True)
          # Use three partitions (reduceByKey) for summarization.
          result = pairWords.reduceByKey(lambda v1,v2:v1+v2)
          # Print the result.
          result.foreach(lambda t :show(t))
          # Save the result to a file.
          result.saveAsTextFile(outputPath)
          # Stop SparkContext.
          sc.stop()

   .. note::

      The encoding format must be set to UTF-8. Otherwise, an error will occur during script execution.

-  Prepare the data file **in.txt**, which contains some English words.

**Procedure**

#. Upload the script and data file to the OBS bucket.


   .. figure:: /_static/images/en-us_image_0000002269198269.png
      :alt: **Figure 1** Uploading files to an OBS bucket

      **Figure 1** Uploading files to an OBS bucket

   .. note::

      In this example, upload **wordcount.py** and **in.txt** to **obs://obs-tongji/python/**.

#. Create an empty job named **job_MRS_Spark_Python**.


   .. figure:: /_static/images/en-us_image_0000002269198253.png
      :alt: **Figure 2** Creating a job

      **Figure 2** Creating a job

#. Go to the job development page, drag the **MRS Spark Python** node to the canvas, and click the node to configure its properties.


   .. figure:: /_static/images/en-us_image_0000002234078972.png
      :alt: **Figure 3** Configuring properties for an MRS Spark Python node

      **Figure 3** Configuring properties for an MRS Spark Python node

   Parameter descriptions:

   .. code-block::

      --master
      yarn
      --deploy-mode
      cluster
      obs://obs-tongji/python/wordcount.py
      obs://obs-tongji/python/in.txt
      obs://obs-tongji/python/out

   Specifically:

   **obs://obs-tongji/python/wordcount.py** is the directory where the script is stored.

   **obs://obs-tongji/python/in.txt** is the directory where the **wordcount.py** parameters are passed. You can pass the words to count.

   **obs://obs-tongji/python/out** is the directory where output parameters are stored. This directory will also be created in the OBS bucket automatically. If the **out** directory already exists in the OBS bucket, an error will occur.

#. Click **Test** to execute the script job.

#. After the test is complete, click **Submit**.

#. Choose **Monitor Job** in the navigation pane and view the job execution result.


   .. figure:: /_static/images/en-us_image_0000002269198261.png
      :alt: **Figure 4** Viewing the job execution result

      **Figure 4** Viewing the job execution result

   The job log shows that the job was successfully executed.


   .. figure:: /_static/images/en-us_image_0000002269118173.png
      :alt: **Figure 5** Job run logs

      **Figure 5** Job run logs


   .. figure:: /_static/images/en-us_image_0000002234238812.png
      :alt: **Figure 6** Job execution status

      **Figure 6** Job execution status

#. View the returned records in the OBS bucket. (Skip this step if the return function is not configured.)


   .. figure:: /_static/images/en-us_image_0000002234238820.png
      :alt: **Figure 7** Viewing the returned records in the OBS bucket

      **Figure 7** Viewing the returned records in the OBS bucket

Case 2: Using an MRS Spark Python Job to Print **hello python**
---------------------------------------------------------------

**Prerequisites**

You have the permission to access OBS paths.

**Data preparation**

Prepare the script file **zt_test_sparkPython1.py** with the following content:

.. code-block::

   from pyspark import SparkContext, SparkConf
   conf = SparkConf().setAppName("master"). setMaster("yarn")
   sc = SparkContext(conf=conf)
   print("hello python")
   sc.stop()

**Procedure**

#. Upload the script file to an OBS bucket.

#. Create an empty job.

#. Go to the job development page, drag the **MRS Spark Python** node to the canvas, and click the node to configure its properties.

   Parameter descriptions:

   .. code-block::

      --master
      yarn
      --deploy-mode
      cluster
      obs://obs-tongji/python/zt_test_sparkPython1.py

   **zt_test_sparkPython1.py** indicates the directory where the script is stored.

#. Click **Test** to execute the script job.

#. After the test is complete, click **Submit**.

#. Choose **Monitor Job** in the navigation pane and view the job execution result.


   .. figure:: /_static/images/en-us_image_0000002234078988.png
      :alt: **Figure 8** Viewing the job execution result

      **Figure 8** Viewing the job execution result

#. Verify the log.

   Log in to MRS Manager and check that the log on YARN contains **hello python**.


   .. figure:: /_static/images/en-us_image_0000002234078980.png
      :alt: **Figure 9** Viewing logs on YARN

      **Figure 9** Viewing logs on YARN
