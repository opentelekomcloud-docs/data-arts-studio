:original_name: dataartsstudio_03_0054.html

.. _dataartsstudio_03_0054:

What Should I Do If a GaussDB(DWS) Connection Test Fails When SSL Is Enabled for the Connection?
================================================================================================

Possible Causes
---------------

The failure may be caused by the rights separation function of the GaussDB(DWS) cluster.

Solution
--------

On the DWS console, click the corresponding cluster, choose **Security Settings**, and disable **Rights Separation**.


.. figure:: /_static/images/en-us_image_0000002234236240.png
   :alt: **Figure 1** Disabling Rights Separation for the DWS cluster

   **Figure 1** Disabling Rights Separation for the DWS cluster
