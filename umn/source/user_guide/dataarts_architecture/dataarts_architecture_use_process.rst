:original_name: dataartsstudio_01_0541.html

.. _dataartsstudio_01_0541:

DataArts Architecture Use Process
=================================

The process of using DataArts Architecture is as follows.


.. figure:: /_static/images/en-us_image_0000002269116861.png
   :alt: **Figure 1** DataArts Architecture use process

   **Figure 1** DataArts Architecture use process

#. **Preparations**

   -  **Add reviewers**: In the DataArts Architecture module, all business processes must be approved. Therefore, add reviewers first before conducting any operations. Only the workspace admin has the permissions required to add reviewers.
   -  **Configuration Center** provides abundant custom options. You can customize the configuration to meet your demands.

#. **Data Survey**: A data survey involves collecting data that is generated when sorting business requirements, creating business processes, and classifying data subjects based on the existing business data and industry status.

   -  **Subject design** is a hierarchical architecture that classifies and defines data to help clarify data assets and specify relationships between business domains and business objects.

      -  **Subject area group** is used to group business domains based on scenarios.
      -  **Subject area** is the high-level data classification that does not overlap and is used to manage business objects.
      -  **Business object** includes important information about people, events, and things that are indispensable to enterprise operations and management.

   -  **Process design** is used to generate a structured framework of process. It describes the categories, levels, boundaries, scopes, and input/output relationships of an enterprise's processes, and reflects the business models and characteristics of the enterprise.
   -  **Data warehouse planning**: Manage data warehouse layers and modeling in a unified manner. You can customize data warehouse layers.

#. **Standards**: Create lookup tables and data standards.

   -  A **lookup table** includes a series of allowed values and additional text descriptions that are generally associated with data standards to generate a range of values for the verification of quality monitoring rules.
   -  **Data standards** refer to the description of attribute data meanings and business rules that enterprises must comply with. It describes the common understanding of certain data at the company level.

#. **Model design:** Perform hierarchical modeling using logical models, ER modeling, dimensional modeling, and data mart.

   -  **Logical models**: Create, modify, and delete logical models, and convert logical models into physical models. You can also create and publish logical entities and perform operations such as reversing databases.
   -  **ER modeling**: Create SDI and DWI models based on ER modeling.

      -  **SDI** stands for Source Data Integration and is the source data layer. SDI is a simple implementation of source system data.
      -  **DWI** stands for Data Warehouse Integration, also called the data consolidation layer. DWI integrates and cleans data from multiple source systems, and implements entity relationship modeling based on the three normal forms.

   -  **Dimensional modeling**: Create DWR models and release dimensions and fact tables based on ER modeling.

      -  **Data Warehouse Report (DWR)** is based on the multi-dimensional model and its data granularity is the same as that of the DWI layer.
      -  **Dimension** is the perspective to observe and analyze business data and assist in data aggregation, drilling, slicing, and analysis, and used as a GROUP BY condition in SQL statements.
      -  A **fact table** that belongs to a business process can enrich the affair information corresponding to the specific business process.

   -  **Data mart**: Create a DM layer and publish summary tables.

      -  **Data Mart (DM)** is where multiple types of data are summarized. DM is designed to display the summarized data.
      -  A **summary table** consists of specific analysis objects (for example, members) and related statistical metrics. The statistical metrics included in a summary table have the same statistical granularity (for example, members). The summary table provides users with all statistics-granularity-themed data (such as a member theme market).

#. **Metrics**: Create business and technical metrics. Technical metrics include atomic, derivative, and compound metrics.

   -  A **business metric** consists of a name and a value. The metric name and its definition reflect the quality and quantity of the metric. The metric value reflects the quantifiable values of the specified time, location, and condition of the metric.

      Business metrics are used to guide technical metrics, and technical metrics are used to implement business metrics.

   -  **Atomic metrics** are generated based on dimension tables and fact tables of a multidimensional model. The objects and the finest data granularity of an atomic metric are consistent with those of the multidimensional model.

      An atomic metric usually consists of measures and attributes related with measures and business objects, all of which aim to support agile self-service consumption of the metric.

   -  **Derivative metrics** are aggregated from the definitions, modifiers, and dimensions of atomic metrics. Therefore, their definitions, modifiers, and dimensions are derived from the attributes of atomic metric associated tables as well.

   -  **Compound metrics** are generated by adding one or more derivative metrics. The dimensions and modifiers of a compound metric are the same as those of the derivative metrics.

      New dimensions and modifiers cannot be generated outside the scope of derivative metrics, dimensions, and modifiers.
