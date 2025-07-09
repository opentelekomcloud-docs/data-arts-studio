:original_name: dataartsstudio_03_0618.html

.. _dataartsstudio_03_0618:

What Should I Do If a Shell/Python Node Fails and Error "session is down" Is Reported?
======================================================================================

This section uses the Shell node as an example.

Symptom
-------

The Shell node fails to be executed, but the Shell script is executed successfully.

Possible Causes
---------------

#. Obtain the run logs of the Shell node.

   .. code-block::

      [2021/11/17 02:00:36 GMT+0800] [INFO] No job-level agency is set, Workspace-level agency is dlg_agency, Execute job use agency dlg_agency, job id is 07572F197E4642E5BE549C2B656F157Ctm7cHkHd
      [2021/11/17 02:00:36 GMT+0800] [DEBUG] ===============================================
      [2021/11/17 02:00:36 GMT+0800] [INFO] Get response from agent when try to submit shell running job :
      [2021/11/17 02:00:36 GMT+0800] [INFO]
      {
      "jobResultList":[
      {
      "jobId":"a567f7f5-3c9e-4dfc-a464-bd477ac5b1ea",
      "status":"created",
      "errorCode":0,
      "failCount":0,
      "result":[

      ]
      }
      ],
      "agentId":"614853ee-c1c6-456d-9aa6-fc84ad1281ed"
      }
      [2021/11/17 02:00:36 GMT+0800] [DEBUG] ===============================================
      [2021/11/17 02:05:56 GMT+0800] [DEBUG] ===============================================
      [2021/11/17 02:05:56 GMT+0800] [INFO] Job Run finish , the raw output is :
      [2021/11/17 02:05:56 GMT+0800] [INFO]
      {
      "jobId":"a567f7f5-3c9e-4dfc-a464-bd477ac5b1ea",
      "status":"failed",
      "errorCode":3427,
      "errorMessage":"Shell script job execute failed.",
      "failCount":0,
      "result":[
      {
      "is_success":false,
      "exeTime":300.609
      }
      ]
      }
      [2021/11/17 02:05:56 GMT+0800] [DEBUG] ===============================================
      [2021/11/17 02:05:56 GMT+0800] [DEBUG] ===============================================
      [2021/11/17 02:05:56 GMT+0800] [INFO] The return code is : [-1].
      [2021/11/17 02:05:56 GMT+0800] [DEBUG] ===============================================
      [2021/11/17 02:05:56 GMT+0800] [INFO] Execute shell script job finished.
      [2021/11/17 02:05:56 GMT+0800] [ERROR] Shell exit code is not 0
      [2021/11/17 02:05:56 GMT+0800] [DEBUG] ===============================================
      [2021/11/17 02:05:56 GMT+0800] [ERROR] Shell script job execute failed. Please contact ECS Service.
      [2021/11/17 02:05:56 GMT+0800] [ERROR] Exception message: RuntimeException: Shell script job execute failed. Please contact ECS Service.
      [2021/11/17 02:05:56 GMT+0800] [ERROR] Root Cause message:RuntimeException: Shell script job execute failed. Please contact ECS Service.

#. Ensure that the values of the following parameters in the **sshd_config** file are as follows.

   |image1|

   Cause: The SSH session times out and is disconnected. As a result, the Shell node fails.

Solution
--------

#. Open the **/etc/ssh/sshd_config** file of the ECS and add or update the following parameter values:

   ClientAliveInterval 300

   ClientAliveCountMax 3

   .. note::

      The ClientAliveInterval parameter specifies the interval for the server to send requests to a client. The default value is **0**, indicating that the server does not send requests to the client. Value **300** indicates that the server sends a request every five minutes and the client sends a response accordingly. In this process, a persistent connection is maintained. The default value of **ClientAliveCountMax** is **3**. If the number of times that the client does not respond to requests sent by the server reaches the value of this parameters, the server disconnects the connection to the client. Normally, the client sends responses.

#. After the modification, restart the sshd of the ECS and run the following command:

   |image2|

#. Check whether sshd is started successfully. (The following figure shows that sshd is started successfully.)

   |image3|

.. |image1| image:: /_static/images/en-us_image_0000002270788936.png
.. |image2| image:: /_static/images/en-us_image_0000002270845798.png
.. |image3| image:: /_static/images/en-us_image_0000002305438737.png
