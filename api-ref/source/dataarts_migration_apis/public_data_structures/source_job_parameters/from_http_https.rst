:original_name: dataartsstudio_02_0288.html

.. _dataartsstudio_02_0288:

From HTTP/HTTPS
===============

Sample JSON File
----------------

.. code-block::

   "from-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "fromJobConfig.inputDirectory",
                   "value": "http://10.114.196.186:8080/httpfrom/symbol.txt"
                 },
                 {
                   "name": "fromJobConfig.inputFormat",
                   "value": "BINARY_FILE"
                 },
                 {
                   "name": "fromJobConfig.fromCompression",
                   "value": "TARGZ"
                 },
                 {
                   "name": "fromJobConfig.compressedFileSuffix",
                   "value": "*"
                 },
                 {
                   "name": "fromJobConfig.fileSeparator",
                   "value": "|"
                 }
               ],
               "name": "fromJobConfig"
             }
           ]
         }

Parameter Description
---------------------

+------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter                          | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                               |
+====================================+=================+=================+===========================================================================================================================================================================================================================================================================================+
| fromJobConfig.inputDirectory       | Yes             | String          | URL of the file to be extracted                                                                                                                                                                                                                                                           |
|                                    |                 |                 |                                                                                                                                                                                                                                                                                           |
|                                    |                 |                 | These connectors are used to read files with an HTTP/HTTPS URL, such as reading public files on the third-party object storage system and web disks.                                                                                                                                      |
+------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.inputFormat          | Yes             | Enumeration     | File format required for data transmission. Currently, only the binary format is supported.                                                                                                                                                                                               |
+------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.fromCompression      | No              | Enumeration     | Compression format of the source files. The options are as follows:                                                                                                                                                                                                                       |
|                                    |                 |                 |                                                                                                                                                                                                                                                                                           |
|                                    |                 |                 | -  **NONE**: Files in all formats are transferred.                                                                                                                                                                                                                                        |
|                                    |                 |                 | -  **GZIP**: Files in gzip format are transferred.                                                                                                                                                                                                                                        |
|                                    |                 |                 | -  **ZIP**: Files in Zip format are transferred.                                                                                                                                                                                                                                          |
|                                    |                 |                 | -  **TAR.GZ**: Files in TAR.GZ format are transferred.                                                                                                                                                                                                                                    |
+------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.compressedFileSuffix | No              | String          | Extension of the files to be decompressed. The decompression operation is performed only when the file name extension is used in a batch of files. Otherwise, files are transferred in the original format. If you enter **\*** or leave the parameter blank, all files are decompressed. |
+------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.fileSeparator        | No              | String          | File separator. When multiple files are transferred, CDM uses the file separator to separate files. The default value is **\|**.                                                                                                                                                          |
+------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.useQuery             | No              | Boolean         | -  If you set this parameter to **true**, the name of the objects uploaded to OBS does not carry the **query** parameter.                                                                                                                                                                 |
|                                    |                 |                 | -  If you set this parameter to **false**, the name of the objects uploaded to OBS carries the **query** parameter.                                                                                                                                                                       |
+------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.md5FileSuffix        | No              | String          | Check whether the files extracted by CDM are consistent with those in the migration source.                                                                                                                                                                                               |
+------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
