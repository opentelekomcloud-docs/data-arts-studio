:original_name: dataartsstudio_02_0013.html

.. _dataartsstudio_02_0013:

Example of Using DataArts Migration APIs
========================================

This section describes how to use cURL to call CDM APIs to migrate data from a local MySQL database to DWS in the cloud.

#. :ref:`Obtaining a Token <dataartsstudio_02_0013__en-us_topic_0000001716156281_en-us_topic_0108272822_s80117f7397924f1eaaa579614623e6ba>`

   Call the API to obtain the user token, which will be put into the request header for authentication in a subsequent request.

#. :ref:`Creating a CDM Cluster <dataartsstudio_02_0013__en-us_topic_0000001716156281_en-us_topic_0108272822_section858213116488>`

   -  If you have created a CDM cluster, skip this step and directly use the ID of the created cluster.
   -  If you want to use a new cluster for migration, call the API in :ref:`Creating a Cluster <createcluster_0>` to create a CDM cluster.

#. :ref:`Creating Links <dataartsstudio_02_0013__en-us_topic_0000001716156281_en-us_topic_0108272822_section1543119195119>`

   Call the API in :ref:`Creating a Link <createlink_0>` to create the MySQL and DWS links.

#. :ref:`Creating a Migration Job <dataartsstudio_02_0013__en-us_topic_0000001716156281_en-us_topic_0108272822_section07183115314>`

   Call the API in :ref:`Creating a Job in a Specified Cluster <createjob_0>` to create a job for migrating data from MySQL to DWS.

#. :ref:`Viewing Job Result <dataartsstudio_02_0013__en-us_topic_0000001716156281_en-us_topic_0108272822_section179778188581>`

   Call the API in :ref:`Starting a Job <startjob_0>` to execute the job.

Preparing Data
--------------

Before calling an API, prepare the following data.

.. table:: **Table 1** Preparing data

   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | Item                | Name              | Description                                                                                                                                                                                                                                     | Example                              |
   +=====================+===================+=================================================================================================================================================================================================================================================+======================================+
   | Account information | Project name      | Name of the project where CDM resides                                                                                                                                                                                                           | Project Name                         |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Project ID        | ID of the project where CDM resides                                                                                                                                                                                                             | 1551c7f6c808414d8e9f3c514a170f2e     |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Account name      | Name of an enterprise account to which a user belongs                                                                                                                                                                                           | Account Name                         |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Username          | Username for using a cloud service. The user must have operation permissions on CDM.                                                                                                                                                            | Username                             |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Password          | User password                                                                                                                                                                                                                                   | password                             |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | VPC information     | VPC ID            | The VPC where CDM resides must be the same as that of DWS.                                                                                                                                                                                      | 6b47302a-bf79-4b20-bf7a-80987408e196 |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Subnet ID         | The subnet where CDM resides must be the same as that of DWS.                                                                                                                                                                                   | 63bdc3cb-a4e7-486f-82ee-d9bf208c8f8c |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Security group ID | The security group where CDM resides must be the same as that of DWS.                                                                                                                                                                           | 005af77a-cce5-45ac-99c7-2ea50ea8addf |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | Endpoint            | IAM endpoint      | An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. You can obtain endpoints from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                | iam_endpoint                         |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | CDM endpoint      | An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. You can obtain endpoints of the service from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__. | cdm_endpoint                         |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | MySQL database      | IP address        | IP address of the local MySQL database, which allows CDM to access the MySQL database using a public IP address                                                                                                                                 | 1xx.120.85.24                        |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Port              | MySQL database port                                                                                                                                                                                                                             | 3306                                 |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Database name     | Name of the MySQL database from which data is to be exported                                                                                                                                                                                    | DB_name                              |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Username          | Username for accessing the MySQL database. The user must have the read, write, and delete permissions on the MySQL database.                                                                                                                    | username                             |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Password          | Password for accessing the MySQL database                                                                                                                                                                                                       | DB_password                          |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | DWS database        | IP address        | IP address of the DWS database. CDM can access the IP address through the internal network.                                                                                                                                                     | 10.120.85.24                         |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Port              | DWS database port                                                                                                                                                                                                                               | 3306                                 |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Database name     | Name of the DWS database to which data is written                                                                                                                                                                                               | DWS                                  |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Username          | Username for accessing the DWS database. The user must have the read, write, and delete permissions on the DWS database.                                                                                                                        | user_dws                             |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   |                     | Password          | Password for accessing the DWS database                                                                                                                                                                                                         | dws_password                         |
   +---------------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+

.. _dataartsstudio_02_0013__en-us_topic_0000001716156281_en-us_topic_0108272822_s80117f7397924f1eaaa579614623e6ba:

Obtaining a Token
-----------------

#. Before calling other APIs, obtain the token and set it as an environment variable.

   .. code-block::

      curl -H "Content-Type:application/json" https://{iam_endpoint}/v3/auth/tokens -X POST -d '
      {
          "auth": {
              "identity": {
                  "methods": [
                      "password"
                  ],
                  "password": {
                      "user": {
                          "name": "Username",
                          "password": "password",
                          "domain": {
                              "name": "Account Name"
                          }
                      }
                  }
              },
              "scope": {
                  "project": {
                      "id": "1551c7f6c808414d8e9f3c514a170f2e"
                  }
              }
          }
      }
      ' -v -k

   The value of **X-Subject-Token** in the response header is the token.

   .. code-block::

      X-Subject-Token:MIIDkgYJKoZIhvcNAQcCoIIDgzCCA38CAQExDTALBglghkgBZQMEAgEwgXXXXX...

#. Run the following command to set the token as an environment variable for future use:

   .. code-block::

      export Token = MIIDkgYJKoZIhvcNAQcCoIIDgzCCA38CAQExDTALBglghkgBZQMEAgEwgXXXXX...

.. _dataartsstudio_02_0013__en-us_topic_0000001716156281_en-us_topic_0108272822_section858213116488:

Creating a CDM Cluster
----------------------

#. Call the API in :ref:`Creating a Cluster <createcluster_0>` to create a cluster. The following values are examples:

   -  Cluster name: **cdm-ab82**
   -  Cluster flavor: **cdm.medium**
   -  The VPC, subnet, and security group are the same as those of DWS, and the EIP is automatically bound.

   If status code **200** is returned, the cluster is successfully created.

   .. code-block::

      curl -X POST -H 'Content-Type:application/json;charset=utf-8' -H "X-Auth-Token:$Token" -d '
      {
        "cluster": {
          "name": "cdm-ab82",
          "vpcId": "6b47302a-bf79-4b20-bf7a-80987408e196",
          "instances": [{
                  "flavorRef": "fb8fe666-6734-4b11-bc6c-43d11db3c745",
                  "nics": [{
                      "net-id": "63bdc3cb-a4e7-486f-82ee-d9bf208c8f8c",
                      "securityGroupId": "005af77a-cce5-45ac-99c7-2ea50ea8addf"
                  }],
                  "availability_zone": "Project Name",
                  "type": "cdm"
              }],
          "datastore": {
                  "version": "1.8.5",
                  "type": "cdm"
              },
          "isScheduleBootOff": false,
          "scheduleBootTime": "null",
          "scheduleOffTime": "null",
          "isAutoOff": false,
          "sys_tags": [{
                  "key": "_sys_enterprise_project_id",
                  "value": "1ce45885-4033-40d2-bdde-d4dbaceb387d"
              }]
          },
        "autoRemind": false,
        "phoneNum": "null",
        "email": "null"
      }'
      https://{cdm_endpoint}/v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters -v -k

#. Call the API in :ref:`Querying the Cluster List <listclusters_0>` to query cluster information, obtain the cluster ID, and set the cluster ID to a global variable.

   .. code-block::

      curl -X GET -H 'Content-Type:application/json;charset=utf-8' -H "X-Auth-Token:$Token" https://{cdm_endpoint}/v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters -k -v

   The response is as follows:

   .. code-block::

      {
        "clusters": [{
          "version": "x.x.x",
          "updated": "2018-09-05T08:38:25",
          "name": "cdm-ab82",
          "created": "2018-09-05T08:38:25",
          "id": "bae65496-643e-47ca-84af-948672de7eeb",
          "status": "200",
          "isFrozen": "0",
          "statusDetail": "Normal",
          "actionProgress": {},
          "config_status": "In-Sync"
        }]
      }

   If the value of **status** is **200**, the cluster is successfully created. The cluster ID is **bae65496-643e-47ca-84af-948672de7eeb**.

#. Run the following command to set the cluster ID to a global variable for future use:

   .. code-block::

      export ID = bae65496-643e-47ca-84af-948672de7eeb

.. _dataartsstudio_02_0013__en-us_topic_0000001716156281_en-us_topic_0108272822_section1543119195119:

Creating Links
--------------

#. Call the API in :ref:`Creating a Link <createlink_0>` to create the MySQL link **mysql_link**. The following values are examples:

   -  IP address: **1**\ *xx*\ **.120.85.24**
   -  Port number: **3306**
   -  Database name: **DB\_**\ *name*
   -  Login username: *username*
   -  Password: **DB\_**\ *password*

   If status code **200** is returned, the link is successfully created.

   .. code-block::

      curl -X POST -H "Content-Type:application/json" -H "X-Auth-Token:$Token" -d '{
        "links": [{
          "enabled": true,
          "update-user": null,
          "name": "mysql_link",
          "link-config-values": {
            "configs": [
                          {
                              "name": "linkConfig",
                              "inputs": [
                                  {
                                      "name": "linkConfig.databaseType",
                                      "value": "MYSQL"
                                  },
                                  {
                                      "name": "linkConfig.host",
                                      "value": "1xx.120.85.24"
                                  },
                                  {
                                      "name": "linkConfig.port",
                                      "value": "3306"
                                  },
                                  {
                                      "name": "linkConfig.database",
                                      "value": "DB_name"
                                  },
                                  {
                                      "name": "linkConfig.username",
                                      "value": "username"
                                  },
                                  {
                                      "name": "linkConfig.password",
                                      "value": "DB_password"
                                  },
                                  {
                                      "name": "linkConfig.fetchSize",
                                      "value": "100000"
                                  },
                                  {
                                      "name": "linkConfig.usingNative",
                                      "value": "true"
                                  }
                              ]
                          }
                      ]
          },
          "connector-name": "generic-jdbc-connector",
          "creation-date": 1536654788622,
          "update-date": 1536654788622,
          "creation-user": null
        }]
      }'
      https://{cdm_endpoint}/v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/bae65496-643e-47ca-84af-948672de7eeb/cdm/link -k -v

#. Call the API in :ref:`Creating a Link <createlink_0>` to create the DWS link **dws_link**. The following values are examples:

   -  IP address of the database: **10.120.85.24**
   -  Port number: **3306**
   -  Database name: **DWS**
   -  Login username: **user_dws**
   -  Password: **dws_password**

   .. code-block::

      curl -X POST -H "Content-Type:application/json" -H "X-Auth-Token:$Token" -d '{
        "links": [{
          "enabled": true,
          "update-user": null,
          "name": "dws_link",
          "link-config-values": {
            "configs": [
                          {
                              "name": "linkConfig",
                              "inputs": [
                                  {
                                      "name": "linkConfig.databaseType",
                                      "value": "DWS"
                                  },
                                  {
                                      "name": "linkConfig.host",
                                      "value": "10.120.85.24"
                                  },
                                  {
                                      "name": "linkConfig.port",
                                      "value": "3306"
                                  },
                                  {
                                      "name": "linkConfig.database",
                                      "value": "DWS"
                                  },
                                  {
                                      "name": "linkConfig.username",
                                      "value": "user_dws"
                                  },
                                  {
                                      "name": "linkConfig.password",
                                      "value": "dws_password"
                                  },
                                  {
                                      "name": "linkConfig.fetchSize",
                                      "value": "100000"
                                  },
                                  {
                                      "name": "linkConfig.usingNative",
                                      "value": "true"
                                  }
                              ]
                          }
                      ]
          },
          "connector-name": "generic-jdbc-connector",
          "creation-date": 1536654788622,
          "update-date": 1536654788622,
          "creation-user": null
        }]
      }'
      https://{cdm_endpoint}/v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/bae65496-643e-47ca-84af-948672de7eeb/cdm/link -k -v

.. _dataartsstudio_02_0013__en-us_topic_0000001716156281_en-us_topic_0108272822_section07183115314:

Creating a Migration Job
------------------------

#. After the links are created, call the API in :ref:`Creating a Job in a Specified Cluster <createjob_0>` to create a migration job. The following is a sample job:

   -  The job name is **mysql2dws**.
   -  The name of the MySQL database from which data is exported is **default**, and the name of the exported table is **mysql_tbl**. The job is split into multiple tasks by **id** and the tasks are executed concurrently.
   -  The name of the database on DWS to which the data is imported is **public**, and the table name is **cdm_all_type**. Do not clear the data in the table before import.
   -  If no table in the local MySQL database exists in the database on DWS, CDM automatically creates the table on DWS.
   -  The field list loaded to DWS is **id&gid&name**.
   -  When the job extracts data, three extractors are concurrently executed.

   If status code **200** is returned, the job is successfully created.

   .. code-block::

      curl -X POST -H "Content-Type:application/json" -H "X-Cluster-ID:$ID" -H "X-Auth-Token:$Token" -d '{
        "jobs": [{
          "job_type": "NORMAL_JOB",
          "name": "mysql2dws",
          "from-link-name": "mysql_link",
          "from-connector-name": "generic-jdbc-connector",
          "to-link-name": "dws_link",
          "to-connector-name": "generic-jdbc-connector",
          "from-config-values": {
            "configs": [{
              "name": "fromJobConfig",
              "inputs": [{
                "name": "fromJobConfig.schemaName",
                "value": "default"
              },
              {
                "name": "fromJobConfig.tableName",
                "value": "mysql_tbl"
              },
              {
                "name": "fromJobConfig.partitionColumn",
                "value": "id"
              }]
            }]
          },
      "to-config-values": {
                   "configs": [
                       {
                           "inputs": [
                               {
                                   "name": "toJobConfig.schemaName",
                                   "value": "public"
                               },
                               {
                                   "name": "toJobConfig.tablePreparation",
                                   "value": "CREATE_WHEN_NOT_EXIST"
                               },
                               {
                                   "name": "toJobConfig.tableName",
                                   "value": "cdm_all_type"
                               },
                               {
                                   "name": "toJobConfig.columnList",
                                   "value": "id&gid&name"
                               },
                               {
                                   "name": "toJobConfig.shouldClearTable",
                                   "value": "false"
                               }
                           ],
                           "name": "toJobConfig"
                       }
                   ]
               },
          "driver-config-values": {
            "configs": [{
              "name": "throttlingConfig",
              "inputs": [{
                "name": "throttlingConfig.numExtractors",
                "value": "3"
              }]
            }]
          }
        }]
      }' https://{cdm_endpoint}/v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/bae65496-643e-47ca-84af-948672de7eeb/cdm/job -k -v

#. Call the API in :ref:`Starting a Job <startjob_0>` to execute the job.

   .. code-block::

      curl -X GET -H 'Content-Type:application/json;charset=utf-8' -H "X-Cluster-ID:$ID" -H "X-Auth-Token:$Token" https://{cdm_endpoint}/v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/bae65496-643e-47ca-84af-948672de7eeb/cdm/job/mysql2dws/start -k -v

   The response is as follows:

   .. code-block::

      {
        "submissions": [{
          "progress": 1,
          "job-name": "mysql2dws",
          "status": "BOOTING",
          "creation-date": 1536654788622,
          "creation-user": "cdm"
        }]
      }

.. _dataartsstudio_02_0013__en-us_topic_0000001716156281_en-us_topic_0108272822_section179778188581:

Viewing Job Result
------------------

#. Call the API in :ref:`Querying Job Status <showjobstatus_0>` to query the job status.

   .. code-block::

      curl -X GET -H 'Content-Type:application/json;charset=utf-8' -H "X-Cluster-ID:$ID" -H "X-Auth-Token:$Token" https://{cdm_endpoint}/v1.1/1551c7f6c808414d8e9f3c514a170f2e/clusters/6ec9a0a4-76be-4262-8697-e7af1fac7920/cdm/job/mysql2dws/status -k -v

#. View the job execution result. The response to successful job execution is as follows:

   .. code-block::

      {
        "submissions": [{
          "progress": 0,
          "job-name": "mysql2dws",
          "status": "SUCCEEDED",
          "creation-date": 1536654788622,
          "creation-user": "cdm",
          "isStopingIncrement": "",
          "last-update-date": 1536654888622,
          "is-execute-auto": false,
          "last-update-user": "cdm",
          "isDeleteJob": false,
          "isIncrementing": false,
          "external-id": "job_local1127970451_0009",
          "counters": {
            "org.apache.sqoop.submission.counter.SqoopCounters": {
              "BYTES_WRITTEN": -1,
              "TOTAL_FILES": -1,
              "BYTES_READ": -1,
              "FILES_WRITTEN": -1,
              "TOTAL_SIZE": -1,
              "FILES_READ": -1,
              "ROWS_WRITTEN": 80,
              "ROWS_READ": 80
            }
          }
        }]
      }

   .. note::

      -  **BYTES_WRITTEN**: number of written bytes
      -  **BYTES_READ**: number of read bytes
      -  **TOTAL_FILES**: total number of files
      -  **FILES_WRITTEN**: number of written files
      -  **FILES_READ**: number of read files
      -  **ROWS_WRITTEN**: number of rows that are successfully written
      -  **ROWS_READ**: number of rows that are successfully read
