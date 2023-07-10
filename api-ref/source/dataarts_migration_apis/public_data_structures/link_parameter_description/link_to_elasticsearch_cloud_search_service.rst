:original_name: dataartsstudio_02_0276.html

.. _dataartsstudio_02_0276:

Link to Elasticsearch/Cloud Search Service
==========================================

Description
-----------

By creating an Elasticsearch link, you can extract data from or load data to the Elasticsearch server or Cloud Search Service.

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
                   "name": "linkConfig.host",
                   "value": "192.168.0.50:9200;192.168.0.62:9200"
                 },
                 {
                   "name": "linkConfig.safemode",
                   "value": "true"
                 },
                 {
                   "name": "linkConfig.user",
                   "value": "admin"
                 },
                 {
                   "name": "linkConfig.password",
                   "value": "Add password here."
                 },
                 {
                   "name": "linkConfig.linkType",
                   "value": "CSS"
                 }
               ],
               "name": "linkConfig"
             }
           ],
           "extended-configs": {
             "name": "linkConfig.extendedFields",
             "value": "eyLodHRwc0FjY2VzcyI6InRydWUifQ=="
           }
         },
         "name": "css-cdm-autotest-nodel",
         "connector-name": "elasticsearch-connector"
       }
     ]
   }

Link Parameters
---------------

+---------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter           | Mandatory | Type    | Description                                                                                                                                                                                              |
+=====================+===========+=========+==========================================================================================================================================================================================================+
| linkConfig.host     | Yes       | String  | List of one or more Elasticsearch servers, including the port number. The format is *ip:port*. Use semicolons (;) to separate multiple IP addresses. For example, **192.168.0.1:9200;192.168.0.2:9200**. |
+---------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.safemode | No        | Boolean | If you select the security authentication mode, you must enter the username and password, and choose whether to enable HTTPS access.                                                                     |
+---------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.user     | No        | String  | For Elasticsearch that supports username and password authentication, configure the username and password when creating a link.                                                                          |
+---------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.password | No        | String  | Password for accessing the Elasticsearch server                                                                                                                                                          |
+---------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.linkType | Yes       | String  | Link type, which is used to distinguish the Elasticsearch link from the Cloud Search Service link                                                                                                        |
+---------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
