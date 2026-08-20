:original_name: PostQualityResourceUpload.html

.. _PostQualityResourceUpload:

Uploading a Resource File
=========================

Function
--------

This API is used to import a file to DataArts Quality.

Calling Method
--------------

For details, see :ref:`Calling APIs <making_request>`.

URI
---

POST /v2/{project_id}/quality/resource/upload

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                             |
   +============+===========+========+=========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                       |
   +==============+===========+========+===================================================================================================================================================+
   | workspace    | Yes       | String | DataArts Studio workspace ID. For details about how to obtain the workspace ID, see :ref:`Instance ID and Workspace ID <dataartsstudio_02_0350>`. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | IAM token. For details about how to obtain the token, see :ref:`Authentication <dataartsstudio_02_0010>`.                                         |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** FormData parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                             |
   +===========+===========+========+=========================================================================================================+
   | type      | Yes       | String | Type of the resource to be uploaded. The value can be rule-template, quality-task, or consistency-task. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | file      | Yes       | File   | Resource file to be uploaded.                                                                           |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +----------------+-----------------------------------------------------------------------------------------------+---------------------------------+
   | Parameter      | Type                                                                                          | Description                     |
   +================+===============================================================================================+=================================+
   | resource_id    | String                                                                                        | Resource ID                     |
   +----------------+-----------------------------------------------------------------------------------------------+---------------------------------+
   | topics         | Array of strings                                                                              | SMN topic                       |
   +----------------+-----------------------------------------------------------------------------------------------+---------------------------------+
   | matched_topics | Array of :ref:`MatchedTopicMsg <postqualityresourceupload__response_matchedtopicmsg>` objects | Matched topics                  |
   +----------------+-----------------------------------------------------------------------------------------------+---------------------------------+
   | directories    | Array of strings                                                                              | Directories in DataArts Quality |
   +----------------+-----------------------------------------------------------------------------------------------+---------------------------------+
   | queues         | Array of strings                                                                              | Queue name                      |
   +----------------+-----------------------------------------------------------------------------------------------+---------------------------------+
   | connections    | Array of :ref:`NameType <postqualityresourceupload__response_nametype>` objects               | Data connection information     |
   +----------------+-----------------------------------------------------------------------------------------------+---------------------------------+

.. _postqualityresourceupload__response_matchedtopicmsg:

.. table:: **Table 5** MatchedTopicMsg

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   id        String Topic ID
   name      String Topic name
   ========= ====== ===========

.. _postqualityresourceupload__response_nametype:

.. table:: **Table 6** NameType

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   name      String Name
   type      String Type
   ========= ====== ===========

**Status code: 500**

.. table:: **Table 7** Response body parameters

   +------------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                                       |
   +============+========+===================================================================================================+
   | error_code | String | Error code, for example, **DQC.0000** which indicates that the request was successfully processed |
   +------------+--------+---------------------------------------------------------------------------------------------------+
   | error_msg  | String | Error message                                                                                     |
   +------------+--------+---------------------------------------------------------------------------------------------------+

Example Requests
----------------

None

Example Responses
-----------------

None

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         Success
500         INTERNAL SERVER ERROR
=========== =====================
