:original_name: dataartsstudio_03_0623.html

.. _dataartsstudio_03_0623:

What Should I Do If Error Message "The request parameter invalid" Is Displayed When I Use Python to Call the API for Executing Scripts?
=======================================================================================================================================

Symptom
-------

Error message "The request parameter invalid" is displayed when Python is used to call the API for executing scripts.

Call the script execution API by following the instructions in *"Executing a Script" in DataArts Studio API Reference* in *DataArts Studio Usage Guide*.

|image1|

View logs.

Error: Content type 'application/octet-stream' not supported

Possible Causes
---------------

The value of the **content-type** parameter is **application/json**.

.. note::

   **content-type** indicates the request body type or format. Its default value is **application/json**.

   If the request body contains Chinese characters, use **charset=utf8** to specify the Chinese character set.

Solution
--------

Change the value of **content-type**.

|image2|

After the value of **content-type** is changed, the API can be called successfully.

.. |image1| image:: /_static/images/en-us_image_0000002424392261.png
.. |image2| image:: /_static/images/en-us_image_0000002269116277.png
