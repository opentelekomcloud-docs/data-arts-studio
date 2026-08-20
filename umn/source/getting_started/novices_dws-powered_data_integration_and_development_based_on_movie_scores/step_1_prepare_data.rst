:original_name: dataartsstudio_04_0032.html

.. _dataartsstudio_04_0032:

Step 1: Prepare Data
====================

.. _dataartsstudio_04_0032__section485519219101:

Preparations
------------

If you are new to DataArts Studio, create a cloud platform account, create a DataArts Studio instance, create workspaces, and make other preparations. For details, see "Creating and Configuring a DataArts Studio Instance" in *User Guide*. Then you can go to the created workspace and start using DataArts Studio.

.. _dataartsstudio_04_0032__section28742371270:

Preparing Data Sources
----------------------

This practice uses the 100,000 scores given by 1,000 users to 1,700 movies. The scores are available at https://grouplens.org/datasets/movielens/100k/. Obtain the .zip package from the link and extract the **u.item** and **u.data** files from it. They contain the movie information and rating information, respectively.

To facilitate demonstration, this practice provides some data used to simulate the original data. To integrate the source data into the cloud, you need to store the sample data in CSV files and upload them to an OBS bucket.

#. Create CSV files (UTF-8 without BOM), name the files with the corresponding data table names, copy the sample data to different CSV files, and save the files.

   To generate a CSV file in Windows, you can perform the following steps:

   a. Use a text editor (for example, Notepad) to create a .txt document and copy the sample data to the document. Then check the total number of rows and check whether the data of rows is correctly separated. (If the sample data is copied from a PDF document, the data in a single row will be wrapped if the data is too long. In this case, you must manually adjust the data to ensure that it is in a single row.)
   b. Choose **File** > **Save as**. In the displayed dialog box, set **Save as type** to **All files (*.*)**, enter the file name with the .csv suffix for **File name**, and select the UTF-8 encoding format (without BOM) to save the file in CSV format.

#. Upload the CSV file to OBS.

   a. Log in to the management console and choose **Storage** > **Object Storage Service** to access the OBS console.

   b. Click **Create Bucket** and set parameters as prompted to create an OBS bucket named **fast-demo**.

      .. note::

         To ensure network connectivity, select the same region for OBS bucket as that for the DataArts Studio instance. If an enterprise project is required, select the enterprise project that is the same as that of the DataArts Studio instance.

      For details about how to create a bucket on the OBS console, see in *Object Storage Service Console Operation Guide*\ **Console Operation Guide > Getting Started > Creating a Bucket** in *Object Storage Service 3.0* *Usage Guide*.

   c. Upload data to OBS bucket **fast-demo**.

      For details about how to upload a file on the OBS console, see in *Object Storage Service Console Operation Guide*\ **Console Operation Guide > Getting Started > Uploading a File** in *Object Storage Service 3.0* *Usage Guide*.

This practice involves movie data (:ref:`movies.csv <dataartsstudio_04_0032__li132871346727>`) and rating data (:ref:`ratings.csv <dataartsstudio_04_0032__li4584112342819>`). Descriptions of the data are as follows:

-  .. _dataartsstudio_04_0032__li132871346727:

   **movies.csv**:

   .. code-block::

      movieId,movieTitle,videoReleaseDate,IMDbURL,unknown,Action,Adventure,Animation,Children,Comedy,Crime,Documentary,Drama,Fantasy,FilmNoir,Horror,Musical,Mystery,Romance,SciFi,Thriller,War,Western
      1,Toy Story (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Toy%20Story%20(1995),0,0,0,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0
      2,GoldenEye (1995),1-Jan-95,http://us.imdb.com/M/title-exact?GoldenEye%20(1995),0,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0
      3,Four Rooms (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Four%20Rooms%20(1995),0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0
      4,Get Shorty (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Get%20Shorty%20(1995),0,1,0,0,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0
      5,Copycat (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Copycat%20(1995),0,0,0,0,0,0,1,0,1,0,0,0,0,0,0,0,1,0,0
      6,Shanghai Triad (Yao a yao yao dao waipo qiao) (1995),1-Jan-95,http://us.imdb.com/Title?Yao+a+yao+yao+dao+waipo+qiao+(1995),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0
      7,Twelve Monkeys (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Twelve%20Monkeys%20(1995),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,1,0,0,0
      8,Babe (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Babe%20(1995),0,0,0,0,1,1,0,0,1,0,0,0,0,0,0,0,0,0,0
      9,Dead Man Walking (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Dead%20Man%20Walking%20(1995),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0
      10,Richard III (1995),22-Jan-96,http://us.imdb.com/M/title-exact?Richard%20III%20(1995),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0
      11,Seven (Se7en) (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Se7en%20(1995),0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,1,0,0
      12,"Usual Suspects, The (1995)",14-Aug-95,"http://us.imdb.com/M/title-exact?Usual%20Suspects,%20The%20(1995)",0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,1,0,0
      13,Mighty Aphrodite (1995),30-Oct-95,http://us.imdb.com/M/title-exact?Mighty%20Aphrodite%20(1995),0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0
      14,"Postino, Il (1994)",1-Jan-94,"http://us.imdb.com/M/title-exact?Postino,%20Il%20(1994)",0,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,0
      15,Mr. Holland's Opus (1995),29-Jan-96,http://us.imdb.com/M/title-exact?Mr.%20Holland's%20Opus%20(1995),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0
      16,French Twist (Gazon maudit) (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Gazon%20maudit%20(1995),0,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,0,0
      17,From Dusk Till Dawn (1996),5-Feb-96,http://us.imdb.com/M/title-exact?From%20Dusk%20Till%20Dawn%20(1996),0,1,0,0,0,1,1,0,0,0,0,1,0,0,0,0,1,0,0
      18,"White Balloon, The (1995)",1-Jan-95,http://us.imdb.com/M/title-exact?Badkonake%20Sefid%20(1995),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0
      19,Antonia's Line (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Antonia%20(1995),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0
      20,Angels and Insects (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Angels%20and%20Insects%20(1995),0,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,0
      21,Muppet Treasure Island (1996),16-Feb-96,http://us.imdb.com/M/title-exact?Muppet%20Treasure%20Island%20(1996),0,1,1,0,0,1,0,0,0,0,0,0,1,0,0,0,1,0,0
      22,Braveheart (1995),16-Feb-96,http://us.imdb.com/M/title-exact?Braveheart%20(1995),0,1,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0
      23,Taxi Driver (1976),16-Feb-96,http://us.imdb.com/M/title-exact?Taxi%20Driver%20(1976),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0
      24,Rumble in the Bronx (1995),23-Feb-96,http://us.imdb.com/M/title-exact?Hong%20Faan%20Kui%20(1995),0,1,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0
      25,"Birdcage, The (1996)",8-Mar-96,"http://us.imdb.com/M/title-exact?Birdcage,%20The%20(1996)",0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0
      26,"Brothers McMullen, The (1995)",1-Jan-95,"http://us.imdb.com/M/title-exact?Brothers%20McMullen,%20The%20(1995)",0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0
      27,Bad Boys (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Bad%20Boys%20(1995),0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
      28,Apollo 13 (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Apollo%2013%20(1995),0,1,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0
      29,Batman Forever (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Batman%20Forever%20(1995),0,1,1,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,0
      30,Belle de jour (1967),1-Jan-67,http://us.imdb.com/M/title-exact?Belle%20de%20jour%20(1967),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0
      31,Crimson Tide (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Crimson%20Tide%20(1995),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,1,0
      32,Crumb (1994),1-Jan-94,http://us.imdb.com/M/title-exact?Crumb%20(1994),0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0
      33,Desperado (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Desperado%20(1995),0,1,0,0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,0
      34,"Doom Generation, The (1995)",1-Jan-95,"http://us.imdb.com/M/title-exact?Doom%20Generation,%20The%20(1995)",0,0,0,0,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0
      35,Free Willy 2: The Adventure Home (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Free%20Willy%202:%20The%20Adventure%20Home%20(1995),0,0,1,0,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0
      36,Mad Love (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Mad%20Love%20(1995),0,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,0
      37,Nadja (1994),1-Jan-94,http://us.imdb.com/M/title-exact?Nadja%20(1994),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0
      38,"Net, The (1995)",1-Jan-95,"http://us.imdb.com/M/title-exact?Net,%20The%20(1995)",0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0
      39,Strange Days (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Strange%20Days%20(1995),0,1,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,0
      40,"To Wong Foo, Thanks for Everything! Julie Newmar (1995)",1-Jan-95,"http://us.imdb.com/M/title-exact?To%20Wong%20Foo,%20Thanks%20for%20Everything!%20Julie%20Newmar%20(1995)",0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0
      41,Billy Madison (1995),1-Jan-95,http://us.imdb.com/M/title-exact?Billy%20Madison%20(1995),0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0
      42,Clerks (1994),1-Jan-94,http://us.imdb.com/M/title-exact?Clerks%20(1994),0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0
      43,Disclosure (1994),1-Jan-94,http://us.imdb.com/M/title-exact?Disclosure%20(1994),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0
      44,Dolores Claiborne (1994),1-Jan-94,http://us.imdb.com/M/title-exact?Dolores%20Claiborne%20(1994),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0
      45,Eat Drink Man Woman (1994),1-Jan-94,http://us.imdb.com/M/title-exact?Yinshi%20Nan%20Nu%20(1994),0,0,0,0,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0
      46,Exotica (1994),1-Jan-94,http://us.imdb.com/M/title-exact?Exotica%20(1994),0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0
      47,Ed Wood (1994),1-Jan-94,http://us.imdb.com/M/title-exact?Ed%20Wood%20(1994),0,0,0,0,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0
      48,Hoop Dreams (1994),1-Jan-94,http://us.imdb.com/M/title-exact?Hoop%20Dreams%20(1994),0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0
      49,I.Q. (1994),1-Jan-94,http://us.imdb.com/M/title-exact?I.Q.%20(1994),0,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,0,0
      50,Star Wars (1977),1-Jan-77,http://us.imdb.com/M/title-exact?Star%20Wars%20(1977),0,1,1,0,0,0,0,0,0,0,0,0,0,0,1,1,0,1,0

   The following table describes the data.

   .. table:: **Table 1** Movie data description

      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Field            | Type    | Description                                                                                           |
      +==================+=========+=======================================================================================================+
      | movieId          | INT     | Movie ID                                                                                              |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | movieTitle       | VARCHAR | Movie name                                                                                            |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | videoReleaseDate | VARCHAR | Release date                                                                                          |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | IMDbURL          | VARCHAR | IMDb link                                                                                             |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | unknown          | INT     | Whether the movie type is unknown. If yes, the value is **1**; otherwise, the value is **0**.         |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Action           | INT     | Whether the movie type is action. If yes, the value is **1**; otherwise, the value is **0**.          |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Adventure        | INT     | Whether the movie type is adventure. If yes, the value is **1**; otherwise, the value is **0**.       |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Animation        | INT     | Whether the movie type is animation. If yes, the value is **1**; otherwise, the value is **0**.       |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Children         | INT     | Whether the movie type is children. If yes, the value is **1**; otherwise, the value is **0**.        |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Comedy           | INT     | Whether the movie type is comedy. If yes, the value is **1**; otherwise, the value is **0**.          |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Crime            | INT     | Whether the movie type is crime. If yes, the value is **1**; otherwise, the value is **0**.           |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Documentary      | INT     | Whether the movie type is documentary. If yes, the value is **1**; otherwise, the value is **0**.     |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Drama            | INT     | Whether the movie type is drama. If yes, the value is **1**; otherwise, the value is **0**.           |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Fantasy          | INT     | Whether the movie type is fantasy. If yes, the value is **1**; otherwise, the value is **0**.         |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | FilmNoir         | INT     | Whether the movie type is noir. If yes, the value is **1**; otherwise, the value is **0**.            |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Horror           | INT     | Whether the movie type is horror. If yes, the value is **1**; otherwise, the value is **0**.          |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Musical          | INT     | Whether the movie type is musical. If yes, the value is **1**; otherwise, the value is **0**.         |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Mystery          | INT     | Whether the movie type is mystery. If yes, the value is **1**; otherwise, the value is **0**.         |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Romance          | INT     | Whether the movie type is romance. If yes, the value is **1**; otherwise, the value is **0**.         |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | SciFi            | INT     | Whether the movie type is science fiction. If yes, the value is **1**; otherwise, the value is **0**. |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Thriller         | INT     | Whether the movie type is thriller. If yes, the value is **1**; otherwise, the value is **0**.        |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | War              | INT     | Whether the movie type is war. If yes, the value is **1**; otherwise, the value is **0**.             |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+
      | Western          | INT     | Whether the movie type is western. If yes, the value is **1**; otherwise, the value is **0**.         |
      +------------------+---------+-------------------------------------------------------------------------------------------------------+

-  .. _dataartsstudio_04_0032__li4584112342819:

   **ratings.csv**:

   .. code-block::

      userId,movieId,rating,timestamp
      210,40,3,891035994
      224,29,3,888104457
      308,1,4,887736532
      7,32,4,891350932
      10,16,4,877888877
      99,4,5,886519097
      115,20,3,881171009
      138,26,5,879024232
      243,15,3,879987440
      293,5,3,888906576
      162,25,4,877635573
      135,23,4,879857765
      62,21,3,879373460
      59,23,5,888205300
      43,14,2,883955745
      19,4,4,885412840
      5,2,3,875636053
      72,48,4,880036718
      224,26,3,888104153
      299,14,4,877877775
      151,10,5,879524921
      6,14,5,883599249
      250,7,4,878089716
      268,2,2,875744173
      292,11,5,881104093
      181,3,2,878963441
      145,15,2,875270655
      1,33,4,878542699
      276,2,4,874792436
      18,26,4,880129731
      87,40,3,879876917
      272,12,5,879455254
      296,20,5,884196921
      5,17,4,875636198
      128,15,4,879968827
      287,1,5,875334088
      65,47,2,879216672
      1,20,4,887431883
      290,50,5,880473582
      45,25,4,881014015
      109,8,3,880572642
      157,25,3,886890787
      301,33,4,882078228
      62,12,4,879373613
      276,40,3,874791871
      269,22,1,891448072
      10,7,4,877892210
      244,17,2,880607205
      222,26,3,878183043
      185,23,4,883524249
      207,13,3,875506839
      8,22,5,879362183
      222,49,3,878183512
      200,11,5,884129542
      90,25,5,891384789
      15,25,3,879456204
      234,10,3,891227851
      295,39,4,879518279
      217,2,3,889069782
      189,20,5,893264466
      42,44,3,881108548
      268,21,3,875742822
      262,28,3,879792220
      90,22,4,891384357
      270,25,5,876954456
      194,23,4,879522819
      161,48,1,891170745
      58,9,4,884304328
      79,50,4,891271545
      221,48,5,875245462
      223,11,3,891550649
      292,9,4,881104148
      16,8,5,877722736
      17,13,3,885272654
      148,1,4,877019411
      280,1,4,891700426
      110,38,3,886988574
      90,12,5,891383241
      239,9,5,889180446
      311,9,4,884963365
      151,13,3,879542688
      2,50,5,888552084
      8,50,5,879362124
      286,44,3,877532173
      85,25,2,879452769
      274,50,5,878944679
      217,27,1,889070011
      181,14,1,878962392
      297,25,4,874954497
      1,47,4,875072125
      6,23,4,883601365
      222,22,5,878183285
      314,28,5,877888346
      291,15,5,874833668
      94,24,4,885873423
      83,43,4,880308690
      43,40,3,883956468
      44,15,4,878341343
      158,24,4,880134261
      151,12,5,879524368
      66,1,3,883601324
      5,1,4,875635748
      207,25,4,876079113
      109,1,4,880563619
      227,50,4,879035347
      181,1,3,878962392
      213,13,4,878955139
      121,14,5,891390014
      117,15,5,880125887
      85,13,3,879452866
      313,22,3,891014870
      43,5,4,875981421
      11,38,3,891905936
      72,28,4,880036824
      115,8,5,881171982
      95,1,5,879197329
      145,22,5,875273021
      66,7,3,883601355
      267,17,4,878971773
      25,25,5,885853415
      103,24,4,880415847
      87,9,4,879877931
      49,47,5,888068715
      135,39,3,879857931
      269,13,4,891446662
      99,50,5,885679998
      306,14,5,876503995
      291,7,5,874834481
      312,28,4,891698300
      184,36,3,889910195
      305,11,1,886323237
      198,7,4,884205317
      104,7,3,888465972
      293,39,3,888906804
      256,25,5,882150552
      92,15,3,875640189
      1,17,3,875073198
      214,42,5,892668130
      82,14,4,876311280
      305,50,5,886321799
      223,8,2,891550684
      91,28,4,891439243
      315,13,4,879821158
      269,9,4,891446246
      217,7,4,889069741
      49,7,4,888067307
      87,2,4,879876074
      268,1,3,875742341
      262,47,2,879794599
      84,12,5,883452874
      264,33,3,886122644
      224,20,1,888104487
      200,24,2,884127370
      92,24,3,875640448
      276,38,3,874792574
      286,34,5,877534701
      49,38,1,888068289
      311,5,3,884365853
      269,47,4,891448386
      194,4,4,879521397
      57,28,4,883698324
      108,50,4,879879739
      207,4,4,876198457
      181,16,1,878962996
      94,9,5,885872684
      234,20,4,891227979
      68,7,3,876974096
      13,14,4,884538727
      98,47,4,880498898
      53,24,3,879442538
      239,10,5,889180338
      63,20,3,875748004
      276,43,1,874791383
      272,48,4,879455143
      116,7,2,876453915
      26,25,3,891373727
      62,24,4,879372633
      295,47,5,879518166
      63,50,4,875747292
      49,17,2,888068651
      310,24,4,879436242
      7,44,5,891351728
      326,22,4,879874989
      213,12,5,878955409
      222,29,3,878184571
      249,11,5,879640868
      217,22,5,889069741
      189,1,5,893264174
      234,50,4,892079237
      296,48,5,884197091
      81,3,4,876592546
      151,15,4,879524879
      59,12,5,888204260
      246,8,3,884921245
      276,34,2,877934264
      97,50,5,884239471
      244,7,4,880602558
      298,8,5,884182748
      7,28,5,891352341
      41,28,4,890687353

   The following table describes the data.

   .. table:: **Table 2** Rating data description

      ========= ======= ====================================
      Field     Type    Description
      ========= ======= ====================================
      userId    INT     User ID
      movieId   INT     Movie ID
      rating    INT     Rating. The total score is 5 points.
      timestamp VARCHAR Timestamp
      ========= ======= ====================================

.. _dataartsstudio_04_0032__section7296123818418:

Preparing a Data Lake
---------------------

This practice uses DWS as the data foundation.

For details about how to create a DWS cluster, see "Cluster Configuration" > "Creating a Cluster" in *Data Warehouse Service (DWS) User Guide*. The DWS cluster must meet the following requirements so that it can communicate with the DataArts Studio instance:

-  If the CDM cluster in the DataArts Studio instance and the DWS cluster are in different regions, a public network or a dedicated connection is required.
-  If the CDM cluster in the DataArts Studio instance and the GaussDB(DWS) cluster are in the same region, VPC, subnet, and security group, they can communicate with each other by default. If they are in the same VPC but in different subnets or security groups, you must configure routing rules and security group rules. For details about how to configure routing rules, see "Adding Routes to a Route Table" in *Virtual Private Cloud (VPC) x.x.x User Guide* in *Virtual Private Cloud (VPC) x.x.x Usage Guide*. For details about how to configure security group rules, see "Security Group" > "Adding a Security Group Rule" in *Virtual Private Cloud (VPC) x.x.x User Guide* in *Virtual Private Cloud (VPC) x.x.x Usage Guide*.
-  The DWS cluster and the DataArts Studio workspace belong to the same enterprise project. If they do not, you can modify the enterprise project of the workspace.

After creating a DWS cluster, you need to create a DWS connection in Management Center, create a database and schema through the DataArts Factory module, and run an SQL statement to create a DWS table. The procedure is as follows:

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **Management Center**.

#. On the displayed **Manage Data Connections** page, click **Create Data Connection**.


   .. figure:: /_static/images/en-us_image_0000002269210125.png
      :alt: **Figure 1** Creating a data connection

      **Figure 1** Creating a data connection

#. .. _dataartsstudio_04_0032__li6594811184817:

   On the displayed page, configure the following parameters and click **OK**.

   -  **Data Connection Type**: Select **DWS**.
   -  **Name**: Enter **dws_link**.
   -  **Tag**: This parameter is optional. You can enter the name of a new tag or select an existing tag from the drop-down list box.
   -  **Applicable Modules**: Retain the default settings.
   -  **SSL Encryption**: Retain the same setting as that for the source GaussDB(DWS) cluster.
   -  **Connection Type**: Select **Proxy connection**.
   -  **Manual**: Select **Cluster Name Mode**. **IP** and **Port** are automatically set.
   -  **DWS Cluster Name**: Select the GaussDB(DWS) cluster that you have created.
   -  **Agent**: Select a CDM cluster as the connection agent. The CDM cluster must be able to communicate with the DWS cluster. In this example, you can select the DataArts Migration cluster that is automatically created when the DataArts Studio instance is created.
   -  **Username**: Enter the database username that you specified when creating the DWS cluster. The default username is **dbadmin**.
   -  **Password**: Enter the password that you specified when creating the DWS cluster for accessing the database.


   .. figure:: /_static/images/en-us_image_0000002269130021.png
      :alt: **Figure 2** DWS connection parameters

      **Figure 2** DWS connection parameters

#. Go to the **DataArts Factory** page.

#. .. _dataartsstudio_04_0032__li646420431311:

   Create a DWS database and a database schema.

   a. Right-click the DWS connection and select **Create Database** to create a database named **demo** for storing data tables.


      .. figure:: /_static/images/en-us_image_0000002269130025.png
         :alt: **Figure 3** Creating a database

         **Figure 3** Creating a database

   b. Expand the DWS connection directory to the database schema level, right-click **schemas**, and select **Create Schema** to create a schema named **dgc** for storing data tables.


      .. figure:: /_static/images/en-us_image_0000002548191863.png
         :alt: **Figure 4** Creating a database schema

         **Figure 4** Creating a database schema

#. Create a DWS SQL script used to create data tables by entering DWS SQL statements in the editor.


   .. figure:: /_static/images/en-us_image_0000002269130013.png
      :alt: **Figure 5** Creating a script

      **Figure 5** Creating a script

#. In the SQL editor, enter the following SQL statements and click **Execute** to create data tables. Among them, **movies_item** and **ratings_item** are original data tables, to which data will be migrated from OBS through CDM. **top_rating_movie** and **top_active_movie** are result tables which store analysis results.

   .. code-block::

      SET SEARCH_PATH TO dgc;
      CREATE TABLE IF NOT EXISTS movies_item(
          movieId INT,
          movieTitle VARCHAR,
          videoReleaseDate VARCHAR,
          IMDbURL VARCHAR,
          unknown INT,
          Action INT,
          Adventure INT,
          Animation INT,
          Children INT,
          Comedy INT,
          Crime INT,
          Documentary INT,
          Drama INT,
          Fantasy INT,
          FilmNoir INT,
          Horror INT,
          Musical INT,
          Mystery INT,
          Romance INT,
          SciFi INT,
          Thriller INT,
          War INT,
          Western INT
      );

      CREATE TABLE IF NOT EXISTS ratings_item(
        userId INT,
        movieId INT,
        rating INT,
        timestamp VARCHAR
      );

      CREATE TABLE IF NOT EXISTS top_rating_movie(
        movieTitle VARCHAR,
        avg_rating float,
        rating_user_number int
      );

      CREATE TABLE IF NOT EXISTS top_active_movie(
        movieTitle VARCHAR,
        avg_rating float,
        rating_user_number int
      );


   .. figure:: /_static/images/en-us_image_0000002269130009.png
      :alt: **Figure 6** Creating data tables

      **Figure 6** Creating data tables

   The key parameters are as follows:

   -  **Data Connection**: DWS data connection created in :ref:`Step 4 <dataartsstudio_04_0032__li6594811184817>`
   -  **Database**: database created in :ref:`Step 6 <dataartsstudio_04_0032__li646420431311>`

#. After the script is executed successfully, run the following script to check whether the data tables are created successfully. After confirming that the data tables are created successfully, you can close the script as it is no longer needed.

   .. code-block::

      SELECT * FROM pg_tables;

.. _dataartsstudio_04_0032__section134011417816:

Preparing Authentication Data
-----------------------------

If you want to migrate OBS data using CDM, you need AK/SK authentication. Therefore, you must create an AK/SK pair.

-  Access Key ID (AK): indicates the ID of the access key, which is a unique identifier associated with a secret access key and is used in conjunction with a secret access key to sign requests cryptographically.
-  Secret Access Key (SK): indicates the key used with its associated AK to cryptographically sign requests and identify request senders to prevent requests from being modified.

To obtain an access key, perform the following steps:

#. Log in to the management console, move the cursor to the username in the upper right corner, and select **My Credentials** from the drop-down list.

#. On the **My Credentials** page, choose **Access Keys**, and click **Create Access Key**. See :ref:`Figure 7 <dataartsstudio_04_0032__en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615>`.

   .. _dataartsstudio_04_0032__en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615:

   .. figure:: /_static/images/en-us_image_0000002269129949.png
      :alt: **Figure 7** Clicking Create Access Key

      **Figure 7** Clicking Create Access Key

#. Click **OK** and save the access key file as prompted. The access key file will be saved to your browser's configured download location. Open the **credentials.csv** file to view **Access Key Id** and **Secret Access Key**.

   .. note::

      -  Only two access keys can be added for each user.
      -  To ensure access key security, the access key is automatically downloaded only when it is generated for the first time and cannot be obtained from the management console later. Keep them properly.
