:original_name: dataartsstudio_01_1202.html

.. _dataartsstudio_01_1202:

DataArts Architecture Operations
================================

CTS provides records of operations on cloud service resources. With CTS, you can query, audit, and backtrack those operations.

.. table:: **Table 1** Key operations recorded by CTS

   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Operation                                      | Resource Type | Resource Names          | Trace Name                     |
   +================================================+===============+=========================+================================+
   | Querying subjects                              | DAYU_DS       | dsSubject               | getListSubject                 |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating subjects                              | DAYU_DS       | dsSubject               | createSubject                  |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating subjects                              | DAYU_DS       | dsSubject               | updateSubject                  |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing subjects                            | DAYU_DS       | dsSubject               | publishedSubject               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending subjects                            | DAYU_DS       | dsSubject               | offlineSubject                 |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting subjects                              | DAYU_DS       | dsSubject               | deleteSubject                  |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying processes                             | DAYU_DS       | dsBizCatalog            | getListBizCatalog              |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating processes                             | DAYU_DS       | dsBizCatalog            | createBizCatalog               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating processes                             | DAYU_DS       | dsBizCatalog            | updateBizCatalog               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting processes                             | DAYU_DS       | dsBizCatalog            | deleteBizCatalog               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying lookup tables                         | DAYU_DS       | dsCodeTable             | getListCodeTable               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating lookup tables                         | DAYU_DS       | dsCodeTable             | createCodeTable                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating lookup tables                         | DAYU_DS       | dsCodeTable             | updateCodeTable                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing lookup tables                       | DAYU_DS       | dsCodeTable             | publishedCodeTable             |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending lookup tables                       | DAYU_DS       | dsCodeTable             | offlineCodeTable               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting lookup tables                         | DAYU_DS       | dsCodeTable             | deleteCodeTable                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying data standards                        | DAYU_DS       | dsStandardElement       | getListStandardElement         |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating data standards                        | DAYU_DS       | dsStandardElement       | createStandardElement          |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating data standards                        | DAYU_DS       | dsStandardElement       | updateStandardElement          |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing data standards                      | DAYU_DS       | dsStandardElement       | publishedStandardElement       |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending data standards                      | DAYU_DS       | dsStandardElement       | offlineStandardElement         |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting data standards                        | DAYU_DS       | dsStandardElement       | deleteStandardElement          |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying logical entities or physical tables   | DAYU_DS       | dsTableModel            | getListTableModel              |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating logical entities or physical tables   | DAYU_DS       | dsTableModel            | createTableModel               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating logical entities or physical tables   | DAYU_DS       | dsTableModel            | updateTableModel               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing logical entities or physical tables | DAYU_DS       | dsTableModel            | publishedTableModel            |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending logical entities or physical tables | DAYU_DS       | dsTableModel            | offlineTableModel              |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting logical entities or physical tables   | DAYU_DS       | dsTableModel            | deleteTableModel               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying dimensions                            | DAYU_DS       | dsDimension             | getListDimension               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating dimensions                            | DAYU_DS       | dsDimension             | createDimension                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating dimensions                            | DAYU_DS       | dsDimension             | updateDimension                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing dimensions                          | DAYU_DS       | dsDimension             | publishedDimension             |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending dimensions                          | DAYU_DS       | dsDimension             | offlineDimension               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting dimensions                            | DAYU_DS       | dsDimension             | deleteDimension                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying dimension tables                      | DAYU_DS       | dsDimensionLogicTable   | getListDimensionLogicTable     |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting dimension tables                      | DAYU_DS       | dsDimensionLogicTable   | deleteDimensionLogicTable      |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying fact tables                           | DAYU_DS       | dsFactLogicTable        | getListFactLogicTable          |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating fact tables                           | DAYU_DS       | dsFactLogicTable        | createFactLogicTable           |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating fact tables                           | DAYU_DS       | dsFactLogicTable        | updateFactLogicTable           |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing fact tables                         | DAYU_DS       | dsFactLogicTable        | publishedFactLogicTable        |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending fact tables                         | DAYU_DS       | dsFactLogicTable        | offlineFactLogicTable          |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting fact tables                           | DAYU_DS       | dsFactLogicTable        | deleteFactLogicTable           |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying summary tables                        | DAYU_DS       | dsAggregationLogicTable | getListAggregationLogicTable   |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating summary tables                        | DAYU_DS       | dsAggregationLogicTable | createAggregationLogicTable    |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating summary tables                        | DAYU_DS       | dsAggregationLogicTable | updateAggregationLogicTable    |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing summary tables                      | DAYU_DS       | dsAggregationLogicTable | publishedAggregationLogicTable |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending summary tables                      | DAYU_DS       | dsAggregationLogicTable | offlineAggregationLogicTable   |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting summary tables                        | DAYU_DS       | dsAggregationLogicTable | deleteAggregationLogicTable    |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying business metrics                      | DAYU_DS       | dsBizMetric             | getListBizMetric               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating business metrics                      | DAYU_DS       | dsBizMetric             | createBizMetric                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating business metrics                      | DAYU_DS       | dsBizMetric             | updateBizMetric                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing business metrics                    | DAYU_DS       | dsBizMetric             | publishedBizMetric             |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending business metrics                    | DAYU_DS       | dsBizMetric             | offlineBizMetric               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting business metrics                      | DAYU_DS       | dsBizMetric             | deleteBizMetric                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying atomic metrics                        | DAYU_DS       | dsAtomicIndex           | getListAtomicIndex             |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating atomic metrics                        | DAYU_DS       | dsAtomicIndex           | createAtomicIndex              |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating atomic metrics                        | DAYU_DS       | dsAtomicIndex           | updateAtomicIndex              |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing atomic metrics                      | DAYU_DS       | dsAtomicIndex           | publishedAtomicIndex           |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending atomic metrics                      | DAYU_DS       | dsAtomicIndex           | offlineAtomicIndex             |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting atomic metrics                        | DAYU_DS       | dsAtomicIndex           | deleteAtomicIndex              |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying derivative metrics                    | DAYU_DS       | dsDerivativeIndex       | getListDerivativeIndex         |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating derivative metrics                    | DAYU_DS       | dsDerivativeIndex       | createDerivativeIndex          |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating derivative metrics                    | DAYU_DS       | dsDerivativeIndex       | updateDerivativeIndex          |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting derivative metrics                    | DAYU_DS       | dsDerivativeIndex       | deleteDerivativeIndex          |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing derivative metrics                  | DAYU_DS       | dsDerivativeIndex       | publishedDerivativeIndex       |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending derivative metrics                  | DAYU_DS       | dsDerivativeIndex       | offlineDerivativeIndex         |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying compound metrics                      | DAYU_DS       | dsCompoundMetric        | getListCompoundMetric          |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating compound metrics                      | DAYU_DS       | dsCompoundMetric        | createCompoundMetric           |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating compound metrics                      | DAYU_DS       | dsCompoundMetric        | updateCompoundMetric           |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting compound metrics                      | DAYU_DS       | dsCompoundMetric        | deleteCompoundMetric           |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing compound metrics                    | DAYU_DS       | dsCompoundMetric        | publishedCompoundMetric        |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending compound metrics                    | DAYU_DS       | dsCompoundMetric        | offlineCompoundMetric          |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying time filters                          | DAYU_DS       | dsTimeCondition         | getListTimeCondition           |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating time filters                          | DAYU_DS       | dsTimeCondition         | createTimeCondition            |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating time filters                          | DAYU_DS       | dsTimeCondition         | updateTimeCondition            |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Publishing time filters                        | DAYU_DS       | dsTimeCondition         | publishedTimeCondition         |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Suspending time filters                        | DAYU_DS       | dsTimeCondition         | offlineTimeCondition           |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting time filters                          | DAYU_DS       | dsTimeCondition         | deleteTimeCondition            |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying directories                           | DAYU_DS       | dsDirectory             | getListDirectory               |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating directories                           | DAYU_DS       | dsDirectory             | createDirectory                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating directories                           | DAYU_DS       | dsDirectory             | updateDirectory                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting directories                           | DAYU_DS       | dsDirectory             | deleteDirectory                |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Querying models                                | DAYU_DS       | dsModel                 | getListModel                   |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Creating models                                | DAYU_DS       | dsModel                 | createModel                    |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Updating models                                | DAYU_DS       | dsModel                 | updateModel                    |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
   | Deleting models                                | DAYU_DS       | dsModel                 | deleteModel                    |
   +------------------------------------------------+---------------+-------------------------+--------------------------------+
