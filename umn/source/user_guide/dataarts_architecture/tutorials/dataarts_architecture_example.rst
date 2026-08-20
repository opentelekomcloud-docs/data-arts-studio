:original_name: dataartsstudio_01_0627.html

.. _dataartsstudio_01_0627:

DataArts Architecture Example
=============================

DataArts Architecture can be used to create entity-relationship (ER) models and dimensional models to standardize and visualize data development and output data governance methods that can guide development personnel to work with ease.

This section covers the following scenarios:

-  Design a data model for the taxi travel data in an MRS Hive data lake.

-  The original taxi travel data table **sdi_taxi_trip_data** is stored in the **demo_sdi_db** database.

-  The following table lists the data fields in the original data table **sdi_taxi_trip_data**.

   The following table lists the taxi trip data:

   .. table:: **Table 1** Taxi trip data

      +-----------------------+-----------------------+------------------------------------------------+
      | No.                   | Field Name            | Field Description                              |
      +=======================+=======================+================================================+
      | 1                     | VendorID              | Vendor ID.                                     |
      |                       |                       |                                                |
      |                       |                       | Possible values are:                           |
      |                       |                       |                                                |
      |                       |                       | 1=A Company                                    |
      |                       |                       |                                                |
      |                       |                       | 2=B Company                                    |
      +-----------------------+-----------------------+------------------------------------------------+
      | 2                     | tpep_pickup_datetime  | Time when a passenger gets on a taxi.          |
      +-----------------------+-----------------------+------------------------------------------------+
      | 3                     | tpep_dropoff_datetime | Time when a passenger gets off a taxi.         |
      +-----------------------+-----------------------+------------------------------------------------+
      | 4                     | passenger_count       | Number of passengers.                          |
      +-----------------------+-----------------------+------------------------------------------------+
      | 5                     | trip_distance         | Driving distance.                              |
      +-----------------------+-----------------------+------------------------------------------------+
      | 6                     | ratecodeid            | Charge rate code.                              |
      |                       |                       |                                                |
      |                       |                       | Possible values are:                           |
      |                       |                       |                                                |
      |                       |                       | 1=Standard rate                                |
      |                       |                       |                                                |
      |                       |                       | 2=JFK                                          |
      |                       |                       |                                                |
      |                       |                       | 3=Newark                                       |
      |                       |                       |                                                |
      |                       |                       | 4=Nassau or Westchester                        |
      |                       |                       |                                                |
      |                       |                       | 5=Negotiated fare                              |
      |                       |                       |                                                |
      |                       |                       | 6=Group ride                                   |
      +-----------------------+-----------------------+------------------------------------------------+
      | 7                     | store_fwd_flag        | Store-and-forward flag.                        |
      +-----------------------+-----------------------+------------------------------------------------+
      | 8                     | PULocationID          | Location at which a passenger gets on a taxi.  |
      +-----------------------+-----------------------+------------------------------------------------+
      | 9                     | DOLocationID          | Location at which a passenger gets off a taxi. |
      +-----------------------+-----------------------+------------------------------------------------+
      | 10                    | payment_type          | Payment type.                                  |
      |                       |                       |                                                |
      |                       |                       | Possible values are:                           |
      |                       |                       |                                                |
      |                       |                       | 1=Credit card                                  |
      |                       |                       |                                                |
      |                       |                       | 2=Cash                                         |
      |                       |                       |                                                |
      |                       |                       | 3=No charge                                    |
      |                       |                       |                                                |
      |                       |                       | 4=Dispute                                      |
      |                       |                       |                                                |
      |                       |                       | 5=Unknown                                      |
      |                       |                       |                                                |
      |                       |                       | 6=Voided trip                                  |
      +-----------------------+-----------------------+------------------------------------------------+
      | 11                    | fare_amount           | Fare amount.                                   |
      +-----------------------+-----------------------+------------------------------------------------+
      | 12                    | extra                 | Extra fee.                                     |
      +-----------------------+-----------------------+------------------------------------------------+
      | 13                    | mta_tax               | MTA tax.                                       |
      +-----------------------+-----------------------+------------------------------------------------+
      | 14                    | tip_amount            | Tip amount.                                    |
      +-----------------------+-----------------------+------------------------------------------------+
      | 15                    | tolls_amount          | Toll amount.                                   |
      +-----------------------+-----------------------+------------------------------------------------+
      | 16                    | improvement_surcharge | Improvement surcharge.                         |
      +-----------------------+-----------------------+------------------------------------------------+
      | 17                    | total_amount          | Total amount.                                  |
      +-----------------------+-----------------------+------------------------------------------------+

The process of using DataArts Architecture is as follows:

#. **Preparations**

   -  :ref:`Add reviewers <dataartsstudio_01_0627__section545333619504>`: In the DataArts Architecture module, all business processes must be approved. Therefore, add reviewers first before conducting any operations. Only the workspace admin has the permissions required to add reviewers.
   -  :ref:`Configuration Center <dataartsstudio_01_0627__section83068019428>` provides abundant custom options. You can customize the configuration to meet your demands.

#. **Data Survey**: A data survey involves collecting data that is generated when sorting business requirements, creating business processes, and classifying data subjects based on the existing business data and industry status.

   -  :ref:`Subject design <dataartsstudio_01_0627__en-us_topic_0222298525_section21581824122814>` is a hierarchical architecture that classifies and defines data to help clarify data assets and specify relationships between business domains and business objects.
   -  **Process design**: This example does not contain this. Process design is to generate a structured framework of data processing process, including the categories, levels, boundaries, scope, and input/output relationships, and reflect the business models and characteristics of your enterprise.

#. **Standards**: Create lookup tables and data standards.

   -  :ref:`Create and publish a lookup table <dataartsstudio_01_0627__section142244103311>`: A lookup table includes a series of allowed values and additional text descriptions that are generally associated with data standards to generate a range of values for the verification of quality monitoring rules.
   -  :ref:`Create and publish a data standard <dataartsstudio_01_0627__section139902116499>`: A data standard refers to the description of attribute data meanings and business rules that enterprises must comply with. It describes the common understanding of certain data at the company level.

#. **Models**: Use ER modeling and dimensional modeling methods to perform hierarchical modeling.

   -  :ref:`Data warehouse planning: Create a model at the SDI and DWI layers, respectively. <dataartsstudio_01_0627__en-us_topic_0222298525_section945153616402>`

      -  **SDI** stands for Source Data Integration and is the source data layer. SDI is a simple implementation of source system data.
      -  **DWI** stands for Data Warehouse Integration, also called the data consolidation layer. DWI integrates and cleans data from multiple source systems, and implements entity relationship modeling based on the three normal forms.

   -  :ref:`Dimensional modeling: Create and publish a dimension at the DWR layer. <dataartsstudio_01_0627__section265510426117>` & :ref:`Creating and Publishing a Fact Table for the DWR Layer <dataartsstudio_01_0627__section665784223319>`.

      -  **Data Warehouse Report (DWR)** is based on the multi-dimensional model and its data granularity is the same as that of the DWI layer.
      -  **Dimension** is the perspective to observe and analyze business data and assist in data aggregation, drilling, slicing, and analysis, and used as a GROUP BY condition in SQL statements.
      -  A **fact table** that belongs to a business process can enrich the affair information corresponding to the specific business process.

#. :ref:`Metric design: Create and publish a technical metric <dataartsstudio_01_0627__section1222433193512>`: Create and publish a business metric (not involved in this example) and a technical metric. Technical metrics are classified into atomic, derivative, and compound metrics.

   -  A **metric** consists of its name and value. The metric name and its definition reflect the quality and quantity of the metric. The metric value reflects the quantifiable values of the specified time, location, and condition of the metric.

      Business metrics are used to guide technical metrics, and technical metrics are used to implement business metrics.

   -  **Atomic metrics** are generated based on dimension tables and fact tables of a multidimensional model. The objects and the finest data granularity of an atomic metric are consistent with those of the multidimensional model.

      An atomic metric usually consists of measures and attributes related with measures and business objects, all of which aim to support agile self-service consumption of the metric.

   -  **Derivative metrics** are aggregated from the definitions, modifiers, and dimensions of atomic metrics. Therefore, their definitions, modifiers, and dimensions are derived from the attributes of atomic metric associated tables as well.

   -  **Compound metrics** are generated by adding one or more derivative metrics. The dimensions and modifiers of a compound metric are the same as those of the derivative metrics.

      New dimensions and modifiers cannot be generated outside the scope of derivative metrics, dimensions, and modifiers.

#. :ref:`Data mart: Create and publish a summary table at the DM layer <dataartsstudio_01_0627__section829585916339>`.

   -  **Data Mart (DM)** is where multiple types of data are summarized. DM is designed to display the summarized data.
   -  A **summary table** consists of specific analysis objects (for example, members) and related statistical metrics. The statistical metrics included in a summary table have the same statistical granularity (for example, members). The summary table provides users with all statistics-granularity-themed data (such as a member theme market).

.. _dataartsstudio_01_0627__section545333619504:

Adding Reviewers
----------------

In the DataArts Architecture module, all modeling steps must be reviewed. Therefore, you need to add a reviewer first. **DARTS** **Administrator** or the workspace administrator has the permission to add reviewers.

#. On the DataArts Studio console, locate a workspace and click **DataArts Architecture**.

#. In the navigation pane on the left, choose **Configuration Center**. On the displayed **Reviewers** page, click **Add**.

#. Select a reviewer (workspace administrator, developer, or custom role with the review permission), enter the correct email address and phone number, and click **OK**.

   You can also add your current account as a reviewer. In this way, auto review is supported in subsequent operations. Add more reviewers, if required.

.. _dataartsstudio_01_0627__section83068019428:

Configuration Center Management
-------------------------------

DataArts Architecture configuration center provides abundant custom options. You can customize the configuration to meet your demands.

#. On the DataArts Architecture console, choose **Configuration Center** in the navigation pane on the left.

#. Click the **Functions** tab and set **Model Design Process**.


   .. figure:: /_static/images/en-us_image_0000002234237744.png
      :alt: **Figure 1** Functions

      **Figure 1** Functions

#. Click **OK**.

.. _dataartsstudio_01_0627__en-us_topic_0222298525_section21581824122814:

Designing a Subject
-------------------

This section uses the subjects listed in :ref:`Table 2 <dataartsstudio_01_0627__en-us_topic_0262779636_table356815710199>` as an example.

-  There is a subject area group named **City transportation**.
-  Under **City transportation**, there are four subject areas: **Trip records**, **Corporation**, **Time&Space**, and **Public dimensions**.
-  Under **Trip records**, there are four business objects: **Original records**, **Standard records**, **Trip facts**, and **Record statistics**.
-  Under **Corporation**, there is one business object: **Suppliers**.
-  Under **Time&Space**, there is one business object: **Time**.
-  Under **Public dimensions**, there is one business object: **Public dimensions**.

.. _dataartsstudio_01_0627__en-us_topic_0262779636_table356815710199:

.. table:: **Table 2** Subject design

   +------------------------------+------------------------------+------------------------+------------------------+---------------------------+---------------------------+
   | Subject Area Group Name (L1) | Subject Area Group Code (L1) | Subject Area Name (L2) | Subject Area Code (L2) | Business Object Name (L3) | Business Object Code (L3) |
   +==============================+==============================+========================+========================+===========================+===========================+
   | City transportation          | city_traffic                 | Trip records           | stroke_reminder        | Original records          | origin_stroke             |
   +------------------------------+------------------------------+------------------------+------------------------+---------------------------+---------------------------+
   |                              |                              |                        |                        | Standard records          | stand_stroke              |
   +------------------------------+------------------------------+------------------------+------------------------+---------------------------+---------------------------+
   |                              |                              |                        |                        | Trip facts                | stroke_fact               |
   +------------------------------+------------------------------+------------------------+------------------------+---------------------------+---------------------------+
   |                              |                              |                        |                        | Record statistics         | stroke_statistic          |
   +------------------------------+------------------------------+------------------------+------------------------+---------------------------+---------------------------+
   |                              |                              | Corporation            | people                 | Suppliers                 | vendor                    |
   +------------------------------+------------------------------+------------------------+------------------------+---------------------------+---------------------------+
   |                              |                              | Time&Space             | time_location          | Time                      | date                      |
   +------------------------------+------------------------------+------------------------+------------------------+---------------------------+---------------------------+
   |                              |                              | Public dimensions      | public_dimension       | Public dimensions         | public_dimension          |
   +------------------------------+------------------------------+------------------------+------------------------+---------------------------+---------------------------+


.. figure:: /_static/images/en-us_image_0000002269117209.png
   :alt: **Figure 2** Designing a subject

   **Figure 2** Designing a subject

**Procedure**

#. Log in to the DataArts Studio console. Locate the created DataArts Studio instance and click **Access**.

#. In the workspace list, locate the target workspace and click **DataArts Architecture**.

#. Choose **Configuration Center** in the navigation pane on the left. Click the **Subject Processes** tab, and use the default three levels.

   There can be a maximum of seven subject levels, a minimum of two subject levels, and three subject levels by default. L1 to L7 are used to represent the layers. The last level is **Business Object** and cannot be customized. The names of other levels can be customized. The levels configured in **Configuration Center** take effect on the **Subjects** page.


   .. figure:: /_static/images/en-us_image_0000002269197265.png
      :alt: **Figure 3** Configuring the subject levels

      **Figure 3** Configuring the subject levels

#. On the DataArts Architecture console, choose **Data Survey** > **Subjects** in the left navigation pane. On the page displayed, click **Create** to create an L1 subject, which is a subject area group.

   .. _dataartsstudio_01_0627__en-us_topic_0262779636_fig184368895516:

   .. figure:: /_static/images/en-us_image_0000002234077860.png
      :alt: **Figure 4** Creating an L1 subject

      **Figure 4** Creating an L1 subject

   In the dialog box displayed, set the parameters as shown in :ref:`Figure 4 <dataartsstudio_01_0627__en-us_topic_0262779636_fig184368895516>` and click **OK**.

#. Select the created subject area group and click **publish**. In the **Apply for Publication** dialog box, select a reviewer and click **OK**. Wait for the reviewer to review the application. If you have the reviewer permissions, select **Auto-review** and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269117129.png
      :alt: **Figure 5** Publishing a subject area group

      **Figure 5** Publishing a subject area group

#. Create four L2 subjects under the L1 subject **City transportation**: **Trip records**, **Corporation**, **Time&Space**, and **Public dimensions**.

   Perform the following procedure to create a subject area named **Trip records**. The procedure for creating other subject areas is similar.

   a. Right-click the L1 subject **City transportation** in the subject tree, and select **Create** from the shortcut menu. Alternatively, click **Create** in the right pane.


      .. figure:: /_static/images/en-us_image_0000002234237716.png
         :alt: **Figure 6** Creating an L2 subject

         **Figure 6** Creating an L2 subject

   b. In the dialog box displayed, set **Subject Name** and **Subject Code** to the values of **Subject Area Name** and **Subject Area Code** in :ref:`Table 2 <dataartsstudio_01_0627__en-us_topic_0262779636_table356815710199>`, set other parameters based on project requirements, and click **OK**.

   c. Select the created subject area and click **publish**. In the **Apply for Publication** dialog box, select a reviewer and click **OK**. Wait for the reviewer to review the application. If you have the reviewer permissions, select **Auto-review** and click **OK**.


      .. figure:: /_static/images/en-us_image_0000002234237880.png
         :alt: **Figure 7** Publishing a subject area

         **Figure 7** Publishing a subject area

#. Create business objects.

   -  Under **Trip records**, create four business objects: **Original records**, **Standard records**, **Trip facts**, and **Record statistics**.
   -  Under **Corporation**, create one business object: **Suppliers**.
   -  Under **Time&Space**, create one business object: **Time**.
   -  Under **Public dimensions**, create one business object: **Public dimensions**.

   Perform the following procedure to create a business object named **Original records** in the subject area **Trip records**. The procedure for creating other business objects is similar.

   a. Right-click the L2 subject **Trip records** in the subject tree, and select **Create** from the shortcut menu. Alternatively, click **Create** in the right pane.

   b. In the dialog box displayed, set **Subject Name** and **Subject Code** to the values of **Business Object Name** and **Business Object Code** in :ref:`Table 2 <dataartsstudio_01_0627__en-us_topic_0262779636_table356815710199>`, set other parameters based on project requirements, and click **OK**.

   c. Select the created business object and click **publish**. In the **Apply for Publication** dialog box, select a reviewer and click **OK**. Wait for the reviewer to review the application. If you have the reviewer permissions, select **Auto-review** and click **OK**.


      .. figure:: /_static/images/en-us_image_0000002234237792.png
         :alt: **Figure 8** Publishing a business object

         **Figure 8** Publishing a business object

.. _dataartsstudio_01_0627__section142244103311:

Creating and Publishing Lookup Tables
-------------------------------------

This section uses the lookup tables listed in :ref:`Table 3 <dataartsstudio_01_0627__en-us_topic_0262779636_table156812733610>` as an example.

.. _dataartsstudio_01_0627__en-us_topic_0262779636_table156812733610:

.. table:: **Table 3** Lookup tables

   +--------------+--------------+-----------------------+-------------------+--------------------+--------------------+--------------+-------------------+
   | Directory    | \*Table Name | \* Table English Name | Table Description | \* Field Name      | \* Field Code      | \* Data Type | Field Description |
   +==============+==============+=======================+===================+====================+====================+==============+===================+
   | payment_type | payment_type | payment_type          | None              | payment_type_id    | payment_type_id    | BIGINT       | None              |
   +--------------+--------------+-----------------------+-------------------+--------------------+--------------------+--------------+-------------------+
   |              |              |                       |                   | payment_type_value | payment_type_value | STRING       | None              |
   +--------------+--------------+-----------------------+-------------------+--------------------+--------------------+--------------+-------------------+
   | vendor       | vendor       | vendor                | None              | vendor_id          | vendor_id          | BIGINT       | None              |
   +--------------+--------------+-----------------------+-------------------+--------------------+--------------------+--------------+-------------------+
   |              |              |                       |                   | vendor_value       | vendor_value       | STRING       | None              |
   +--------------+--------------+-----------------------+-------------------+--------------------+--------------------+--------------+-------------------+
   | rate         | rate_code    | rate_code             | None              | rate_code_id       | rate_code_id       | BIGINT       | None              |
   +--------------+--------------+-----------------------+-------------------+--------------------+--------------------+--------------+-------------------+
   |              |              |                       |                   | rate_code_value    | rate_code_value    | STRING       | None              |
   +--------------+--------------+-----------------------+-------------------+--------------------+--------------------+--------------+-------------------+

**Procedure**

#. On the DataArts Architecture console, choose **Standards** > **Lookup Tables** in the navigation pane on the left.

#. Create three lookup table directories: **payment_type**, **vendor**, and **rate**.

   Perform the following procedure to create a directory named **payment_type**. The procedure for creating other directories is similar.

   a. On the **Lookup Tables** page, click |image1| above the directory tree to create a directory.


      .. figure:: /_static/images/en-us_image_0000002234077864.png
         :alt: **Figure 9** Lookup table directory tree

         **Figure 9** Lookup table directory tree

   b. In the dialog box displayed, enter a directory name, select a parent directory, and click **OK**.


      .. figure:: /_static/images/en-us_image_0000002234077872.png
         :alt: **Figure 10** Creating a directory for lookup tables

         **Figure 10** Creating a directory for lookup tables

#. Create three lookup tables: **payment_type**, **vendor**, and **rate_code**.

   Perform the following procedure to create a lookup table named **payment_type**. The procedure for creating other lookup tables is similar.

   a. .. _dataartsstudio_01_0627__en-us_topic_0262779636_li16645139502:

      On the **Lookup Tables** page, click **payment_type** in the directory tree, and click **Create** on the page displayed.


      .. figure:: /_static/images/en-us_image_0000002234078020.png
         :alt: **Figure 11** Lookup Tables page

         **Figure 11** Lookup Tables page

   b. .. _dataartsstudio_01_0627__en-us_topic_0262779636_li8669185316506:

      Set the parameters based on :ref:`Table 3 <dataartsstudio_01_0627__en-us_topic_0262779636_table156812733610>` and click **Save**.


      .. figure:: /_static/images/en-us_image_0000002234077908.png
         :alt: **Figure 12** Creating a lookup table

         **Figure 12** Creating a lookup table

   c. Refer to :ref:`3.a <dataartsstudio_01_0627__en-us_topic_0262779636_li16645139502>` to :ref:`3.b <dataartsstudio_01_0627__en-us_topic_0262779636_li8669185316506>` to create the lookup table **vendor** in the **vendor** directory and the lookup table **rate_code** in the **rate** directory.


      .. figure:: /_static/images/en-us_image_0000002234237732.png
         :alt: **Figure 13** Creating a lookup table named vendor

         **Figure 13** Creating a lookup table named vendor


      .. figure:: /_static/images/en-us_image_0000002269197313.png
         :alt: **Figure 14** Creating a lookup table named rate_code

         **Figure 14** Creating a lookup table named rate_code

#. Enter values for the three lookup tables **payment_type**, **vendor**, and **rate_code**.

   On the **Lookup Tables** page, locate the row that contains the lookup table **payment_type**, and choose **More** > **Manage Value** in the **Operation** column. On the page displayed, click **Add** to add the values listed in :ref:`Table 4 <dataartsstudio_01_0627__en-us_topic_0262779636_table16482204445819>`.

   .. _dataartsstudio_01_0627__en-us_topic_0262779636_table16482204445819:

   .. table:: **Table 4** Values to be added for the lookup table payment_type

      =============== ==================
      payment_type_id payment_type_value
      =============== ==================
      1               Credit card
      2               Cash
      3               No charge
      4               Dispute
      5               Unknown
      6               Voided trip
      =============== ==================

   Return to the **Lookup Tables** page, locate the row that contains the lookup table **vendor**, and choose **More** > **Manage Value** in the **Operation** column. On the page displayed, click **Add** to add the values listed in :ref:`Table 5 <dataartsstudio_01_0627__en-us_topic_0262779636_table139471353195913>`.

   .. _dataartsstudio_01_0627__en-us_topic_0262779636_table139471353195913:

   .. table:: **Table 5** Values to be added for the lookup table vendor

      ========= ============
      vendor_id vendor_value
      ========= ============
      1         A Company
      2         B Company
      ========= ============

   Return to the **Lookup Tables** page, locate the row that contains the lookup table **rate_code**, and choose **More** > **Manage Value** in the **Operation** column. On the page displayed, click **Add** to add the values listed in :ref:`Table 6 <dataartsstudio_01_0627__en-us_topic_0262779636_table14783193912011>`.

   .. _dataartsstudio_01_0627__en-us_topic_0262779636_table14783193912011:

   .. table:: **Table 6** Values to be added for the lookup table rate_code

      ============ =====================
      rate_code_id rate_code_value
      ============ =====================
      1            Standard rate
      2            JFK
      3            Newark
      4            Nassau or Westchester
      5            Negotiated fare
      6            Group ride
      ============ =====================

#. Return to the **Lookup Tables** page, select the three lookup tables, and click **Publish**.

#. In the **Apply for Publication** dialog box, select a reviewer and click **OK**. Wait for the reviewer to review the application. If you have the reviewer permissions, select **Auto-review** and click **OK**.

.. _dataartsstudio_01_0627__section139902116499:

Creating and Publishing Data Standards
--------------------------------------

In this example, you need to create the three data standards listed in :ref:`Table 7 <dataartsstudio_01_0627__en-us_topic_0262779636_table16465343364>`.

.. _dataartsstudio_01_0627__en-us_topic_0262779636_table16465343364:

.. table:: **Table 7** Data standards

   +--------------+-----------------+---------------------------+-----------------------+-------------+--------------+----------------------+-------------+
   | Directory    | \*Standard Name | \* Standard Code (Custom) | \*Data Type           | Data Length | Lookup Table | \*Lookup Table Field | Description |
   +==============+=================+===========================+=======================+=============+==============+======================+=============+
   | payment_type | payment_type    | payment_type              | Long integer (BIGINT) | None        | payment_type | payment_type_id      | None        |
   +--------------+-----------------+---------------------------+-----------------------+-------------+--------------+----------------------+-------------+
   | vendor       | vendor          | vendor                    | Long integer (BIGINT) | None        | vendor       | vendor_id            | None        |
   +--------------+-----------------+---------------------------+-----------------------+-------------+--------------+----------------------+-------------+
   | rate         | rate_code       | rate_code                 | Long integer (BIGINT) | None        | rate_code    | rate_code_id         | None        |
   +--------------+-----------------+---------------------------+-----------------------+-------------+--------------+----------------------+-------------+

#. On the DataArts Architecture console, choose **Standards** > **Data Standards** in the navigation pane on the left.

#. If you access the Data Standards page for the first time, you must customize a template. The custom template can be modified in Configuration Center. Additionally, select **Lookup table**, as shown in the following figure.


   .. figure:: /_static/images/en-us_image_0000002234078008.png
      :alt: **Figure 15** Customize Template

      **Figure 15** Customize Template

#. Create three directories for data standards: **payment_type**, **vendor**, and **rate_code**.

   In the upper part of the directory tree on the **Data Standards** page, click |image2|. In the dialog box displayed, enter the directory name as **payment_type**, select a parent directory, and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002234077912.png
      :alt: **Figure 16** Creating a directory for data standards

      **Figure 16** Creating a directory for data standards

#. Create three data standards: **payment_type**, **vendor**, and **rate_code**.

   a. In the directory tree on the **Data Standards** page, select the required directory and click **Create** on the page displayed on the right.
   b. On the **Create Data Standard** page, configure the three data standards by referring to the following figures, and click **Save**. In this example, only a few parameters are selected for the data standard template. You can customize a data standard template by referring to **DataArts Architecture** > **Configuration Center** > **Managing a Standard Template** in *DataArts Studio User Guide*.


   .. figure:: /_static/images/en-us_image_0000002269197117.png
      :alt: **Figure 17** Creating a data standard named payment_type

      **Figure 17** Creating a data standard named payment_type


   .. figure:: /_static/images/en-us_image_0000002234077876.png
      :alt: **Figure 18** Creating a data standard named vendor

      **Figure 18** Creating a data standard named vendor


   .. figure:: /_static/images/en-us_image_0000002234078000.png
      :alt: **Figure 19** Creating a data standard named rate_code

      **Figure 19** Creating a data standard named rate_code

#. Return to the **Data Standards** page, select the three data standards in the list, and click **Publish**.

#. In the **Apply for Publication** dialog box, select a reviewer and click **OK**. Wait for the reviewer to review the application. If you have the reviewer permissions, select **Auto-review** and click **OK**.

.. _dataartsstudio_01_0627__en-us_topic_0222298525_section945153616402:

Data Warehouse Planning: Creating Two ER Models for the SDI and DWI Layers
--------------------------------------------------------------------------

During data warehouse planning, create two models for the SDI and DWI layers, import the source table to the ER model for the SDI layer by reversing the database, and create a standard business table to record trip data for the DWI layer.

#. On the DataArts Architecture page, choose **Data Warehouse Layer** in the left navigation pane.

   In the **SDI** area, click **Create** to create an SDI model named **sdi**. In the **DWI** area, click **Create** to create a DWI model named **dwi**. Click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269117157.png
      :alt: **Figure 20** Creating an SDI model

      **Figure 20** Creating an SDI model


   .. figure:: /_static/images/en-us_image_0000002234237772.png
      :alt: **Figure 21** Creating a DWI model

      **Figure 21** Creating a DWI model

   a. Create an SDI ER model named **sdi**. In the **SDI** area, click **Create**. In the displayed **Create Model** dialog box, set the following parameters and click **OK**.


      .. figure:: /_static/images/en-us_image_0000002234077944.png
         :alt: **Figure 22** Creating a physical model named sdi

         **Figure 22** Creating a physical model named sdi

   b. Create a DWI ER model named **dwi**. In the **DWI** area, click **Create**. In the displayed **Create Model** dialog box, set the following parameters and click **OK**.


      .. figure:: /_static/images/en-us_image_0000002269117165.png
         :alt: **Figure 23** Creating a physical model named dwi

         **Figure 23** Creating a physical model named dwi

#. .. _dataartsstudio_01_0627__en-us_topic_0262779636_en-us_topic_0222298525_li167674202477:

   On the **Data Warehouse Layer** page, click the newly created SDI model to go to the **ER Modeling** page. Choose **City transportation** > **Trip records** > **Original records**, and click **Reverse Database** on the page displayed on the right to import the source table.

   .. note::

      Before reversing a database, ensure that you have collected the data assets of the database.


   .. figure:: /_static/images/en-us_image_0000002269117169.png
      :alt: **Figure 24** Model directory

      **Figure 24** Model directory

   In the **Reverse Database** dialog box, set the parameters and click **Yes**. In this example, select the source table in the SDI layer database **demo_sdi_db**.


   .. figure:: /_static/images/en-us_image_0000002234237684.png
      :alt: **Figure 25** Reversing a database

      **Figure 25** Reversing a database

   After the database is reversed, click **Close**. The table is in the draft state. Click **Publish** in the **Operation** column, and you can view the imported and published table.


   .. figure:: /_static/images/en-us_image_0000002234237708.png
      :alt: **Figure 26** Viewing a table

      **Figure 26** Viewing a table

#. Create a standard business table to record trip data.

   a. On the **Data Warehouse Layer** area, click the newly created DWI model to go to the **ER Modeling** page. Expand subjects, choose **City transportation** > **Trip records** > **Standard records**, and click **Create** on the page displayed on the right.

   b. On the **Basic Settings** tab page, set the parameters as shown in the figure below.

      .. table:: **Table 8** Standard trip data table

         +------------------+--------------------+-----------------------+------------------------+-------------+---------------+
         | \*Subject        | \*Table Name       | \* Table English Name | \*Data Connection Name | Database    | \*Description |
         +==================+====================+=======================+========================+=============+===============+
         | Standard records | dwi_taxi_trip_data | dwi_taxi_trip_data    | mrs_hive_link          | demo_dwi_db | None          |
         +------------------+--------------------+-----------------------+------------------------+-------------+---------------+


      .. figure:: /_static/images/en-us_image_0000002234077968.png
         :alt: **Figure 27** Basic settings of the table named dwi_taxi_trip_data

         **Figure 27** Basic settings of the table named dwi_taxi_trip_data

   c. Click **Next** to go to the **Table Fields** page. Click **Add**. Add the fields listed in :ref:`Table 9 <dataartsstudio_01_0627__en-us_topic_0262779636_table929218193298>`. Then click |image3| in the **Data Standard** column of the rows where the vendor ID, rate code ID, and payment type reside to associate with the **Vendor**, **Rate Code ID**, and **Payment Type** standards, respectively. :ref:`Figure 28 <dataartsstudio_01_0627__en-us_topic_0262779636_en-us_topic_0222298525_fig1948138204112>` shows the configuration after the fields are added.

      .. _dataartsstudio_01_0627__en-us_topic_0262779636_table929218193298:

      .. table:: **Table 9** Fields to be added to the table named dwi_table_trip_data

         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | No. | Field Name            | Field Code            | Data Type      | Data Standard | Primary Key  | Partition    | Not Null | Tag   |
         +=====+=======================+=======================+================+===============+==============+==============+==========+=======+
         | 1   | vendor_id             | vendor_id             | BIGINT         | vendor        | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 2   | tpep_pickup_datetime  | tpep_pickup_datetime  | TIMESTAMP      | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 3   | tpep_dropoff_datetime | tpep_dropoff_datetime | TIMESTAMP      | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 4   | passenger_count       | passenger_count       | STRING         | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 5   | trip_distance         | trip_distance         | DECIMAL (10,2) | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 6   | rate_code_id          | rate_code_id          | BIGINT         | rate_code     | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 7   | store_fwd_flag        | store_fwd_flag        | STRING         | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 8   | pu_location_id        | pu_location_id        | STRING         | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 9   | do_location_id        | do_location_id        | STRING         | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 10  | payment_type          | payment_type          | BIGINT         | payment_type  | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 11  | fare_amount           | fare_amount           | DECIMAL (10,2) | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 12  | extra                 | extra                 | DECIMAL (10,2) | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 13  | mta_tax               | mta_tax               | DECIMAL (10,2) | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 14  | tip_amount            | tip_amount            | DECIMAL (10,2) | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 15  | tolls_amount          | tolls_amount          | DECIMAL (10,2) | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 16  | improvement_surcharge | improvement_surcharge | DECIMAL (10,2) | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+
         | 17  | total_amount          | total_amount          | DECIMAL (10,2) | ``-``         | Not selected | Not selected | Selected | ``-`` |
         +-----+-----------------------+-----------------------+----------------+---------------+--------------+--------------+----------+-------+

      .. _dataartsstudio_01_0627__en-us_topic_0262779636_en-us_topic_0222298525_fig1948138204112:

      .. figure:: /_static/images/en-us_image_0000002234237796.png
         :alt: **Figure 28** Fields to be added to the table named dwi_table_trip_data

         **Figure 28** Fields to be added to the table named dwi_table_trip_data

      You can perform the following operations on the fields.

      -  **Associating with data standards**

         When creating or editing a table, click the **Table Fields** tab. In the **Data Standard** column of the row where the field is located, click |image4| to select a data standard to be associated with the field. After a field is associated with a data standard, a quality job is automatically generated after the table is published. A quality rule is generated for each field associated with the data standard. You can monitor the quality of fields based on the data standard. You can view the quality job on the **Quality Jobs** page of DataArts Quality. For more information about associating data standards, see **DataArts Architecture** > **ER Modeling** > **Designing Physical Models** in *DataArts Studio User Guide*.

      -  **Adding a tag**

         A tag is a custom identifier. After adding a tag, you can search for data assets in the DataArts Studio DataArts Catalog module with ease.

         When creating or editing a table, click the **Table Fields** tab. In the **Tag** column of the row where the field is located, click |image5| to select a tag. In the dialog box displayed, enter a new tag name and press **Enter**. Alternatively, select an existing tag from the drop-down list. Then click **OK**.

      -  **Associating with quality rules**

         After a table is created, you can associate fields in the table with quality rules. After the association, a quality job is automatically created in the DataArts Quality module after the table is published. If the table has been published, the system automatically updates the quality job. For more information about associating quality rules, see **DataArts Architecture** > **ER Modeling** > **Associating with Quality Rules** in *DataArts Studio User Guide*.

   d. Click **Next** to go to the **Relationships** page. In this example, you do not need to perform any operation on this page.

   e. Click **Next** to go to the **Mappings** page and create mappings to design data sources of the table.

      -  If the table fields come from different ER models, you must create multiple mappings. In each mapping, you only need to set the source field for the field that comes from the current mapping.
      -  If the table fields come from multiple tables in the same ER model, you can create a mapping. In the **Table** field of the mapping, you can join multiple tables and then set source fields for the fields in the table.

      In this example, you only need to create one mapping. Click **Create** and set a mapping as shown in :ref:`Figure 29 <dataartsstudio_01_0627__en-us_topic_0262779636_en-us_topic_0222298525_fig2672153020255>`.

      -  **Mapping** is automatically generated. You can customize the name.

      -  Select **sdi** for **Model**.

      -  Select the source table **sdi_taxi_trip_data** for **Table**. All data in the **dwi_taxi_trip_data** table comes from this source table.

         .. _dataartsstudio_01_0627__en-us_topic_0262779636_en-us_topic_0222298525_fig2672153020255:

         .. figure:: /_static/images/en-us_image_0000002269117265.png
            :alt: **Figure 29** Creating a mapping

            **Figure 29** Creating a mapping

      -  **Field Mapping**

         In the **Field Mapping** area, set source fields for the fields in the table in sequence. The selected source fields must have the same meaning as the fields in the table. As shown in :ref:`Figure 30 <dataartsstudio_01_0627__en-us_topic_0262779636_en-us_topic_0222298525_fig1344103811414>`, an SQL statement is displayed at the bottom of **Field Mapping** for reference.

         .. note::

            -  On the **DataArts Architecture** page, choose **Metrics** > **Configuration Center** in the navigation pane on the left, and click the **Functions** tab. On the **Functions** page, if **Create data development jobs** is selected (unselected by default) for **Model Design Process**, the system can create an ETL job during data development based on the table mapping information during table release. An ETL node is generated for each mapping, and the job name starts with *Database name_Table code*. Currently, this function is in the internal test stage. Only DLI-to-DLI and DLI-to-DWS mapping jobs can be created.

               You can choose **DataArts Factory** > **Job Development** to view the created ETL jobs. By default, ETL jobs are scheduled at 00:00 every day.

            -  In this example, the function of automatically creating ETL jobs is not enabled. The function provides only the data flow direction for data development. During data development, you can refer to the mapping to write SQL scripts.

         .. _dataartsstudio_01_0627__en-us_topic_0262779636_en-us_topic_0222298525_fig1344103811414:

         .. figure:: /_static/images/en-us_image_0000002234237760.png
            :alt: **Figure 30** Mapping fields

            **Figure 30** Mapping fields

   f. After the mappings are configured, click **Save**.

#. Select the created model and choose **More** > **Export**. In the dialog box displayed, select **Table** for **Export** and click **OK**. Export the **sdi** model in the same way. You can use the exported model as a backup and import it.


   .. figure:: /_static/images/en-us_image_0000002234237828.png
      :alt: **Figure 31** Export dialog box

      **Figure 31** Export dialog box

#. Publish the table model.

   a. Publish the source table imported to the SDI ER model in :ref:`2 <dataartsstudio_01_0627__en-us_topic_0262779636_en-us_topic_0222298525_li167674202477>`. After the table is published, you can use DataArts Studio to manage and monitor the source table.

      Return to the **ER Modeling** page, select the **sdi** model in the model directory. Select the **sdi_taxi_trip_data** table in the list on the right, and click **Publish**. In the dialog box displayed, select a reviewer and click **OK**. Wait for the reviewer to review the application. If you have the reviewer permissions, select **Auto-review** and click **OK**.

   b. Publish a table of the DWI ER model.

      Return to the **ER** **Modeling** page, select the **dwi** model in the model directory. Select the **dwi_table_trip_data** table in the list on the right, and click **Publish**. In the dialog box displayed, select a reviewer and click **OK**. Wait for the reviewer to review the application. If you have the reviewer permissions, select **Auto-review** and click **OK**.

#. After the application is approved, you can view **Status** and **Sync Status** of the corresponding model on the **ER Modeling** page.

   Publication is an asynchronous operation. You can click |image6| to refresh the status. After an application for publishing a table is approved, the system performs operations such as creating tables and synchronizing technical assets and logical assets based on the configurations of **Model Design Process** on the **Functions** tab page in **Configuration Center**. The synchronization status is displayed in the **Sync Status** column of the table.

   -  If all items in **Sync Status** are displayed as **Succeeded**, the table is published. Move your mouse pointer to |image7| in **Sync Status**. If **Creation succeeded** is displayed, the table is created in the corresponding data source.

   -  If an item in **Sync Status** is displayed as **Failed**, you can refresh the status. If the fault persists, choose **More** > **View History** to view logs.

      Locate the failure cause based on the logs. After the fault is rectified, return to the **ER Modeling** page, select the table to be synchronized in the list, choose **More** > **Synchronize** and click **OK** in the dialog box displayed. If the synchronization fails again, contact technical support for assistance.


   .. figure:: /_static/images/en-us_image_0000002269117057.png
      :alt: **Figure 32** Checking the table status

      **Figure 32** Checking the table status

   Click a table name in the list to view the table details. **Data Source** shows the table location.


   .. figure:: /_static/images/en-us_image_0000002234077880.png
      :alt: **Figure 33** Table details

      **Figure 33** Table details

.. _dataartsstudio_01_0627__section265510426117:

Creating and Publishing Dimensions for the DWR Layer
----------------------------------------------------

During dimension modeling, create three lookup table dimensions (**vendor**, **rate_code**, and **payment_type**) and one hierarchy dimension (**date**) for the DWR layer.

#. On the DataArts Architecture console, choose **Models** > **Dimensional Modeling** in the navigation pane on the left.

#. Create the three lookup table dimensions listed in :ref:`Table 10 <dataartsstudio_01_0627__en-us_topic_0262779636_table1988313451106>`.

   .. _dataartsstudio_01_0627__en-us_topic_0262779636_table1988313451106:

   .. table:: **Table 10** Lookup table dimensions

      +------------------+------------------+-------------------+--------------+---------+-------------+------------------------+------------------------+-------------+--------------+
      | \*Subject        | \*Dimension Name | \* Dimension Code | \*Type       | \*Owner | Description | \*Data Connection Type | \*Data Connection Name | \*Database  | Lookup Table |
      +==================+==================+===================+==============+=========+=============+========================+========================+=============+==============+
      | vendor           | dim_vendor       | dim_vendor        | Lookup table | ``-``   | None        | MRS_HIVE               | mrs_hive_link          | demo_dwr_db | vendor       |
      +------------------+------------------+-------------------+--------------+---------+-------------+------------------------+------------------------+-------------+--------------+
      | public_dimension | dim_rate_code    | dim_rate_code     | Lookup table | ``-``   | None        | MRS_HIVE               | mrs_hive_link          | demo_dwr_db | rate         |
      +------------------+------------------+-------------------+--------------+---------+-------------+------------------------+------------------------+-------------+--------------+
      | public_dimension | dim_payment_type | dim_payment_type  | Lookup table | ``-``   | None        | MRS_HIVE               | mrs_hive_link          | demo_dwr_db | payment_type |
      +------------------+------------------+-------------------+--------------+---------+-------------+------------------------+------------------------+-------------+--------------+

   a. Click the **Dimensions** tab, choose **City transportation** > **Corporation** > **Suppliers** in the subject tree, and click **Create** to create a dimension named **dim_vendor**.


      .. figure:: /_static/images/en-us_image_0000002234077928.png
         :alt: **Figure 34** Dimensional modeling

         **Figure 34** Dimensional modeling

   b. On the **Create Dimension** page, set the parameters as shown in the figure below and click **Save**.


      .. figure:: /_static/images/en-us_image_0000002269117049.png
         :alt: **Figure 35** Creating a dimension named dim_vendor

         **Figure 35** Creating a dimension named dim_vendor

   c. Click the **Dimensions** tab, choose **City transportation** > **Public dimensions** > **Public dimensions** in the subject tree, and click **Create** to create a dimension named **dim_rate_code**. On the **Create Dimension** page, set the parameters as shown in the figure below and click **Save**.


      .. figure:: /_static/images/en-us_image_0000002269197325.png
         :alt: **Figure 36** Creating a dimension named dim_rate_code

         **Figure 36** Creating a dimension named dim_rate_code

   d. Click the **Dimensions** tab, choose **City transportation** > **Public dimensions** > **Public dimensions** in the subject tree, and click **Create** to create a dimension named **dim_payment_type**. On the **Create Dimension** page, set the parameters as shown in the figure below and click **Save**.


      .. figure:: /_static/images/en-us_image_0000002269117085.png
         :alt: **Figure 37** Creating a dimension named dim_payment_type

         **Figure 37** Creating a dimension named dim_payment_type

#. Create a hierarchy dimension named **dim_date**.

   a. On the **Dimensional Modeling** tab page, choose **City transportation** > **Time&Space** > **Time** in the subject tree. Then click **Create** on the **Dimensions** tab page to create a dimension named **dim_date**.

   b. Configure the basic settings and physicalization settings as shown in the figure below.

      .. table:: **Table 11** Date dimension

         +-----------+------------------+---------------------------+-----------+---------+-------------+------------------------+------------------------+-------------+
         | \*Subject | \*Dimension Name | \* Dimension English Name | \*Type    | \*Owner | Description | \*Data Connection Type | \*Data Connection Name | \*Database  |
         +===========+==================+===========================+===========+=========+=============+========================+========================+=============+
         | date      | dim_date         | dim_date                  | Hierarchy | ``-``   | None        | MRS_HIVE               | mrs_hive_link          | demo_dwr_db |
         +-----------+------------------+---------------------------+-----------+---------+-------------+------------------------+------------------------+-------------+


      .. figure:: /_static/images/en-us_image_0000002234237688.png
         :alt: **Figure 38** Date dimension

         **Figure 38** Date dimension

   c. In the **Field Settings** area, add fields as described in the table below.

      .. table:: **Table 12** Field settings

         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | No. | Field Name   | Field Code   | Data Standard | Data Type | Surrogate Key | Primary Key  | Partition    | Not Null     |
         +=====+==============+==============+===============+===========+===============+==============+==============+==============+
         | 1   | dim_date_key | dim_date_key | ``-``         | TIMESTAMP | Selected      | Selected     | Not selected | Selected     |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 2   | real_time    | real_time    | ``-``         | TIMESTAMP | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 3   | minute_id    | minute_id    | ``-``         | BIGINT    | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 4   | minute       | minute       | ``-``         | BIGINT    | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 5   | hour_id      | hour_id      | ``-``         | BIGINT    | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 6   | hour         | hour         | ``-``         | BIGINT    | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 7   | day_id       | day_id       | ``-``         | BIGINT    | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 8   | day          | day          | ``-``         | STRING    | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 9   | month_id     | month_id     | ``-``         | BIGINT    | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 10  | month        | month        | ``-``         | STRING    | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 11  | year_id      | year_id      | ``-``         | BIGINT    | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+
         | 12  | year         | year         | ``-``         | BIGINT    | Not selected  | Not selected | Not selected | Not selected |
         +-----+--------------+--------------+---------------+-----------+---------------+--------------+--------------+--------------+


      .. figure:: /_static/images/en-us_image_0000002269197193.png
         :alt: **Figure 39** Field settings

         **Figure 39** Field settings

   d. In the **Hierarchy Settings** area, click **Add** to create two layers as shown in the figures below.


      .. figure:: /_static/images/en-us_image_0000002234237812.png
         :alt: **Figure 40** Layer 1

         **Figure 40** Layer 1


      .. figure:: /_static/images/en-us_image_0000002234077980.png
         :alt: **Figure 41** Layer 2

         **Figure 41** Layer 2

   e. Click **Save**.

#. Return to the **Dimensions** tab page, select the four new dimensions in the dimension list, and click **Publish**.

#. In the **Apply for Publication** dialog box, select a reviewer and click **OK**. Wait for the reviewer to review the application. If you have the reviewer permissions, select **Auto-review** and click **OK**.

#. After a dimension is published and approved, the system automatically creates a dimension table for the dimension. The name and code of the dimension table are the same as those of the dimension. On the **Dimensional Modeling** page, click the **Dimension Tables** tab to view the created dimension table.

   In the dimension table list, you can view **Sync Status** of the dimension tables.

   -  If all items in **Sync Status** are displayed as **Succeeded**, the dimension is published and the dimension table is created in the database.
   -  If an item in **Sync Status** is displayed as **Failed**, click **View History** in the row. On the page displayed, click the **History** tab to view logs. Troubleshoot the fault based on the logs. After the fault is rectified, select the dimension table, click **Synchronize** above the dimension table list, and click **OK** in the dialog box displayed. If the fault persists, contact technical support for assistance.


   .. figure:: /_static/images/en-us_image_0000002269197157.png
      :alt: **Figure 42** Sync Status of the dimension tables

      **Figure 42** Sync Status of the dimension tables

.. _dataartsstudio_01_0627__section665784223319:

Creating and Publishing a Fact Table for the DWR Layer
------------------------------------------------------

During dimensional modeling, create a fact table named **stroke_order** for the DWR layer.

#. On the DataArts Architecture console, choose **Models** > **Dimensional Modeling** in the navigation pane on the left.

#. Click the **Fact Tables** tab, choose **City transportation** > **Trip records** > **Trip facts** in the subject tree, and click **Create** to create a fact table named **stroke_order**.

   In the **Basic Settings** area on the **Create Fact Table** page, set the following parameters:

   -  **Subject**: **Subject Area Group: City transportation > Subject Area: Trip records > Business Object: Trip facts**
   -  **Table Name**: **stroke_order**
   -  **Table English Name**: **fact_stroke_order**
   -  **Data Connection Type**: **MRS_HIVE**
   -  **Data Connection Name**: **mrs_hive_link**
   -  **Database**: **demo_dwr_db**
   -  **Table Type**: **HIVE_TABLE**
   -  **Owner**: an owner in the drop-down list box
   -  **Description**: None

   In the **Field Settings** area, choose **Create** > **Dimension**. In the dialog box displayed, select the dimensions **rate_code**, **vendor**, **payment_type**, and **date**, and click **OK**. Choose **Create** > **Dimension**. In the dialog box displayed, select the dimension **date** and click **OK**. In the dimension field list, adjust the sequence of the dimension fields and modify the information about the two **date** dimensions, as listed in :ref:`Table 13 <dataartsstudio_01_0627__en-us_topic_0262779636_table16541810165218>`.

   .. _dataartsstudio_01_0627__en-us_topic_0262779636_table16541810165218:

   .. table:: **Table 13** Dimension fields

      +-----+-----------------------+----------------------+-----------+--------------+--------------+--------------+---------------------+----------------------+-------------+----------------------+
      | No. | Field Name            | Field Code           | Data Type | Primary Key  | Partition    | Not Null     | Associated Standard | Associated Dimension | Role        | Description          |
      +=====+=======================+======================+===========+==============+==============+==============+=====================+======================+=============+======================+
      | 1   | rate_code_id          | rate_code_id         | BIGINT    | Not selected | Not selected | Not selected | ``-``               | rate_code            | dim\_       | ``-``                |
      +-----+-----------------------+----------------------+-----------+--------------+--------------+--------------+---------------------+----------------------+-------------+----------------------+
      | 2   | vendor_id             | vendor_id            | BIGINT    | Not selected | Not selected | Not selected | ``-``               | vendor               | dim\_       | ``-``                |
      +-----+-----------------------+----------------------+-----------+--------------+--------------+--------------+---------------------+----------------------+-------------+----------------------+
      | 3   | payment_type_id       | payment_type_id      | BIGINT    | Not selected | Not selected | Not selected | ``-``               | payment_type         | dim\_       | ``-``                |
      +-----+-----------------------+----------------------+-----------+--------------+--------------+--------------+---------------------+----------------------+-------------+----------------------+
      | 4   | pickup_date_key       | dim_pickup_date_key  | TIMESTAMP | Not selected | Not selected | Not selected | ``-``               | Date                 | dim_pickup  | Date dimension table |
      +-----+-----------------------+----------------------+-----------+--------------+--------------+--------------+---------------------+----------------------+-------------+----------------------+
      | 5   | tpep_dropoff_datetime | dim_dropoff_date_key | TIMESTAMP | Not selected | Not selected | Not selected | ``-``               | Date                 | dim_dropoff | Date dimension table |
      +-----+-----------------------+----------------------+-----------+--------------+--------------+--------------+---------------------+----------------------+-------------+----------------------+

   In the **Field Settings** area, choose **Create** > **Measure** and create the fields listed in :ref:`Table 14 <dataartsstudio_01_0627__en-us_topic_0262779636_table751725421110>` in sequence.

   .. _dataartsstudio_01_0627__en-us_topic_0262779636_table751725421110:

   .. table:: **Table 14** Measure fields

      +-----+-----------------------+-----------------------+----------------+--------------+--------------+--------------+---------------------+
      | No. | Field Name            | Field Code            | Data Type      | Primary Key  | Partition    | Not Null     | Associated Standard |
      +=====+=======================+=======================+================+==============+==============+==============+=====================+
      | 6   | pu_location_id        | pu_location_id        | STRING         | Not selected | Not selected | Not selected | ``-``               |
      +-----+-----------------------+-----------------------+----------------+--------------+--------------+--------------+---------------------+
      | 7   | do_location_id        | do_location_id        | STRING         | Not selected | Not selected | Not selected | ``-``               |
      +-----+-----------------------+-----------------------+----------------+--------------+--------------+--------------+---------------------+
      | 8   | fare_amount           | fare_amount           | DECIMAL (10,2) | Not selected | Not selected | Not selected | ``-``               |
      +-----+-----------------------+-----------------------+----------------+--------------+--------------+--------------+---------------------+
      | 9   | extra                 | extra                 | DECIMAL (10,2) | Not selected | Not selected | Not selected | ``-``               |
      +-----+-----------------------+-----------------------+----------------+--------------+--------------+--------------+---------------------+
      | 10  | mta_tax               | mta_tax               | DECIMAL (10,2) | Not selected | Not selected | Not selected | ``-``               |
      +-----+-----------------------+-----------------------+----------------+--------------+--------------+--------------+---------------------+
      | 11  | tip_amount            | tip_amount            | DECIMAL (10,2) | Not selected | Not selected | Not selected | ``-``               |
      +-----+-----------------------+-----------------------+----------------+--------------+--------------+--------------+---------------------+
      | 12  | tolls_amount          | tolls_amount          | DECIMAL (10,2) | Not selected | Not selected | Not selected | ``-``               |
      +-----+-----------------------+-----------------------+----------------+--------------+--------------+--------------+---------------------+
      | 13  | improvement_surcharge | improvement_surcharge | DECIMAL (10,2) | Not selected | Not selected | Not selected | ``-``               |
      +-----+-----------------------+-----------------------+----------------+--------------+--------------+--------------+---------------------+
      | 14  | total_amount          | total_amount          | DECIMAL (10,2) | Not selected | Not selected | Not selected | ``-``               |
      +-----+-----------------------+-----------------------+----------------+--------------+--------------+--------------+---------------------+


   .. figure:: /_static/images/en-us_image_0000002234078024.png
      :alt: **Figure 43** Fact table fields

      **Figure 43** Fact table fields

#. After the configuration, click **Publish**.

#. In the dialog box displayed, select a reviewer and click **OK**. Wait for the reviewer to review the application. If you have the reviewer permissions, select **Auto-review** and click **OK**.

#. Return to the **Fact Tables** tab page, find the new fact table in the list, and view **Sync Status**.

   -  If all items in **Sync Status** are displayed as **Succeeded**, the fact table is published and created in the database.
   -  If an item in **Sync Status** is displayed as **Failed**, choose **More** > **View History**. On the page displayed, click the **History** tab to view logs. Troubleshoot the fault based on the logs. After the fault is rectified, choose **More** > **Synchronize** above the fact table list, and click **OK** in the dialog box displayed. If the fault persists, contact technical support for assistance.

.. _dataartsstudio_01_0627__section1222433193512:

Creating and Publishing Technical Metrics
-----------------------------------------

In this example, you need to create the technical metrics listed in :ref:`Table 15 <dataartsstudio_01_0627__en-us_topic_0262779636_table19618548718>` and :ref:`Table 16 <dataartsstudio_01_0627__en-us_topic_0262779636_table56617262116>`.

.. _dataartsstudio_01_0627__en-us_topic_0262779636_table19618548718:

.. table:: **Table 15** Atomic metrics

   +------------------+------------------+-----------------+-------------+--------------------+-------------+
   | \*Metric Name    | \* Metric Code   | Data Table      | \*Subject   | \*Expression       | Description |
   +==================+==================+=================+=============+====================+=============+
   | sum_total_amount | sum_total_amount | Itinerary order | stroke_fact | sum (total amount) | None        |
   +------------------+------------------+-----------------+-------------+--------------------+-------------+

.. _dataartsstudio_01_0627__en-us_topic_0262779636_table56617262116:

.. table:: **Table 16** Derivative metrics

   +---------------------------------------------------------+-----------------+------------------+-----------------+------------------------------------------------------+-------------+----------------+
   | Metric                                                  | \*Data Table    | \*Subject        | \*Atomic Metric | Statistical Dimension                                | Time Filter | General Filter |
   +=========================================================+=================+==================+=================+======================================================+=============+================+
   | total_amount_(payment_type)                             | Itinerary order | stroke_statistic | total_amount    | payment_type                                         | None        | None           |
   +---------------------------------------------------------+-----------------+------------------+-----------------+------------------------------------------------------+-------------+----------------+
   | total_amount_(rate_code)                                | Itinerary order | stroke_statistic | total_amount    | rate_code                                            | None        | None           |
   +---------------------------------------------------------+-----------------+------------------+-----------------+------------------------------------------------------+-------------+----------------+
   | total_amount_(vendor,stroke_order.dim_dropoff_date_key) | Itinerary order | stroke_statistic | total_amount    | **vendor** and **stroke_order.dim_dropoff_date_key** | None        | None           |
   +---------------------------------------------------------+-----------------+------------------+-----------------+------------------------------------------------------+-------------+----------------+

#. On the DataArts Architecture console, choose **Metrics** > **Technical Metrics** in the navigation pane on the left.
#. Create an atomic metric named **total_amount** to collect statistics on fares.

   a. Click the **Atomic Metrics** tab and click **Create**.

   b. On the **Create Atomic Metric** page, set the parameters as shown in the figure below and click **Publish**.


      .. figure:: /_static/images/en-us_image_0000002269197181.png
         :alt: **Figure 44** Creating an atomic metric

         **Figure 44** Creating an atomic metric

   c. Wait for the reviewer to review the application. After the application is approved, the atomic metric will be created.

#. Create three derivative metrics.

   -  Create **total_amount_(payment_type)** to collect statistics on the total fares based on **payment_type**.

      On the **Technical Metrics** page, click the **Derivative Metrics** tab and click **Create**. On the **Create Derivative Metric** page, set the parameters as shown in the figure below. After the configuration is complete, click **Trial Run**. In the dialog box displayed, click **Execute**. If the trial running is successful, click **Save**.


      .. figure:: /_static/images/en-us_image_0000002269117077.png
         :alt: **Figure 45** Creating a derivative metric named total_amount_(payment_type)

         **Figure 45** Creating a derivative metric named total_amount_(payment_type)

   -  Create **total_amount_(rate_code)** to collect statistics on the total fares based on **rate_code**.

      On the **Technical Metrics** page, click the **Derivative Metrics** tab and click **Create**. On the **Create Derivative Metric** page, set the parameters as shown in the figure below. After the configuration is complete, click **Trial Run**. In the dialog box displayed, click **Execute**. If the trial running is successful, click **Save**.


      .. figure:: /_static/images/en-us_image_0000002234237888.png
         :alt: **Figure 46** Creating a derivative metric named total_amount_(rate_code)

         **Figure 46** Creating a derivative metric named total_amount_(rate_code)

   -  Create **total_amount_(vendor,stroke_order.dim_dropoff_date_key)** to collect statistics on the total fares based on **vendor**.

      On the **Technical Metrics** page, click the **Derivative Metrics** tab and click **Create**. On the **Create Derivative Metric** page, set the parameters as shown in the figure below. After the configuration is complete, click **Trial Run**. In the dialog box displayed, click **Execute**. If the trial running is successful, click **Save**.


      .. figure:: /_static/images/en-us_image_0000002269117229.png
         :alt: **Figure 47** Creating a derivative metric named total_amount_(vendor,stroke_order.dim_dropoff_date_key)

         **Figure 47** Creating a derivative metric named total_amount_(vendor,stroke_order.dim_dropoff_date_key)

#. Return to the **Derivative Metrics** tab page, select the three derivative metrics and click **Publish**. In the dialog box displayed, select a reviewer and click **OK**. Wait for the reviewer to review the application. If you have the reviewer permissions, select **Auto-review** and click **OK**.

.. _dataartsstudio_01_0627__section829585916339:

Data Mart: Creating and Publishing Summary Tables for the DM Layer
------------------------------------------------------------------

Create the three summary tables listed in :ref:`Table 17 <dataartsstudio_01_0627__en-us_topic_0262779636_table219762715358>` for the DM layer.

.. _dataartsstudio_01_0627__en-us_topic_0262779636_table219762715358:

.. table:: **Table 17** Summary tables

   +-------------------+------------------+-----------------------+------------------------------------------------------+----------------------+------------------------+------------+-------+-------------+
   | \*Subject         | \*Table Name     | \* Table English Name | Statistical Dimension                                | Data Connection Type | \*Data Connection Name | \*Database | Owner | Description |
   +===================+==================+=======================+======================================================+======================+========================+============+=======+=============+
   | stroke_statistic  | dws_payment_type | dws_payment_type      | payment_type                                         | MRS_HIVE             | mrs_hive_link          | demo_dm_db | ``-`` | None        |
   +-------------------+------------------+-----------------------+------------------------------------------------------+----------------------+------------------------+------------+-------+-------------+
   | stroke_statistic  | dws_rate_code    | dws_rate_code         | rate_code                                            | MRS_HIVE             | mrs_hive_link          | demo_dm_db | ``-`` | None        |
   +-------------------+------------------+-----------------------+------------------------------------------------------+----------------------+------------------------+------------+-------+-------------+
   | stroke_statistics | dws_vendor       | dws_vendor            | **vendor** and **stroke_order.dim_dropoff_date_key** | MRS_HIVE             | mrs_hive_link          | demo_dm_db | ``-`` | None        |
   +-------------------+------------------+-----------------------+------------------------------------------------------+----------------------+------------------------+------------+-------+-------------+

#. On the DataArts Architecture console, choose **Data Mart** in the navigation pane on the left.
#. Click the **Summary Tables** tab.
#. Create three summary tables: **payment_type**, **rate_code**, and **vendor**.

   a. On the **Summary Tables** page, choose **City transportation** > **Trip records** > **Record statistics** in the directory tree, and click **Create** to create a summary table named **dws_payment_type**. On the **Create Summary Table** page, set the parameters and click **Save**.

      Set the basic settings as shown in the figure below.


      .. figure:: /_static/images/en-us_image_0000002269117197.png
         :alt: **Figure 48** Creating a summary table named dws_payment_type

         **Figure 48** Creating a summary table named dws_payment_type

      On the **Field Settings** tab page, click **Add**, enter the time field name, and select the data type.


      .. figure:: /_static/images/en-us_image_0000002269197153.png
         :alt: **Figure 49** Field settings

         **Figure 49** Field settings

      On the **Field Settings** tab page, click **Add** to add the derivative metric **total_amount_(payment_mode)**. Set associated objects and select corresponding metrics. You can add only published derivative or compound metrics that are associated with the specified statistical dimension.


      .. figure:: /_static/images/en-us_image_0000002234237912.png
         :alt: **Figure 50** Field settings

         **Figure 50** Field settings

      Click **Save**.

   b. On the **Summary Tables** page, choose **City transportation** > **Trip records** > **Record statistics** in the directory tree, and click **Create** to create a summary table named **dws_rate_code**. On the **Create Summary Table** page, set the parameters and click **Save**.


      .. figure:: /_static/images/en-us_image_0000002269117061.png
         :alt: **Figure 51** Creating a summary table named dws_rate_code (Basic Settings)

         **Figure 51** Creating a summary table named dws_rate_code (Basic Settings)


      .. figure:: /_static/images/en-us_image_0000002234077992.png
         :alt: **Figure 52** Creating a summary table named dws_rate_code (Field Settings)

         **Figure 52** Creating a summary table named dws_rate_code (Field Settings)

   c. On the **Summary Tables** page, choose **City transportation** > **Trip records** > **Record statistics** in the directory tree, and click **Create** to create a summary table named **dws_vendor**. On the **Create Summary Table** page, set the parameters and click **Save**.


      .. figure:: /_static/images/en-us_image_0000002234077852.png
         :alt: **Figure 53** Creating a summary table named dws_vendor (Basic Settings)

         **Figure 53** Creating a summary table named dws_vendor (Basic Settings)


      .. figure:: /_static/images/en-us_image_0000002269117141.png
         :alt: **Figure 54** Creating a summary table named dws_vendor (Field Settings)

         **Figure 54** Creating a summary table named dws_vendor (Field Settings)

#. Return to the **Summary Tables** tab page, select the three new summary tables, and click **Publish**.
#. In the dialog box displayed, select a reviewer and click **OK**. After the reviewer approves the publishing application, the summary table is automatically created. If you have the reviewer permissions, select **Auto-review** and click **OK**.
#. Return to the **Summary Tables** tab page, find the new summary tables in the list, and view **Sync Status**.

   -  If all items in **Sync Status** are displayed as **Succeeded**, the summary tables are published and created in the database.
   -  If an item in **Sync Status** is displayed as **Failed**, choose **More** > **View History** in the row. On the page displayed, click the **History** tab to view logs. Troubleshoot the fault based on the logs. After the fault is rectified, choose **More** > **Synchronize** above the summary table list, and click **OK** in the dialog box displayed. If the fault persists, contact technical support for assistance.

.. |image1| image:: /_static/images/en-us_image_0000002234237876.png
.. |image2| image:: /_static/images/en-us_image_0000002234077996.png
.. |image3| image:: /_static/images/en-us_image_0000002269117153.png
.. |image4| image:: /_static/images/en-us_image_0000002234237776.png
.. |image5| image:: /_static/images/en-us_image_0000002269117149.png
.. |image6| image:: /_static/images/en-us_image_0000002269197201.png
.. |image7| image:: /_static/images/en-us_image_0000002269197333.png
