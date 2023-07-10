:original_name: dataartsstudio_03_0093.html

.. _dataartsstudio_03_0093:

What Should I Do If a Hive Migration Job Is Suspended for a Long Period of Time?
================================================================================

Manually stop the Hive migration job and add the following attribute settings to the Hive data connection:

-  **Attribute Name**: **hive.server2.idle.operation.timeout**
-  **Value**: **10m**

In the figure on the left:

|image1|

.. |image1| image:: /_static/images/en-us_image_0000001322089232.png
