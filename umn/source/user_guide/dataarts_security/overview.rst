:original_name: dataartsstudio_01_1001.html

.. _dataartsstudio_01_1001:

Overview
========

DataArts Security protects data lake security and meets the data security and governance requirements of different roles, such as data development engineers, data security administrators, data security auditors, and data security operators.


.. figure:: /_static/images/en-us_image_0000002234078752.png
   :alt: **Figure 1** DataArts Studio DataArts Security framework

   **Figure 1** DataArts Studio DataArts Security framework

-  **Resources**: databases, tables, fields, and computing engine queues in the cloud data lake. They include the databases, tables, and fields of MRS Hive/Spark, DLI, and GaussDB(DWS), as well as computing queues of MRS Yarn and DLI.
-  **End-to-end data security**: DataArts Studio protects data security throughout data integration, data management (architecture design, metric design, and data quality management), data development, data asset management, and data services. It protects data throughout its lifecycle and ensures secure data flow through measures such as data access control and data masking. For example, it can mask sensitive fields in the data to be imported to the data lake and can control access to data sources. When analysts query data, sensitive data can be protected using dynamic masking policies or field access permissions.
-  **Unified data security policies**: unified permission governance, sensitive data governance, privacy protection policies, and data security operations.

Scenario
--------

DataArts Security meets the data security and governance requirements of different roles, such as data development engineers, data security administrators, data security auditors, and data security operators. :ref:`Figure 2 <dataartsstudio_01_1001__fig14309165617119>` shows how different roles can use DataArts Security.

.. _dataartsstudio_01_1001__fig14309165617119:

.. figure:: /_static/images/en-us_image_0000002269117941.png
   :alt: **Figure 2** How different roles can use DataArts Security

   **Figure 2** How different roles can use DataArts Security

Advantages
----------

-  DataArts Security integrates and centrally manages different big data services, such as MRS, DLI, and GaussDB(DWS), and provides unified permission configuration to improve usability and maintainability.
-  DataArts Security provides end-to-end data security capabilities, such as unified permission governance, sensitive data governance, and privacy protection policy management.
-  Unified permission governance allows you to allocate workspace permission sets (databases and tables that can be managed by each project workspace). You can assign permissions to users and user groups of different roles in a workspace. Cross-workspace dependency supports on-demand permission application, review, and approval.
-  Sensitive data management supports classification, automatic discovery, and security management policies based on security levels of sensitive data.
-  Privacy protection and management provides static and dynamic data masking and data watermarking capabilities to meet service requirements while ensuring data security.

Function
--------

DataArts Security provides the following functions:

-  :ref:`Unified permission governance <dataartsstudio_01_1151>`

   DataArts Security provides unified management of data permissions based on MRS, DLI, and GaussDB(DWS). You can create workspace permission sets, permission sets, or roles, and use them to control access to MRS, DLI, and GaussDB(DWS) data, assign the minimum permissions to users and user groups on demand, and reduce data security risks.

-  :ref:`Sensitive data governance <dataartsstudio_01_1009>`

   You can create sensitive data identification rules (or rule groups), or use the built-in identification rules (or rule groups), to detect, classify, and grade sensitive data.

-  :ref:`Privacy protection and management <dataartsstudio_01_1018>`

   You can use static and dynamic data masking, and data, file, and dynamic watermarking to prevent your data from being misused, disclosed, or stolen intentionally or unintentionally. In this way, your sensitive data is secure, complete, and safe to use.

-  :ref:`Data security operations <dataartsstudio_01_1181>`

   DataArts Security provides data security diagnosis and data lake access and audit log query capabilities, helping you manage security better.
