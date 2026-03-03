:original_name: dataartsstudio_01_1205.html

.. _dataartsstudio_01_1205:

DataArts Catalog Operations
===========================

CTS provides records of operations on cloud service resources. With CTS, you can query, audit, and backtrack those operations.

.. table:: **Table 1** Key operations recorded by CTS

   +----------------------------------------+---------------------+--------------------------------+
   | Operation                              | Resource Type       | Trace Name                     |
   +========================================+=====================+================================+
   | Creating data masks                    | datamask            | createDataMask                 |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying data masks                    | datamask            | listDataMask                   |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying a data mask                   | datamask            | getDataMask                    |
   +----------------------------------------+---------------------+--------------------------------+
   | Deleting a data mask                   | datamask            | deleteDataMask                 |
   +----------------------------------------+---------------------+--------------------------------+
   | Deleting data masks                    | datamask            | batchDeleteDataMask            |
   +----------------------------------------+---------------------+--------------------------------+
   | Updating data masks                    | datamask            | updateDataMask                 |
   +----------------------------------------+---------------------+--------------------------------+
   | Creating and running a collection task | bridgetask          | createBridgeTask               |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying collection tasks              | bridgetask          | getBridgeTask                  |
   +----------------------------------------+---------------------+--------------------------------+
   | Editing collection tasks               | bridgetask          | updateBridgeTask               |
   +----------------------------------------+---------------------+--------------------------------+
   | Deleting collection tasks              | bridgetask          | batchDeleteBridgeTask          |
   +----------------------------------------+---------------------+--------------------------------+
   | Adding a tag to a data asset           | asset               | addTagToAsset                  |
   +----------------------------------------+---------------------+--------------------------------+
   | Adding a tag                           | tag                 | createTag                      |
   +----------------------------------------+---------------------+--------------------------------+
   | Adding tags                            | tag                 | batchCreateTag                 |
   +----------------------------------------+---------------------+--------------------------------+
   | Deleting tags                          | tag                 | batchDeleteTag                 |
   +----------------------------------------+---------------------+--------------------------------+
   | Updating a tag                         | tag                 | updateTag                      |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying tags                          | tag                 | getTags                        |
   +----------------------------------------+---------------------+--------------------------------+
   | Deleting a tag                         | tag                 | deleteTag                      |
   +----------------------------------------+---------------------+--------------------------------+
   | Creating a task directory              | bridgetaskcategory  | createBridgeTaskCategory       |
   +----------------------------------------+---------------------+--------------------------------+
   | Obtaining task directories             | bridgetaskcategory  | getBridgeTaskCategoryTree      |
   +----------------------------------------+---------------------+--------------------------------+
   | Editing a task directory               | bridgetaskcategory  | updateBridgeTaskCategory       |
   +----------------------------------------+---------------------+--------------------------------+
   | Deleting a task directory              | bridgetaskcategory  | deleteBridgeTaskCategory       |
   +----------------------------------------+---------------------+--------------------------------+
   | Creating a classification group        | classificationgroup | createClassificationGroup      |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying classification groups         | classificationgroup | listClassificationGroup        |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying a classification group        | classificationgroup | getClassificationGroup         |
   +----------------------------------------+---------------------+--------------------------------+
   | Deleting classification groups         | classificationgroup | batchDeleteClassificationGroup |
   +----------------------------------------+---------------------+--------------------------------+
   | Modifying a classification group       | classificationgroup | updateClassificationGroup      |
   +----------------------------------------+---------------------+--------------------------------+
   | Creating a classification rule         | classificationrule  | createClassificationRule       |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying classification rules          | classificationrule  | listClassificationRule         |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying a classification rule         | classificationrule  | getClassificationRule          |
   +----------------------------------------+---------------------+--------------------------------+
   | Deleting classification rules          | classificationrule  | batchDeleteClassificationRule  |
   +----------------------------------------+---------------------+--------------------------------+
   | Modifying a classification rule        | classificationrule  | updateClassificationRule       |
   +----------------------------------------+---------------------+--------------------------------+
   | Creating a data security level         | secrecylevel        | createSecrecyLevel             |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying data security levels          | secrecylevel        | listSecrecyLevel               |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying a data security level         | secrecylevel        | getSecrecyLevel                |
   +----------------------------------------+---------------------+--------------------------------+
   | Deleting data security levels          | secrecylevel        | batchDeleteSecrecyLevel        |
   +----------------------------------------+---------------------+--------------------------------+
   | Modifying a data security level        | secrecylevel        | updateSecrecyLevel             |
   +----------------------------------------+---------------------+--------------------------------+
   | Creating collection tasks              | bridgetask          | createBridgeTask               |
   +----------------------------------------+---------------------+--------------------------------+
   | Editing collection tasks               | bridgetask          | updateBridgeTask               |
   +----------------------------------------+---------------------+--------------------------------+
   | Deleting collection tasks              | bridgetask          | deleteBridgeTask               |
   +----------------------------------------+---------------------+--------------------------------+
   | Querying collection tasks              | bridgetask          | getTasks                       |
   +----------------------------------------+---------------------+--------------------------------+
