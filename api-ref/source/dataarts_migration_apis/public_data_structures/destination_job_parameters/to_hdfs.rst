:original_name: dataartsstudio_02_0298.html

.. _dataartsstudio_02_0298:

To HDFS
=======

Sample JSON File
----------------

.. code-block::

   "to-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "toJobConfig.outputDirectory",
                   "value": "/hdfsto"
                 },
                 {
                   "name": "toJobConfig.outputFormat",
                   "value": "BINARY_FILE"
                 },
                 {
                   "name": "toJobConfig.writeToTempFile",
                   "value": "false"
                 },
                 {
                   "name": "toJobConfig.duplicateFileOpType",
                   "value": "REPLACE"
                 },
                 {
                   "name": "toJobConfig.compression",
                   "value": "NONE"
                 },
                 {
                   "name": "toJobConfig.appendMode",
                   "value": "true"
                 }
               ],
               "name": "toJobConfig"
             }
           ]
         }

Parameter Description
---------------------

+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter                       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                      |
+=================================+=================+=================+==================================================================================================================================================================================================================================================================================+
| toJobConfig.outputDirectory     | Yes             | String          | Path to which data is written. For example, **/data_dir**.                                                                                                                                                                                                                       |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.outputFormat        | Yes             | Enumeration     | File format required for data writes (except the binary format). Currently, the following file formats are supported:                                                                                                                                                            |
|                                 |                 |                 |                                                                                                                                                                                                                                                                                  |
|                                 |                 |                 | -  **CSV_FILE**: Write data in CSV format.                                                                                                                                                                                                                                       |
|                                 |                 |                 | -  **BINARY_FILE**: Files are directly transferred without resolving the content. CDM writes the file without changing the file format.                                                                                                                                          |
|                                 |                 |                 |                                                                                                                                                                                                                                                                                  |
|                                 |                 |                 | If you select **BINARY_FILE**, the migration source must also be a file system.                                                                                                                                                                                                  |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.lineSeparator       | No              | String          | Line feed character. This parameter is valid only when **toJobConfig.outputFormat** is **CSV_FILE**. The default value is **\\r\\n**.                                                                                                                                            |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.fieldSeparator      | No              | String          | Column delimiter. This parameter is valid only when **toJobConfig.outputFormat** is **CSV_FILE**. The default value is **,**.                                                                                                                                                    |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.writeToTempFile     | No              | Boolean         | The binary file is written to a **.tmp** file first. After the migration is successful, run the **rename** or **move** command at the migration destination to restore the file.                                                                                                 |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.duplicateFileOpType | No              | Enumeration     | Method for processing duplicate files. If the name and size of a file are the same as those of another file, the file is regarded as a duplicate file. Duplicate files can be processed in the following ways:                                                                   |
|                                 |                 |                 |                                                                                                                                                                                                                                                                                  |
|                                 |                 |                 | -  **REPLACE**: Replace duplicate files.                                                                                                                                                                                                                                         |
|                                 |                 |                 | -  **SKIP**: Skip duplicate files.                                                                                                                                                                                                                                               |
|                                 |                 |                 | -  **ABANDON**: Stop the job when any duplicate file is found.                                                                                                                                                                                                                   |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.compression         | No              | Enumeration     | After the file is written, select the compression format of the file. The following compression formats are supported:                                                                                                                                                           |
|                                 |                 |                 |                                                                                                                                                                                                                                                                                  |
|                                 |                 |                 | -  **NONE**: Do not compress the file.                                                                                                                                                                                                                                           |
|                                 |                 |                 | -  **DEFLATE**: Compress the file in DEFLATE format.                                                                                                                                                                                                                             |
|                                 |                 |                 | -  **GZIP**: Compress the file in gzip format.                                                                                                                                                                                                                                   |
|                                 |                 |                 | -  **BZIP2**: Compress the file in bzip2 format.                                                                                                                                                                                                                                 |
|                                 |                 |                 | -  **LZ4**: Compress the file in LZ4 format.                                                                                                                                                                                                                                     |
|                                 |                 |                 | -  **SNAPPY**: Compress the file in Snappy format.                                                                                                                                                                                                                               |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.appendMode          | Yes             | Boolean         | Whether to write data when one or more files exist in the loading path. The default value is **false**.                                                                                                                                                                          |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.encryption          | No              | Enumeration     | This parameter is available only when **toJobConfig.outputFormat** is set to **BINARY_FILE**. It specifies whether to encrypt the uploaded data, and the encryption method. The options are as follows:                                                                          |
|                                 |                 |                 |                                                                                                                                                                                                                                                                                  |
|                                 |                 |                 | -  **NONE**: Directly write data without encryption.                                                                                                                                                                                                                             |
|                                 |                 |                 | -  **AES-256-GCM**: Use the AES 256-bit encryption algorithm to encrypt data. Currently, only the AES-256-GCM (NoPadding) encryption algorithm is supported.                                                                                                                     |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.dek                 | No              | String          | Data encryption key. This parameter is available when **toJobConfig.encryption** is set to **AES-256-GCM**. The key is a string of 64-bit hexadecimal numbers.                                                                                                                   |
|                                 |                 |                 |                                                                                                                                                                                                                                                                                  |
|                                 |                 |                 | Remember the key configured here because the decryption key must be the same as that configured here. If the encryption and decryption keys are inconsistent, the system does not report an exception, but the decrypted data is incorrect.                                      |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.iv                  | No              | String          | Initialization vector. This parameter is available when **toJobConfig.encryption** is set to **AES-256-GCM**. The initialization vector is a string of 32-bit hexadecimal numbers.                                                                                               |
|                                 |                 |                 |                                                                                                                                                                                                                                                                                  |
|                                 |                 |                 | Remember the initialization vector configured here because the initialization vector used for decryption must be the same as that configured here. If the initialization vectors are inconsistent, the system does not report an exception, but the decrypted data is incorrect. |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
