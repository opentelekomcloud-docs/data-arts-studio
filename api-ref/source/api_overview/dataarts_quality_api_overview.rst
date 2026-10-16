:original_name: apiOverview_DQC.html

.. _apiOverview_DQC:

DataArts Quality API Overview
=============================

.. table:: **Table 1** DataArts Quality API types

   +-------------------------------------------------------------------------+------------------------+
   | Type                                                                    | Description            |
   +=========================================================================+========================+
   | :ref:`Catalog <apioverview_dqc__section_tag_child_834396929653>`        | Catalog APIs           |
   +-------------------------------------------------------------------------+------------------------+
   | :ref:`Rule Template <apioverview_dqc__section_tag_child_844603095870>`  | Rule template APIs     |
   +-------------------------------------------------------------------------+------------------------+
   | :ref:`Quality Job <apioverview_dqc__section_tag_child_992797819342>`    | Quality job APIs       |
   +-------------------------------------------------------------------------+------------------------+
   | :ref:`Comparison Job <apioverview_dqc__section_tag_child_505643943826>` | Comparison job APIs    |
   +-------------------------------------------------------------------------+------------------------+
   | :ref:`O&M <apioverview_dqc__section_tag_child_750306783854>`            | O&M APIs               |
   +-------------------------------------------------------------------------+------------------------+
   | :ref:`Task Instance <apioverview_dqc__section_tag_child_198753084322>`  | Task instance APIs     |
   +-------------------------------------------------------------------------+------------------------+
   | :ref:`Quality Report <apioverview_dqc__section_tag_child_345366285529>` | Quality report APIs    |
   +-------------------------------------------------------------------------+------------------------+
   | :ref:`Import/Export <apioverview_dqc__section_tag_child_808277483906>`  | Import and export APIs |
   +-------------------------------------------------------------------------+------------------------+

.. _apioverview_dqc__section_tag_child_834396929653:

Directory
---------

.. table:: **Table 2** Directory

   +-------------------------------------------------+---------------------------------------------+
   | API                                             | Description                                 |
   +=================================================+=============================================+
   | :ref:`Obtaining Job Directories <listcategory>` | This API is used to obtain job directories. |
   +-------------------------------------------------+---------------------------------------------+

.. _apioverview_dqc__section_tag_child_844603095870:

Rule Template
-------------

.. table:: **Table 3** Rule template

   +----------------------------------------------------------------+------------------------------------------------------------+
   | API                                                            | Description                                                |
   +================================================================+============================================================+
   | :ref:`Obtaining the Rule Template List <listqualitytemplates>` | This API is used to obtain the rule template list.         |
   +----------------------------------------------------------------+------------------------------------------------------------+
   | :ref:`Creating a Rule Template <createtemplate>`               | This API is used to create a rule template.                |
   +----------------------------------------------------------------+------------------------------------------------------------+
   | :ref:`Obtaining Rule Template Details <showtemplatesdetail>`   | This API is used to obtain the details of a rule template. |
   +----------------------------------------------------------------+------------------------------------------------------------+
   | :ref:`Updating a Rule Template <updatetemplate>`               | This API is used to update a rule template.                |
   +----------------------------------------------------------------+------------------------------------------------------------+
   | :ref:`Deleting Rule Templates <batchdeletetemplates>`          | This API is used to delete rule templates.                 |
   +----------------------------------------------------------------+------------------------------------------------------------+

.. _apioverview_dqc__section_tag_child_992797819342:

Quality Job
-----------

.. table:: **Table 4** Quality job

   +-------------------------------------------------------------------+----------------------------------------------------------+
   | API                                                               | Description                                              |
   +===================================================================+==========================================================+
   | :ref:`Obtaining the Quality Job List (V1) <listqualitytasklists>` | This API is used to obtain quality jobs.                 |
   +-------------------------------------------------------------------+----------------------------------------------------------+
   | :ref:`Obtaining the Quality Job List <listqualitytask>`           | This API is used to obtain the list of quality jobs.     |
   +-------------------------------------------------------------------+----------------------------------------------------------+
   | :ref:`Obtaining Quality Job Details <showqualitytaskdetail>`      | This API is used to obtain the details of a quality job. |
   +-------------------------------------------------------------------+----------------------------------------------------------+
   | :ref:`Deleting Quality Jobs <batchdeletequalityqualitytasks>`     | This API is used to delete quality jobs.                 |
   +-------------------------------------------------------------------+----------------------------------------------------------+

.. _apioverview_dqc__section_tag_child_505643943826:

Comparison Job
--------------

.. table:: **Table 5** Comparison job

   +----------------------------------------------------------------------+-------------------------------------------------------------+
   | API                                                                  | Description                                                 |
   +======================================================================+=============================================================+
   | :ref:`Obtaining the Comparison Job List <listconsistencytask>`       | This API is used to obtain the comparison job list.         |
   +----------------------------------------------------------------------+-------------------------------------------------------------+
   | :ref:`Obtaining Comparison Job Details <showconsistencytaskdetail>`  | This API is used to obtain the details of a comparison job. |
   +----------------------------------------------------------------------+-------------------------------------------------------------+
   | :ref:`Deleting Comparison Jobs <batchdeletequalityconsistencytasks>` | This API is used to delete comparison jobs.                 |
   +----------------------------------------------------------------------+-------------------------------------------------------------+

.. _apioverview_dqc__section_tag_child_750306783854:

O&M
---

.. table:: **Table 6** O&M

   +-----------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                   | Description                                                                                                                                          |
   +=======================================================================+======================================================================================================================================================+
   | :ref:`Obtaining the Task Execution Result List <listinstances>`       | This API is used to obtain the task execution result list.                                                                                           |
   +-----------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining the Instance Result <showinstanceresult>`             | This API is used to obtain the instance result.                                                                                                      |
   +-----------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Rectifying Issues of an Instance <updatequalityinstancerecord>` | This API is used to rectify issues of an instance. On the DataArts Quality console, you can click **More** and select **Rectify** to rectify issues. |
   +-----------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _apioverview_dqc__section_tag_child_198753084322:

Task Instance
-------------

.. table:: **Table 7** Task instance

   +-------------------------------------------------------+-----------------------------------------+
   | API                                                   | Description                             |
   +=======================================================+=========================================+
   | :ref:`Stopping Instances <batchstopqualityinstances>` | This API is used to stop job instances. |
   +-------------------------------------------------------+-----------------------------------------+

.. _apioverview_dqc__section_tag_child_345366285529:

Quality Report
--------------

.. table:: **Table 8** Quality report

   +-------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | API                                                                                                   | Description                                                                     |
   +=======================================================================================================+=================================================================================+
   | :ref:`Obtaining a Quality Report Scoring System <getqualityreportscoring>`                            | This API is used to obtain a quality report scoring system.                     |
   +-------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | :ref:`Obtaining the Quality Report Overview <getqualityreportoverview>`                               | This API is used to obtain the quality report overview.                         |
   +-------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | :ref:`Obtaining the Quality Report Trend <getqualityreporttrend>`                                     | This API is used to obtain the quality report trend.                            |
   +-------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | :ref:`Obtaining the Quality Report Rule Score <getqualityreportrules>`                                | This API is used to obtain the score of a quality report rule.                  |
   +-------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | :ref:`Obtaining the Score of a Sub-rule Field in the Quality Report <getqualityreportsubruleresults>` | This API is used to obtain the score of a sub-rule field in the quality report. |
   +-------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | :ref:`Obtaining Technical Report Data <getqualityreporttechnologyscores>`                             | This API is used to obtain technical report data.                               |
   +-------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | :ref:`Obtaining Business Report Data <getqualityreportbusinessscores>`                                | This API is used to obtain business report data.                                |
   +-------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+

.. _apioverview_dqc__section_tag_child_808277483906:

Import and Export
-----------------

.. table:: **Table 9** Import and export

   +---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | API                                                                             | Description                                                                                           |
   +=================================================================================+=======================================================================================================+
   | :ref:`Exporting Resources <postqualityresourceexport>`                          | This API is used to export resources from DataArts Quality, such as quality jobs and comparison jobs. |
   +---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining the Status of an Import/Export Task <getqualityresourcestatus>` | This API is used to obtain the status of an export or import task.                                    |
   +---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | :ref:`Downloading a Resource File <getqualityresourcedownload>`                 | This API is used to download a resource file.                                                         |
   +---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | :ref:`Uploading a Resource File <postqualityresourceupload>`                    | This API is used to import a file to DataArts Quality.                                                |
   +---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | :ref:`Importing Resources <postqualityresourceimport>`                          | This API is used to import resources to DataArts Quality.                                             |
   +---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
