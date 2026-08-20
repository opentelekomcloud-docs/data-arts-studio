:original_name: dataartsstudio_03_0516.html

.. _dataartsstudio_03_0516:

How Should I Select a Subject When a Public Dimension (Date, Region, Supplier, or Product) Is Shared by Multiple Subject Areas?
===============================================================================================================================

DataArts Architecture does not provide public dimensions. Each dimension must belong to a subject. If a public dimension is used, you are advised to create a public subject for the public dimension.

In addition, permissions of dimensions are classified by model instead of by subject. Therefore, subjects do not affect permission control or query.
