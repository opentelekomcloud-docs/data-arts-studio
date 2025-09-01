:original_name: dataartsstudio_03_0417.html

.. _dataartsstudio_03_0417:

What Should I Do If Error Message "UnicodeEncodeError: 'ascii' codec can't encode characters in position 63-64: ordinal not in range(128)" Is Displayed When I Run a Python Script?
===================================================================================================================================================================================

This error occurs when **json.dumps(json_data, ensure_ascii=False)** is configured in the Python script. The following figure shows the error.


.. figure:: /_static/images/en-us_image_0000002234076304.png
   :alt: **Figure 1** Error message

   **Figure 1** Error message

Possible Cause
--------------

By default, DataArts Studio uses the Python2 interpreter. This interpreter uses the ASCII encoding format by default and cannot encode Chinese characters. As a result, the error occurs. Therefore, you need to convert the encoding format to UTF-8.

Solution
--------

#. Use the Python3 interpreter to create a soft connection on the host.


   .. figure:: /_static/images/en-us_image_0000002234236144.png
      :alt: **Figure 2** Creating a soft connection on the host

      **Figure 2** Creating a soft connection on the host

#. Set the standard encoding mode in the file.

   # -``*``- coding: utf-8 -``*``-; Alternatively, set the encoding format for the host, that is, create a **sitecustomize.py** file in the **Lib\\site-packages** folder in the Python installation directory and write the following information in the file:

   .. code-block::

      # encoding=utf8
      #import sys
      #reload(sys)
      #sys.setdefaultencoding('utf8')

#. Restart Python and run **sys.getdefaultencoding()** to view the default encoding format, which is **utf8**.
