:original_name: dataartsstudio_03_0628.html

.. _dataartsstudio_03_0628:

What Should I Do If the Default Queue of a New DLI SQL Script in DataArts Factory Has Been Deleted?
===================================================================================================

Symptom
-------

The default queue of a new DLI SQL script has been deleted.


.. figure:: /_static/images/en-us_image_0000002269115609.png
   :alt: **Figure 1** DLI SQL script

   **Figure 1** DLI SQL script

Possible Cause
--------------

When a DLI SQL script is used or opened, the queue selected for the script is stored in the cache. This queue is automatically selected for another DLI SQL script created in the workspace.

Solution
--------

When creating a DLI SQL script in the workspace, select a valid DLI resource queue. When you create DLI SQL scripts in the future, this valid DLI resource queue will be used by default.
