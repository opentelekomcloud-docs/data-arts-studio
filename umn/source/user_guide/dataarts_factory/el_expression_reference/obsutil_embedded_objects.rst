:original_name: dataartsstudio_01_0553.html

.. _dataartsstudio_01_0553:

OBSUtil Embedded Objects
========================

The OBSUtil embedded objects provide a series of OBS operation methods, for example, checking whether an OBS file or directory exists.

Methods
-------

.. table:: **Table 1** Method description

   +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Method                                 | Description                                                                                                                                                              |
   +========================================+==========================================================================================================================================================================+
   | boolean isExistOBSPath(String obsPath) | Check whether the OBS file or the OBS directory that ends with a slash (/) exists. If the file or directory exists, **true** is returned. If not, **false** is returned. |
   +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Examples
--------

-  The following is the EL expression for checking whether the OBS directory that ends with a slash (/) exists:

   #{OBSUtil.isExistOBSPath("obs://test/jobs/")}

-  The following is the EL expression for checking whether the OBS file exists:

   #{OBSUtil.isExistOBSPath("obs://test/jobs/job.log")}
