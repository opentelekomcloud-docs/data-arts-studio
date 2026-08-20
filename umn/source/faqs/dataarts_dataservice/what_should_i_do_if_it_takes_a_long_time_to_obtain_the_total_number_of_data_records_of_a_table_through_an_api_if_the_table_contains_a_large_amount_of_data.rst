:original_name: dataartsstudio_03_0240.html

.. _dataartsstudio_03_0240:

What Should I Do If It Takes a Long Time to Obtain the Total Number of Data Records of a Table Through an API If the Table Contains a Large Amount of Data?
===========================================================================================================================================================

Scenario
--------

During API creation, **Return Total Records** is enabled. If a table contains a large amount of data, obtaining the total number of data records of the table through an API is time-consuming.


.. figure:: /_static/images/en-us_image_0000002234076816.png
   :alt: **Figure 1** Return Total Records

   **Figure 1** Return Total Records

Solution
--------

During a pagination query, you can use the **use_total_num** parameter to determine whether the total number of data records is calculated and returned.

For example, add parameter **use_total_num** and set its value to **1** to obtain the total number of data records. In subsequent requests, add parameter **use_total_num** and set its value to **0** so that the total number of data records is not returned.


.. figure:: /_static/images/en-us_image_0000002234236668.png
   :alt: **Figure 2** Total number of data records

   **Figure 2** Total number of data records
