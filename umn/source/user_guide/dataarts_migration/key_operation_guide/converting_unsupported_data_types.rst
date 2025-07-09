:original_name: dataartsstudio_01_0209.html

.. _dataartsstudio_01_0209:

Converting Unsupported Data Types
=================================

Scenario
--------

When field mapping is configured on CDM, a message is displayed indicating that the data type of the field is not supported and the field needs to be deleted. If you need to use this field, you can use SQL statements to convert the field type in the source job configuration to the type supported by CDM for data migration.

|image1|

Procedure
---------

#. Modify the CDM migration job and enable **Use SQL Statement**.

   |image2|

   .. note::

      The SQL statement format is as follows: **select id,cast**\ (*Original field name* **as INT) as** *New field name, which can be the same as the original field name* **from schemaName.tableName;**

      For example, select \`id`, \`name`, cast(`sex\` AS char(255) ) AS \`sex\` from \`test_1117869`.`test_no_support_type`;

#. Wait for the fields to be converted to the data types supported by CDM.

   |image3|

.. |image1| image:: /_static/images/en-us_image_0000002270848222.png
.. |image2| image:: /_static/images/en-us_image_0000002270848226.png
.. |image3| image:: /_static/images/en-us_image_0000002270791360.png
