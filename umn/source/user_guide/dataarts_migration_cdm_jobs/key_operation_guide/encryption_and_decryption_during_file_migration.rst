:original_name: dataartsstudio_01_0590.html

.. _dataartsstudio_01_0590:

Encryption and Decryption During File Migration
===============================================

When you migrate files to a file system, CDM can encrypt and decrypt those files. Currently, CDM supports the following encryption modes:

-  :ref:`AES-256-GCM <dataartsstudio_01_0590__en-us_topic_0000001197659213_en-us_topic_0000001197658801_en-us_topic_0108275362_section17832638131012>`
-  :ref:`KMS Encryption <dataartsstudio_01_0590__en-us_topic_0000001197659213_en-us_topic_0000001197658801_en-us_topic_0108275362_section9481412161214>`

.. _dataartsstudio_01_0590__en-us_topic_0000001197659213_en-us_topic_0000001197658801_en-us_topic_0108275362_section17832638131012:

AES-256-GCM
-----------

Currently, only AES-256-GCM (NoPadding) is supported. This algorithm is used for encryption at the migration destination and decryption at the migration source. The supported source and destination data sources are as follows:

-  Data sources supported by the migration source: HDFS (supported in the binary format)
-  Data sources supported by the migration destination: HDFS (supported in the binary format)

The following part describes how to use AES-256-GCM to decrypt the encrypted files to be exported from HDFS and encrypt the files to be imported to HDFS.

-  **Configure decryption at the migration source.**

   When you use CDM to create a job for exporting files from HDFS, set the migration source to HDFS and file format to binary, and set the following parameters in the advanced settings of **Source Job Configuration**:

   #. **Encryption**: Select **AES-256-GCM**.
   #. **DEK**: The key must be the same as that configured in encryption. Otherwise, the decrypted data is incorrect and the system does not display an error message.
   #. **IV**: The initialization vector must be the same as that configured in encryption. Otherwise, the decrypted data is incorrect and the system does not display an error message.

   In this way, after CDM exports encrypted files from HDFS, the files written to the migration destination are decrypted plaintext files.

-  **Configure encryption at the migration destination.**

   When you create a CDM job to import files to HDFS, set the migration destination to HDFS and file format to binary, and set the following parameters in the advanced settings of **Destination Job Configuration**:

   #. **Encryption**: Select **AES-256-GCM**.
   #. **DEK**: custom encryption key. The key consists of 64 hexadecimal numbers. It is case-insensitive but must contain 64 characters. For example, **DD0AE00DFECD78BF051BCFDA25BD4E320DB0A7AC75A1F3FC3D3C56A457DCDC1B**.
   #. **IV**: custom initialization vector. The initialization vector consists of 32 hexadecimal numbers. It is case-insensitive but must contain 32 characters. For example, **5C91687BA886EDCD12ACBC3FF19A3C3F**.

   In this way, after CDM imports files to HDFS, the files in the destination HDFS are encrypted using the AES-256-GCM algorithm.

.. _dataartsstudio_01_0590__en-us_topic_0000001197659213_en-us_topic_0000001197658801_en-us_topic_0108275362_section9481412161214:

KMS Encryption
--------------

.. note::

   The migration source does not support KMS encryption.

CDM supports KMS encryption if tables, files, or a whole database is migrated to OBS. In the **Advanced Attributes** area of the **Destination Job Configuration** page, set the parameters.

A key must be created in KMS of DEW in advance. For details, see the *Data Encryption Workshop User Guide*.

After KMS encryption is enabled, objects to be uploaded will be encrypted and stored on OBS. When you download the encrypted objects, the encrypted data will be decrypted on the server and displayed in plaintext to users.

.. note::

   -  If KMS encryption is enabled, :ref:`MD5 verification <dataartsstudio_01_0591>` cannot be used.
   -  If the KMS ID of another project is used, change **Project ID** to the ID of the project to which KMS belongs. If KMS and CDM are in the same project, retain the default value of **Project ID**.
   -  After KMS encryption is performed, the encryption status of the objects on OBS cannot be changed.
   -  A key in use cannot be deleted. Otherwise, the object encrypted with this key cannot be downloaded.
