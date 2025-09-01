:original_name: dataartsstudio_03_0341.html

.. _dataartsstudio_03_0341:

What Should I Do If invalid input syntax for integer: "true" Is Displayed During MySQL Database Migration?
==========================================================================================================

Symptom
-------

The MySQL database stores values **0** and **1**, rather than **true** and **false**. However, **true** or **false** is read during MySQL database migration, and the following error information is displayed: Unable to execute the SQL statement. Cause: ERROR: invalid input syntax for integer: "true" Where: COPY sd_mask_ext, line 1, column mask_type.

Possible Cause
--------------

By default, **tinyInt1isBit** is set to **true** for MySQL databases. As a result, **TINYINT(1)** is processed as **BIT** (that is, **Types.BOOLEAN**), and **1** or **0** is read as **true** or **false**.

Solution
--------

In the advanced attributes of the MySQL link, add either of the following parameters so that tables can be properly created at the destination:

-  Parameter **tinyInt1isBit**, with its value set to **false**

-  Parameter **mysql.bool.type.transform**, with its value set to **false**


   .. figure:: /_static/images/en-us_image_0000002269196149.png
      :alt: **Figure 1** Adding link attributes

      **Figure 1** Adding link attributes
