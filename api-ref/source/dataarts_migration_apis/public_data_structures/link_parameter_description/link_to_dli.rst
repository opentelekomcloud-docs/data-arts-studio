:original_name: dataartsstudio_02_0277.html

.. _dataartsstudio_02_0277:

Link to DLI
===========

Description
-----------

By creating a DLI link, you can import data to DLI. Currently, you cannot export data from DLI using CDM.

Sample Link
-----------

.. code-block::

   {
       "links": [
           {
               "link-config-values": {
                   "configs": [
                       {
                           "inputs": [
                               {
                                   "name": "linkConfig.ak",
                                   "value": "GRC2WR0IDC6NGROYLWU2"
                               },
                               {
                                   "name": "linkConfig.sk",
                                   "value": "Add password here"
                               },
                               {
                                   "name": "linkConfig.region",
                                   "value": ""
                               },
                               {
                                   "name": "linkConfig.projectId",
                                   "value": "c48475ce8e174a7a9f775706a3d5ebe2"
                               }
                           ],
                           "name": "linkConfig"
                       }
                   ]
               },
               "name": "dli",
               "connector-name": "dli-connector"
           }
       ]
   }

Link Parameters
---------------

==================== ========= ====== =================================
Parameter            Mandatory Type   Description
==================== ========= ====== =================================
linkConfig.ak        Yes       String AK for accessing the DLI database
linkConfig.sk        Yes       String SK for accessing the DLI database
linkConfig.region    Yes       String Region where DLI resides
linkConfig.projectId Yes       String Project ID of the DLI service
==================== ========= ====== =================================
