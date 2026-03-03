:original_name: dataartsstudio_01_1009.html

.. _dataartsstudio_01_1009:

Sensitive Data Governance Process
=================================

Sensitive Data Definition
-------------------------

Sensitive data is usually used by others without the consent of individuals or companies. The interests of individuals or companies might be seriously compromised.

According to *GB/T 35273-2020 Information Security Technology — Personal Information Security Specification*, sensitive personal data includes:

-  Personal property information (deposit, credit, and banking transactions)
-  Personal health state and physiological information (physical examination information and medical records)
-  Personal biometric information (fingerprint and facial features)
-  Personal identity information (ID card, social security card, and driving license)
-  Other information (religious belief and precise location)

Sensitive Data Protection Methods
---------------------------------

-  **Sensitive data identification and label adding**

   Classify and grade data to facilitate security management of different granularities and levels.

-  **Data leakage detection and prevention**

   If sensitive data is frequently accessed, a risk alarm is reported immediately.

-  **Static data masking and data watermarking**

   Sensitive data with a specific security level can be masked or watermarked when being provided to external systems.

-  **Personal information compliance**

   Accurately distinguish and protect personal data to avoid compliance issues.

-  **General data protection regulation (GDPR) compliance**

   Comply with GDPR requirements on detecting and protecting sensitive data, and audit the use of sensitive data.

-  **Data security compliance check**

   Based on the analysis of sensitive data, develop data security compliance management regulations to help enterprises build and improve their information security compliance management systems.

Sensitive Data Identification Process
-------------------------------------

:ref:`Figure 1 <dataartsstudio_01_1009__en-us_topic_0000001627400086_fig6960633345>` shows the sensitive data identification process.

.. _dataartsstudio_01_1009__en-us_topic_0000001627400086_fig6960633345:

.. figure:: /_static/images/en-us_image_0000002269117509.png
   :alt: **Figure 1** Sensitive data identification process

   **Figure 1** Sensitive data identification process

#. :ref:`Create data security levels. <dataartsstudio_01_1010>`

   Before performing any operations on data, create security levels for the data to specify the scope of confidential information.

#. :ref:`Create data classifications. <dataartsstudio_01_1030>`

   If data security levels cannot meet the data classification requirements in the case of a large amount of data, you can create data classifications for data of different values to better manage and measure your data.

#. :ref:`Create identification rules. <dataartsstudio_01_1011>`

   Define sensitive data identification standards.

#. :ref:`Create identification rule groups. <dataartsstudio_01_1012>`

   Define sensitive data identification rules and rule groups for the purpose of effectively identifying sensitive data in a database.

#. :ref:`Discover sensitive data. <dataartsstudio_01_1013>`

   Create and run a sensitive data identification task.

#. :ref:`View sensitive data distribution. <dataartsstudio_01_1014>`

   View the sensitive data identified by the sensitive data identification task.
