:original_name: dataartsstudio_01_1018.html

.. _dataartsstudio_01_1018:

Overview
========

DataArts Security provides privacy data protection to protect enterprises' sensitive data. You can use static and dynamic data masking, and data, file, and dynamic watermarking to prevent your data from being misused, disclosed, or stolen intentionally or unintentionally. In this way, your sensitive data is secure, complete, and safe to use.

Methods
-------

Privacy data protection provides the following methods for protecting sensitive data:

-  Static masking

   Static data masking prevents private data leakage, and ensures regulatory compliance as well as data security for enterprises. Sensitive data is masked, truncated, and hashed based on the abundant and effective built-in masking algorithms, and the processed data can be written to the target data table. For security purpose, it is the target data table that can be used to provide services for external requirements.

-  Dynamic data masking

   After a dynamic masking policy is created in DataArts Security, the system synchronizes the policy to the data source. The data source dynamically masks data columns based on specified rules. When the users and user groups specified in the policy access sensitive data, the system returns the data that is dynamically masked by the data source to protect sensitive data from being disclosed.

-  Data watermarking

   Users can embed watermarks into data. The watermarked data is transparent, available, and covert. It is not easy for others to crack the watermarked data. Even if data is leaked, watermarks can be traced to find the person accountable for the leakage. Once the watermarked data is used without the content of data owners, users can import the leaked file to trace and extract the watermarks. In this case, the organization or person that is accountable for the leakage problem can be easily found.

-  File watermarks

   File watermarks can be injected into data files in the following scenarios to accurately locate security events:

   -  Insert invisible watermarks into structured data files (CSV, XML, and JSON files) and extract the watermarks.
   -  Insert visible watermarks into unstructured data files (DOCX, PPTX, XLSX, and PDF files) and open the files on a local host to view the watermarks.

-  Dynamic watermarking

   After data development dynamic watermarking is enabled for DataArts Security and a dynamic watermarking policy is created, when a user group or role specified in the policy dumps or downloads sensitive data in DataArts Factory, DataArts Factory injects an invisible watermark into the sensitive data to protect it from being disclosed.
