:original_name: dataartsstudio_03_0167.html

.. _dataartsstudio_03_0167:

What Should I Do If Message "CDM Does Not Support Auto Creation of an Empty Table with No Column" Is Displayed When I Enable Auto Table Creation?
=================================================================================================================================================

The cause is that the database table name contains special characters, resulting in incorrect syntax. You can resolve this issue by renaming the database table according to the naming rules for database objects.

For example, the name of a data table in the DWS data warehouse can contain a maximum of 63 characters and support letters, digits, underscores (_), dollar signs ($), and number signs (#), and must start with a letter or underscore (_).
