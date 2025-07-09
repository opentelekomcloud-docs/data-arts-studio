:original_name: dataartsstudio_01_0581.html

.. _dataartsstudio_01_0581:

Obtaining the Return Value of a Rest Client Node
================================================

The Rest Client node can execute RESTful requests.

This tutorial describes how to obtain the return value of the Rest Client node, covering the following two application scenarios:

-  :ref:`Obtaining the Return Value Through Parameter "The response message body parses the transfer parameter" <dataartsstudio_01_0581__en-us_topic_0000001116272948_section16953144113278>`
-  :ref:`Obtaining the Return Value Using an EL Expression <dataartsstudio_01_0581__en-us_topic_0000001116272948_section1886792313411>`

.. _dataartsstudio_01_0581__en-us_topic_0000001116272948_section16953144113278:

Obtaining the Return Value Through Parameter "The response message body parses the transfer parameter"
------------------------------------------------------------------------------------------------------

As shown in :ref:`Figure 1 <dataartsstudio_01_0581__fig172611511282>`, the first Rest Client node invokes the API of MRS to query the cluster list. :ref:`Figure 2 <dataartsstudio_01_0581__en-us_topic_0000001116272948_fig082225015325>` shows the JSON message body returned by the API.

-  Scenario: The ID of the first cluster in the cluster list needs to be obtained and transferred to other nodes as a parameter.
-  Key configurations: Set **The response message body parses the transfer parameter** of the first Rest Client to **clusterId=clusters[0].clusterId**. Other Rest Client nodes can reference the ID of the first cluster in ${clusterId} mode.

   .. note::

      When setting **The response message body parses the transfer parameter**, ensure that the transferred parameter name (for example, **clusterId**) is unique among all node parameters of the job.

.. _dataartsstudio_01_0581__fig172611511282:

.. figure:: /_static/images/en-us_image_0000002270791064.png
   :alt: **Figure 1** Rest Client job example 1

   **Figure 1** Rest Client job example 1

.. _dataartsstudio_01_0581__en-us_topic_0000001116272948_fig082225015325:

.. figure:: /_static/images/en-us_image_0000002305440869.png
   :alt: **Figure 2** JSON message body

   **Figure 2** JSON message body

.. _dataartsstudio_01_0581__en-us_topic_0000001116272948_section1886792313411:

Obtaining the Return Value Using an EL Expression
-------------------------------------------------

The Rest Client node can be used together with EL expressions. You can select different EL expressions based on scenarios. This section describes how to develop your own jobs based on your service requirements.

As shown in :ref:`Figure 3 <dataartsstudio_01_0581__en-us_topic_0000001116272948_fig474512269340>`, the Rest Client invokes the API of MRS to query the cluster list and then invokes the Kafka Client to send a message.

-  Scenario: The Kafka Client sends a character string message. The message content is the ID of the first cluster in the cluster list.
-  Key configurations: When you configure the Kafka Client, use the following EL expression to obtain a specific field in the message body returned by the REST API: **#{JSONUtil.toString(JSONUtil.path(Job.getNodeOutput("Rest_Client_4901"),"clusters[0].clusterId"))}**

.. _dataartsstudio_01_0581__en-us_topic_0000001116272948_fig474512269340:

.. figure:: /_static/images/en-us_image_0000002305440865.png
   :alt: **Figure 3** Rest Client job example 2

   **Figure 3** Rest Client job example 2
