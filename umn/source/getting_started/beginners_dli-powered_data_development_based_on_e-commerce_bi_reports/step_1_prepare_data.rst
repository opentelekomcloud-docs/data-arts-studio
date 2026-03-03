:original_name: dataartsstudio_04_0022.html

.. _dataartsstudio_04_0022:

Step 1: Prepare Data
====================

.. _dataartsstudio_04_0022__section485519219101:

Preparations Before Using DataArts Studio
-----------------------------------------

If you are new to DataArts Studio, create a cloud platform account, create a DataArts Studio instance, create workspaces, and make other preparations. For details, see "Creating and Configuring a DataArts Studio Instance" in *User Guide*. Then you can go to the created workspace and start using DataArts Studio.

.. _dataartsstudio_04_0022__en-us_topic_0119212931_section1564194492417:

Preparing Data Sources
----------------------

This practice analyzes the data features of the users and products of an e-commerce store. (The data is from BI reports.)

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

   c. In the **fast-demo** OBS bucket, create folders **user_data**, **product_data**, **comment_data**, and **action_data**, and upload files **user_data.csv**, **product_data.csv**, **comment_data.csv**, and **action_data.csv** to the corresponding folders.

      .. note::

         When associating a CSV table with DLI to create an OBS foreign table, you cannot specify the file name and can only specify the file path. Therefore, you need to place CSV tables in different file paths and ensure that each file path contains only the required CSV table.

      For details about how to upload a file on the OBS console, see in *Object Storage Service Console Operation Guide*\ **Console Operation Guide > Getting Started > Uploading a File** in *Object Storage Service 3.0* *Usage Guide*.

This practice involves the following sample data: user data (:ref:`user_data.csv <dataartsstudio_04_0022__li132871346727>`), product data (:ref:`product_data.csv <dataartsstudio_04_0022__li18914287154>`), comment data (:ref:`comment_data.csv <dataartsstudio_04_0022__li166101229182018>`), and action data (:ref:`action_data.csv <dataartsstudio_04_0022__li62981631172015>`). Descriptions of the data are as follows:

-  .. _dataartsstudio_04_0022__li132871346727:

   **user_data.csv**:

   .. code-block::

      user_id,age,gender,rank,register_time
      100001,20,0,1,2021/1/1
      100002,22,1,2,2021/1/2
      100003,21,0,3,2021/1/3
      100004,24,2,5,2021/1/4
      100005,50,2,9,2021/1/5
      100006,20,1,3,2021/1/6
      100007,18,1,1,2021/1/7
      100008,20,1,6,2021/1/8
      100009,60,0,4,2021/1/9
      100010,20,1,1,2021/1/10
      100011,35,0,5,2021/1/11
      100012,20,1,1,2021/1/12
      100013,7,0,1,2021/1/13
      100014,64,0,8,2021/1/14
      100015,20,1,1,2021/1/15
      100016,33,1,7,2021/1/16
      100017,20,0,1,2021/1/17
      100018,15,1,1,2021/1/18
      100019,20,1,9,2021/1/19
      100020,33,0,1,2021/1/20
      100021,20,0,1,2021/1/21
      100022,22,1,5,2021/1/22
      100023,20,1,1,2021/1/23
      100024,20,0,1,2021/1/24
      100025,34,0,7,2021/1/25
      100026,34,1,1,2021/1/26
      100027,20,1,8,2021/1/27
      100028,20,0,1,2021/1/28
      100029,56,0,5,2021/1/29
      100030,20,1,1,2021/1/30
      100031,22,1,8,2021/1/31
      100032,20,0,1,2021/2/1
      100033,32,1,0,2021/2/2
      100034,20,1,1,2021/2/3
      100035,45,0,6,2021/2/4
      100036,20,0,1,2021/2/5
      100037,67,1,4,2021/2/6
      100038,78,0,6,2021/2/7
      100039,11,1,8,2021/2/8
      100040,8,0,0,2021/2/9

   The following table describes the data.

   .. table:: **Table 1** User data description

      +-----------------+-----------------+------------------------+-----------------------------------------------------------------+
      | Field           | Type            | Description            | Value                                                           |
      +=================+=================+========================+=================================================================+
      | user_id         | int             | User ID                | Anonymized                                                      |
      +-----------------+-----------------+------------------------+-----------------------------------------------------------------+
      | age             | int             | Age group              | **-1** indicates that the user age is unknown.                  |
      +-----------------+-----------------+------------------------+-----------------------------------------------------------------+
      | gender          | int             | Gender                 | -  **0**: male                                                  |
      |                 |                 |                        | -  **1**: female                                                |
      |                 |                 |                        | -  **2**: confidential                                          |
      +-----------------+-----------------+------------------------+-----------------------------------------------------------------+
      | rank            | Int             | User level             | The greater the value of this field, the higher the user level. |
      +-----------------+-----------------+------------------------+-----------------------------------------------------------------+
      | register_time   | string          | User registration date | Unit: day                                                       |
      +-----------------+-----------------+------------------------+-----------------------------------------------------------------+

-  .. _dataartsstudio_04_0022__li18914287154:

   **product_data.csv**:

   .. code-block::

      product_id,a1,a2,a3,category,brand
      200001,1,1,1,300001,400001
      200002,2,2,2,300002,400001
      200003,3,3,3,300003,400001
      200004,1,2,3,300004,400001
      200005,3,2,1,300005,400002
      200006,1,1,1,300006,400002
      200007,2,2,2,300007,400002
      200008,3,3,3,300008,400002
      200009,1,2,3,300009,400003
      200010,3,2,1,300010,400003
      200011,1,1,1,300001,400003
      200012,2,2,2,300002,400003
      200013,3,3,3,300003,400004
      200014,1,2,3,300004,400004
      200015,3,2,1,300005,400004
      200016,1,1,1,300006,400004
      200017,2,2,2,300007,400005
      200018,3,3,3,300008,400005
      200019,1,2,3,300009,400005
      200020,3,2,1,300010,400005
      200021,1,1,1,300001,400006
      200022,2,2,2,300002,400006
      200023,3,3,3,300003,400006
      200024,1,2,3,300004,400006
      200025,3,2,1,300005,400007
      200026,1,1,1,300006,400007
      200027,2,2,2,300007,400007
      200028,3,3,3,300008,400007
      200029,1,2,3,300009,400008
      200030,3,2,1,300010,400008
      200031,1,1,1,300001,400008
      200032,2,2,2,300002,400008
      200033,3,3,3,300003,400009
      200034,1,2,3,300004,400009
      200035,3,2,1,300005,400009
      200036,1,1,1,300006,400009
      200037,2,2,2,300007,400010
      200038,3,3,3,300008,400010
      200039,1,2,3,300009,400010
      200040,3,2,1,300010,400010

   The following table describes the data.

   .. table:: **Table 2** Product data description

      +------------+------+-------------+-------------------------------------------------------+
      | Field      | Type | Description | Value                                                 |
      +============+======+=============+=======================================================+
      | product_id | int  | Product No. | Anonymized                                            |
      +------------+------+-------------+-------------------------------------------------------+
      | a1         | int  | Attribute 1 | Enumerated value. The value **-1** indicates unknown. |
      +------------+------+-------------+-------------------------------------------------------+
      | a2         | int  | Attribute 2 | Enumerated value. The value **-1** indicates unknown. |
      +------------+------+-------------+-------------------------------------------------------+
      | a3         | int  | Attribute 3 | Enumerated value. The value **-1** indicates unknown. |
      +------------+------+-------------+-------------------------------------------------------+
      | category   | int  | Category ID | Anonymized                                            |
      +------------+------+-------------+-------------------------------------------------------+
      | brand      | int  | Brand ID    | Anonymized                                            |
      +------------+------+-------------+-------------------------------------------------------+

-  .. _dataartsstudio_04_0022__li166101229182018:

   **comment_data.csv**:

   .. code-block::

      deadline,product_id,comment_num,has_bad_comment,bad_comment_rate
      2021/3/1,200001,4,0,0
      2021/3/1,200002,1,0,0
      2021/3/1,200003,2,2,0.1
      2021/3/1,200004,3,3,0.05
      2021/3/1,200005,1,0,0
      2021/3/1,200006,2,0,0
      2021/3/1,200007,3,2,0.01
      2021/3/1,200008,4,1,0.001
      2021/3/1,200009,4,0,0
      2021/3/1,200010,1,0,0
      2021/3/1,200011,2,2,0.2
      2021/3/1,200012,3,3,0.04
      2021/3/1,200013,1,0,0
      2021/3/1,200014,2,2,0.2
      2021/3/1,200015,3,2,0.05
      2021/3/1,200016,4,1,0.003
      2021/3/1,200017,4,0,0
      2021/3/1,200018,1,0,0
      2021/3/1,200019,2,2,0.3
      2021/3/1,200020,3,3,0.03
      2021/3/1,200021,1,0,0
      2021/3/1,200022,2,5,1
      2021/3/1,200023,3,2,0.07
      2021/3/1,200024,4,1,0.006
      2021/3/1,200025,4,0,0
      2021/3/1,200026,1,0,0
      2021/3/1,200027,2,2,0.4
      2021/3/1,200028,3,3,0.03
      2021/3/1,200029,1,0,0
      2021/3/1,200030,2,5,1
      2021/3/1,200031,3,2,0.02
      2021/3/1,200032,4,1,0.003
      2021/3/1,200033,4,0,0
      2021/3/1,200034,1,0,0
      2021/3/1,200035,2,2,0.5
      2021/3/1,200036,3,3,0.06
      2021/3/1,200037,1,0,0
      2021/3/1,200038,2,1,0.01
      2021/3/1,200039,3,2,0.01
      2021/3/1,200040,4,1,0.009

   The following table describes the data.

   .. table:: **Table 3** Comment data description

      +------------------+-----------------+-------------------------------------------+---------------------------------+
      | Field            | Type            | Description                               | Value                           |
      +==================+=================+===========================================+=================================+
      | deadline         | string          | Deadline                                  | Unit: day                       |
      +------------------+-----------------+-------------------------------------------+---------------------------------+
      | product_id       | int             | Product No.                               | Anonymized                      |
      +------------------+-----------------+-------------------------------------------+---------------------------------+
      | comment_num      | int             | Segments of the accumulated comment count | -  **0**: no comment            |
      |                  |                 |                                           | -  **1**: one comment           |
      |                  |                 |                                           | -  **2**: 2 to 10 comments      |
      |                  |                 |                                           | -  **3**: 11 to 50 comments     |
      |                  |                 |                                           | -  **4**: more than 50 comments |
      +------------------+-----------------+-------------------------------------------+---------------------------------+
      | has_bad_comment  | int             | Whether there are negative comments       | **0**: no; **1**: yes           |
      +------------------+-----------------+-------------------------------------------+---------------------------------+
      | bad_comment_rate | float           | Dissatisfaction rate                      | Proportion of negative comments |
      +------------------+-----------------+-------------------------------------------+---------------------------------+

-  .. _dataartsstudio_04_0022__li62981631172015:

   **action_data.csv**:

   .. code-block::

      user_id,product_id,time,model_id,type
      100001,200001,2021/1/1,1,view
      100001,200001,2021/1/1,1,add
      100001,200001,2021/1/1,1,delete
      100001,200002,2021/1/2,1,view
      100001,200002,2021/1/2,1,add
      100001,200002,2021/1/2,1,buy
      100001,200002,2021/1/2,1,like
      100002,200003,2021/1/1,1,view
      100002,200003,2021/1/1,1,add
      100002,200003,2021/1/1,1,delete
      100002,200004,2021/1/2,1,view
      100002,200004,2021/1/2,1,add
      100002,200004,2021/1/2,1,buy
      100002,200004,2021/1/2,1,like
      100003,200001,2021/1/1,1,view
      100003,200001,2021/1/1,1,add
      100003,200001,2021/1/1,1,delete
      100004,200002,2021/1/2,1,view
      100005,200002,2021/1/2,1,add
      100006,200002,2021/1/2,1,buy
      100007,200002,2021/1/2,1,like
      100001,200003,2021/1/1,1,view
      100002,200003,2021/1/1,1,add
      100003,200003,2021/1/1,1,delete
      100004,200004,2021/1/2,1,view
      100005,200004,2021/1/2,1,add
      100006,200004,2021/1/2,1,buy
      100007,200004,2021/1/2,1,like
      100001,200005,2021/1/3,1,view
      100001,200005,2021/1/3,1,add
      100001,200005,2021/1/3,1,delete
      100001,200006,2021/1/3,1,view
      100001,200006,2021/1/4,1,add
      100001,200006,2021/1/4,1,buy
      100001,200006,2021/1/4,1,like
      100010,200005,2021/1/3,1,view
      100010,200005,2021/1/3,1,add
      100010,200005,2021/1/3,1,delete
      100010,200006,2021/1/3,1,view
      100010,200006,2021/1/4,1,add
      100010,200006,2021/1/4,1,buy
      100010,200006,2021/1/4,1,like
      100001,200007,2021/1/2,1,buy
      100001,200007,2021/1/2,1,like
      100002,200007,2021/1/1,1,view
      100002,200007,2021/1/1,1,add
      100002,200007,2021/1/1,1,delete
      100002,200007,2021/1/2,1,view
      100002,200007,2021/1/2,1,add
      100002,200008,2021/1/2,1,like
      100002,200008,2021/1/2,1,like
      100003,200008,2021/1/1,1,view
      100003,200008,2021/1/1,1,add
      100003,200008,2021/1/1,1,delete
      100004,200008,2021/1/2,1,view
      100005,200009,2021/1/2,1,like
      100006,200009,2021/1/2,1,buy
      100007,200010,2021/1/2,1,like
      100001,200010,2021/1/1,1,view
      100002,200010,2021/1/1,1,add
      100003,200010,2021/1/1,1,delete
      100004,200010,2021/1/2,1,view
      100005,200010,2021/1/2,1,like
      100006,200010,2021/1/2,1,buy
      100007,200010,2021/1/2,1,like
      100001,200010,2021/1/3,1,view
      100001,200010,2021/1/3,1,add
      100001,200010,2021/1/3,1,delete
      100001,200011,2021/1/3,1,view
      100001,200011,2021/1/4,1,like
      100001,200011,2021/1/4,1,buy
      100001,200011,2021/1/4,1,like
      100010,200012,2021/1/3,1,view
      100011,200012,2021/1/3,1,like
      100011,200012,2021/1/3,1,delete
      100011,200013,2021/1/3,1,view
      100011,200013,2021/1/4,1,like
      100011,200014,2021/1/4,1,buy
      100011,200014,2021/1/4,1,like
      100007,200022,2021/1/2,1,like
      100001,200022,2021/1/1,1,view
      100002,200023,2021/1/1,1,add
      100003,200023,2021/1/1,1,delete
      100004,200023,2021/1/2,1,like
      100005,200024,2021/1/2,1,add
      100006,200024,2021/1/2,1,buy
      100007,200025,2021/1/2,1,like
      100001,200025,2021/1/3,1,view
      100001,200026,2021/1/3,1,like
      100001,200026,2021/1/3,1,delete
      100001,200027,2021/1/3,1,view
      100001,200027,2021/1/4,1,like
      100001,200027,2021/1/4,1,buy
      100001,200028,2021/1/4,1,like
      100010,200029,2021/1/3,1,view
      100011,200030,2021/1/3,1,like
      100011,200031,2021/1/3,1,delete
      100011,200032,2021/1/3,1,view
      100011,200033,2021/1/4,1,like
      100011,200034,2021/1/4,1,buy
      100011,200035,2021/1/4,1,like

   The following table describes the data.

   .. table:: **Table 4** Action data description

      +-----------------+-----------------+-------------------------------------------------------+-----------------+
      | Field           | Type            | Description                                           | Value           |
      +=================+=================+=======================================================+=================+
      | user_id         | int             | User ID                                               | Anonymized      |
      +-----------------+-----------------+-------------------------------------------------------+-----------------+
      | product_id      | int             | Product No.                                           | Anonymized      |
      +-----------------+-----------------+-------------------------------------------------------+-----------------+
      | time            | string          | Time of action                                        | ``-``           |
      +-----------------+-----------------+-------------------------------------------------------+-----------------+
      | model_id        | string          | Module ID                                             | Anonymized      |
      +-----------------+-----------------+-------------------------------------------------------+-----------------+
      | type            | string          | -  View (browsing the product details page)           | ``-``           |
      |                 |                 | -  Add (adding a product to the shopping cart)        |                 |
      |                 |                 | -  Delete (removing a product from the shopping cart) |                 |
      |                 |                 | -  Buy (placing an order)                             |                 |
      |                 |                 | -  Like (adding a product to the favorite list)       |                 |
      +-----------------+-----------------+-------------------------------------------------------+-----------------+

.. _dataartsstudio_04_0022__section168683560519:

Preparing a Data Lake
---------------------

This practice uses DLI as the data foundation. To ensure network connectivity between DataArts Studio and DLI, ensure that you select the same region and enterprise project as those of the DataArts Studio instance when creating a DLI queue.

.. note::

   -  The version of the default Spark component of the default DLI queue is not up-to-date, and an error may be reported indicating that a table creation statement cannot be executed. In this case, you are advised to create a queue to run your tasks. To enable the execution of table creation statements in the default queue, contact the customer service or technical support of the DLI service.

   -  The default queue **default** of DLI is only used for trial. It may be occupied by multiple users at a time. Therefore, it is possible that you fail to obtain the resource for related operations. If the execution takes a long time or fails, you are advised to try again during off-peak hours or use a self-built queue to run the job.

After enabling DLI, you need to create a DLI connection in Management Center, create a database through the DataArts Factory module, and run an SQL statement to create an OBS foreign table. The procedure is as follows:

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **Management Center**.

#. On the displayed **Manage Data Connections** page, click **Create Data Connection**.


   .. figure:: /_static/images/en-us_image_0000002269210125.png
      :alt: **Figure 1** Creating a data connection

      **Figure 1** Creating a data connection

#. .. _dataartsstudio_04_0022__li4298133815461:

   Create a DLI data connection. Select **DLI** for **Data Connection Type**, set **Name** to **dli**, and retain the default values for other parameters.

   Click **Test** to test the connection. If the test is successful, click **Save**.


   .. figure:: /_static/images/en-us_image_0000002269130181.png
      :alt: **Figure 2** Creating a data connection

      **Figure 2** Creating a data connection

#. Go to the **DataArts Factory** page.

#. .. _dataartsstudio_04_0022__li17522165311514:

   Right-click the DLI connection to create a database named **BI** for storing data tables. For how to create a database, see :ref:`Figure 3 <dataartsstudio_04_0022__fig1221414337597>`.

   .. _dataartsstudio_04_0022__fig1221414337597:

   .. figure:: /_static/images/en-us_image_0000002269130185.png
      :alt: **Figure 3** Creating a database

      **Figure 3** Creating a database

#. Create a DLI SQL script used to create data tables by entering DLI SQL statements in the editor.


   .. figure:: /_static/images/en-us_image_0000002269129953.png
      :alt: **Figure 4** Creating a script

      **Figure 4** Creating a script

#. In the SQL editor, enter the following SQL statements and click **Execute** to create data tables. Among them, **user**, **product**, **comment**, and **action** are OBS foreign tables that store raw data. The data in these files is from CSV files in specified OBS paths. **top_like_product** and **top_bad_comment_product** are DLI tables that store analysis results.

   .. code-block::

      create table user(
        user_id int,
        age int,
        gender int,
        rank int,
        register_time string
      ) USING csv OPTIONS (path "obs://fast-demo/user_data");
      create table product(
        product_id int,
        a1 int,
        a2 int,
        a3 int,
        category int,
        brand int
      ) USING csv OPTIONS (path "obs://fast-demo/product_data");
      create table comment(
        deadline string,
        product_id int,
        comment_num int,
        has_bad_comment int,
        bad_comment_rate float
      ) USING csv OPTIONS (path "obs://fast-demo/comment_data");
      create table action(
        user_id int,
        product_id int,
        time string,
        model_id string,
        type string
      ) USING csv OPTIONS (path "obs://fast-demo/action_data");
      create table top_like_product(brand int, like_count int);
      create table top_bad_comment_product(product_id int, comment_num int, bad_comment_rate float);


   .. figure:: /_static/images/en-us_image_0000002269210285.png
      :alt: **Figure 5** Creating data tables

      **Figure 5** Creating data tables

   The key parameters are as follows:

   -  **Data Connection**: DLI data connection created in :ref:`Step 4 <dataartsstudio_04_0022__li4298133815461>`
   -  **Database**: database created in :ref:`Step 6 <dataartsstudio_04_0022__li17522165311514>`
   -  **Resource Queue**: The default resource queue **default** can be used.

      .. note::

         -  The version of the default Spark component of the default DLI queue is not up-to-date, and an error may be reported indicating that a table creation statement cannot be executed. In this case, you are advised to create a queue to run your tasks. To enable the execution of table creation statements in the default queue, contact the customer service or technical support of the DLI service.

         -  The default queue **default** of DLI is only used for trial. It may be occupied by multiple users at a time. Therefore, it is possible that you fail to obtain the resource for related operations. If the execution takes a long time or fails, you are advised to try again during off-peak hours or use a self-built queue to run the job.

#. After the script is executed successfully, run the following script to check whether the data tables are created successfully.

   .. code-block::

      SHOW TABLES;

   .. note::

      After confirming that the data tables are created, you can close the script as it is no longer needed.
