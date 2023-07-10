:original_name: dataartsstudio_01_0494.html

.. _dataartsstudio_01_0494:

Expression Overview
===================

Node parameter values in a DataArts Factory job can be dynamically generated based on the running environment by using Expression Language (EL). You can determine whether to execute this node based on the input parameters of the pipeline and the output of the upstream node. EL uses simple arithmetic and logic to calculate and references embedded objects, including job objects and tool objects.

Job object: provides properties and methods of obtaining the output message, job scheduling plan time, and job execution time of the previous node in a job.

Tool job: Provides methods of operating character strings, time, and JSON. For example, truncating a substring from a string or formatting time.

Syntax
------

Expression syntax:

.. code-block::

   #{expr}

In the preceding information, **expr** indicates an expression. **#** and **{}** are common operators used in EL, allowing you to access job properties using embedded objects.

**Example**
-----------

In the **URL** parameter of the Rest Client node, use expression **tableName=#{JSONUtil.path(Job.getNodeOutput("get_cluster"),"tables[0].table_name")}**.

Expression description:

#. **Job.getNodeOutput("get_cluster")** is used to obtain the execution result of the **get_cluster** node in the job. The execution result is a JSON character string.
#. **tables[0].table_name** is used to obtain the value of a field in the JSON character string.

Debugging Methods
-----------------

You can debug EL expressions using the following methods.

This section uses the #{DateUtil.now()} expression as an example.

#. Use the DIS Client node.

   -  Prerequisites: A DIS stream is available.

   -  Method: Select the DIS Client node, write the EL expression in the data to be sent, and click **Test**. Then right-click the node to view the log. The value of the EL expression is printed in the log.

      |image1|

      |image2|

#. Use the Kafka Client node.

   -  Prerequisites: An MRS cluster with the Kafka component is available.

   -  Method: Select the Kafka Client node, write the EL expression in the data to be sent, and click **Test**. Then right-click the node to view the log. The value of the EL expression is printed in the log.

      |image3|

      |image4|

#. Use the shell node.

   -  Prerequisites: An ECS is available.

   -  Method: Create a host connection, print the EL expression using echo, and click **Test**. Then view the log. The value of the EL expression is printed in the log.

      |image5|

      |image6|

#. Use the Create OBS node.

   If none of the preceding methods is available, use the Create OBS node and create an OBS path with the value of the EL expression as its name. You can click **Test** and go to the OBS console to view the name of the created path.

   |image7|

   |image8|

.. |image1| image:: /_static/images/en-us_image_0000001373169101.png
.. |image2| image:: /_static/images/en-us_image_0000001373288829.png
.. |image3| image:: /_static/images/en-us_image_0000001322248392.png
.. |image4| image:: /_static/images/en-us_image_0000001322408368.png
.. |image5| image:: /_static/images/en-us_image_0000001322088460.png
.. |image6| image:: /_static/images/en-us_image_0000001373169105.png
.. |image7| image:: /_static/images/en-us_image_0000001321928776.png
.. |image8| image:: /_static/images/en-us_image_0000001322088468.png
