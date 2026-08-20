:original_name: dataartsstudio_01_0329.html

.. _dataartsstudio_01_0329:

Configuring an Output Processing Operator
=========================================

The Output Processing operator maps the error codes and result sets, and converts the format of an API workflow to determine the format of the returned data.

.. table:: **Table 1** Output Processing operator parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory             | Description                                                                                                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================================================================================================+
   | Error Code Mappings   | No                    | Error codes returned by DataArts DataService can be mapped to custom information,                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                             |
   |                       |                       | for example, error code **DLM.0** can be mapped to **OK**.                                                                                                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Result Set Mappings   | Yes                   | The result set names of one or more Common API operators can be mapped to custom names which will be used in the JSON string or file name. Result sets that are not mapped will not be output to the final returned result. |
   |                       |                       |                                                                                                                                                                                                                             |
   |                       |                       | The node mapping expression is in **${**\ **Node code**\ **\|payload}** format. You can obtain the node code by clicking a node in the API orchestration canvas, and copy the code by clicking |image1|.                    |
   |                       |                       |                                                                                                                                                                                                                             |
   |                       |                       | .. _dataartsstudio_01_0329__fig958994013816:                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                             |
   |                       |                       | .. figure:: /_static/images/en-us_image_0000002234236412.png                                                                                                                                                                |
   |                       |                       |    :alt: **Figure 1** Viewing the node code                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                                             |
   |                       |                       |    **Figure 1** Viewing the node code                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                             |
   |                       |                       | For example, if the node code is **NormalApi_5a256**, set the node mapping expression to **${NormalApi_5a256|payload}** and the result set name to **sales record**.                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Format Conversion     | No                    | By default, a workflow result is a JSON string. You can export each mapped result set to a CSV, TXT, Excel, or XML file, or export all mapped result sets to a .zip file.                                                   |
   |                       |                       |                                                                                                                                                                                                                             |
   |                       |                       | Resumable data transfer is not supported during export.                                                                                                                                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002269195857.png
