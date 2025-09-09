:original_name: dataartsstudio_01_0145.html

.. _dataartsstudio_01_0145:

Creating a DataArts Migration Resource Group Incremental Package
================================================================

This type of incremental package provides resource groups for real-time jobs in DataArts Migration. DataArts Migration resource groups can be used to migrate data to the cloud and ingest data into and export data out of a data lake. It provides wizard-based configuration and management and can migrate all and incremental data from a single table, entire database, or database or table shard.

DataArts Migration resource groups can be used in the following scenarios:

They can be used to create and run real-time processing migration jobs to migrate data to the cloud or ingest data into the data lake.

By default, a DataArts Studio instance does not contain DataArts Migration resource groups. If you want to migrate data in real time, create a DataArts Migration resource group incremental package.

Context
-------

-  When you create a DataArts Migration resource group incremental package, the system automatically creates a resource group required by real-time data integration jobs based on the specifications you set for the incremental package.
-  When buying a DataArts Migration resource group incremental package (pay-per-use resource package), pay attention to the following:

   -  When you buy a DataArts Migration resource group incremental package which is billed based on a pay-per-use package, the system does not automatically create a resource group for real-time processing migration jobs. Instead, you can use a resource group you have obtained on the DataArts Studio console for 745 hours each month within the validity period of the incremental package and in a specified region.

   -  If you have one or more resource groups in a region, the duration quota of your resource package will be deducted first. Any usage beyond the quota will be billed in pay-per-use mode. (If a resource package is shared by multiple clusters, the available package duration may be insufficient in each subscription period.)

      For example, if you purchase a one-month package (745 hours/month) and two resources are associated with the package, 372.5 hours (about 15.5 days) can be allocated to each resource group within the one-month subscription. Any usage beyond the allocated hours will be billed in pay-per-use mode.

   -  If you purchase a package and do not associate it with any resource group, the duration quota in the package will not be consumed and the validity period of the package will not be extended as well. Therefore, you are advised to make a plan before buying a package.

   -  If you want to enjoy the preferential price of the yearly/monthly incremental package, you can buy a yearly/monthly incremental package and then buy a pay-per-use incremental package which is in the same region and has the same specifications as the yearly/monthly incremental package.

   -  If you buy a pay-per-use incremental package and then a yearly/monthly incremental package in the same region and with the same specifications as the pay-per-use incremental package, the fees generated before you buy the yearly/monthly incremental package are charged in pay-per-use mode, and the subsequent fees are charged based on the yearly/monthly incremental package.

-  You can locate a DataArts Studio instance, click **More**, and select **View Packages** to view your incremental packages.
-  The prices of resource groups vary depending on their specifications. For details, see . You can also access the of DataArts Studio and select a region and specifications to quickly obtain the price of a resource group.

.. _dataartsstudio_01_0145__en-us_topic_0197155665_section6294131512712:

Creating a DataArts Migration Resource Group
--------------------------------------------

#. You can buy a resource group in either of the following ways:

   -  Method 1

      Locate an enabled instance and click **Create**.


      .. figure:: /_static/images/en-us_image_0000002269121941.png
         :alt: **Figure 1** Incremental package

         **Figure 1** Incremental package

   -  Method 2

      a. Locate an instance and click **Access**.
      b. In the upper right corner, click **Buy**.

   -  Method 3

      a. Locate an instance, click **More**, and select **Resources**.


         .. figure:: /_static/images/en-us_image_0000002269202017.png
            :alt: **Figure 2** Accessing Resources

            **Figure 2** Accessing Resources

      b. On the **Real-Time Resources** tab page, click **Buy Resource Group**.


         .. figure:: /_static/images/en-us_image_0000002269121969.png
            :alt: **Figure 3** Buying a resource group

            **Figure 3** Buying a resource group

2. On the displayed page, set parameters based on :ref:`Table 1 <dataartsstudio_01_0145__en-us_topic_0197155665_table18411132631912>`.


   .. figure:: /_static/images/en-us_image_0000002234082736.png
      :alt: **Figure 4** Creating a DataArts Migration resource group

      **Figure 4** Creating a DataArts Migration resource group

   .. _dataartsstudio_01_0145__en-us_topic_0197155665_table18411132631912:

   .. table:: **Table 1** Parameters for the DataArts Migration resource group incremental package

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================================================================================+
      | Package                           | DataArts Migration resource group                                                                                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                              | Enter the resource group name.                                                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Enter a description for the DataArts Migration resource group.                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Specifications                    | Select the specifications for the resource group, including the CU value, applicable environment, and maximum number of jobs that can be created.                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                |
      |                                   | The maximum number of migration tasks or jobs that can be created varies depending on the resource group specifications. Select the specifications that suit your needs. A maximum of 50 tables can be created for a single job (at least 2 CUs are required). |
      |                                   |                                                                                                                                                                                                                                                                |
      |                                   | Small: 16 CUs and a maximum of 7 jobs This option is applicable to tests and does not support high availability. It is not recommended.                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                |
      |                                   | Medium: 64 CUs and a maximum of 32 jobs                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                |
      |                                   | Large: 96 CUs and a maximum of 48 jobs                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                |
      |                                   | Super-large: 128 CUs and a maximum of 64 jobs                                                                                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Network Segment                   | Recommended network segments:                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                |
      |                                   | -  10.0.0.0-10.255.0.0/8-19                                                                                                                                                                                                                                    |
      |                                   | -  172.16.0.0-172.31.0.0/12-19                                                                                                                                                                                                                                 |
      |                                   | -  192.168.0.0~192.168.0.0/16 ~19                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                |
      |                                   |    .. note::                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                |
      |                                   |       -  To use VPC peering connections, set a network segment that does not overlap with that of the source and destination cluster or instance. If they overlap, the network will be disconnected.                                                           |
      |                                   |       -  Restricted by the CCE logic, the maximum length of the network segment mask is 19 bits. Network segments with a mask longer than 20 bits are not supported.                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Discount Quota (Hour)             | A discount package is prepaid by month or year. Compared with pay-per-use billing, the fee is reduced by 15% to 29%.                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. important::

      -  You cannot modify the specifications of an existing resource group. If you need higher specifications, create another resource group.
      -  A pay-per-use resource package in use cannot be unsubscribed from. For details, see .

3. Click **Create Now**, confirm the settings, and click **Next**. If the resource group fails to be created and a quota issue is displayed, contact the service personnel to apply for a quota.

4. Go to the corresponding workspace to view the DataArts Migration resource group you have created.

#. On the displayed page, set the following parameters:

   a. Select **DataArts Migration resource group** for **Package**.
   b. Select **Pay-per-Use Package** for **Billing Mode**.
   c. Specify a validity period in **Required Duration** for the package.
   d. Enter the number of subscribed packages in **Quantity**. For example, if you set **Required Duration** to **1 month** and **Quantity** to **2**, you will have a 1,490-hour quota in one month.

#. Click **Buy Now**, confirm the specifications, and click **Next**.
#. After you buy this package, the system will not automatically create a DataArts Migration resource group. You need to buy a pay-per-use incremental package in the same region and with the same specifications as this package by following the instructions in :ref:`Creating a DataArts Migration Resource Group <dataartsstudio_01_0145__en-us_topic_0197155665_section6294131512712>`. Then you can enjoy the favorable price of this package.
