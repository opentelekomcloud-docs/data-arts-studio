:original_name: dataartsstudio_03_0005.html

.. _dataartsstudio_03_0005:

What Data Modeling Methods Are Supported by DataArts Architecture?
==================================================================

Symptom
-------

Data modeling methods supported by DataArts Architecture

Solution
--------

DataArts Studio DataArts Architecture supports the following three types of modeling methods:

-  **ER modeling**

   ER modeling describes the business activities within an enterprise. Compliant with the third normal form (3NF), ER modeling is designed for data integration. It is used for combining and merging data with similarities by subject. ER modeling results cannot be used directly for decision-making, but they are a useful tool.

   You can divide ER modeling into three levels of abstraction: design conceptual models, logical models, and physical models.

   -  **Physical model**: A physical model is based on logical models and is used to design the database architecture for data storage with a range of technical factors all considered. For example, the selected data warehouse could be defined as DWS or DLI.

-  **Dimensional modeling**

   Dimensional modeling is the construction of models based on analysis and decision-making requirements. It is mainly used for data analysis. Dimensional modeling is focused on how to quickly analyze user requirements and respond rapidly to complicated large-scale queries.

   A multidimensional model is a fact table that consists of numeric measurement metrics. The fact table is associated with a group of dimensional tables that contain description attributes through primary or foreign keys.

   Typical dimensional models include star models and snowflake models used in some special scenarios.

   In the DataArts Architecture module of DataArts Studio, dimensional modeling involves constructing bus matrices to extract business facts and dimensions for model creation. You need to sort out business requirements for constructing metric systems and creating summary models.

-  **Data mart**

   A data mart (DM) aggregates data from multiple layers and consists of a specific analysis object and its related metrics. The DM provides all statistical data by subject.
