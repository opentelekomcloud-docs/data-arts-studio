:original_name: dataartsstudio_03_0404.html

.. _dataartsstudio_03_0404:

What Should I Do If Error Message "Workspace does not exists" Is Displayed When I Call a DataArts Factory API?
==============================================================================================================

Add the project ID to the request header in the code, that is, header.add("X-Project-Id",\ *Project ID*).
