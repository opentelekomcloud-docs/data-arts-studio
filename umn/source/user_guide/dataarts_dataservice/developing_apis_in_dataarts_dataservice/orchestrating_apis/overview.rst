:original_name: dataartsstudio_01_0324.html

.. _dataartsstudio_01_0324:

Overview
========

API orchestration allows you to reorganize and reconstruct APIs in a visualized manner based on specific service logic and processes without compiling code. In this way, you can perform secondary development easily without affecting native APIs. API orchestration provides you with drag-and-drop and visualized API workflow orchestration capabilities. You can combine multiple APIs into a workflow in serial or parallel mode based on the service logic, invoke the API workflow through the entry API, and obtain the required data.

API orchestration provides more intuitive and efficient design and optimization of business processes, and more convenient secondary development. You can use API orchestration in the following scenarios to simplify development:

-  :ref:`Map or convert the format of a returned message <dataartsstudio_01_0330__en-us_topic_0180012632_section579414314409>` through API orchestration.
-  :ref:`A data request depends on multiple data APIs <dataartsstudio_01_0330__en-us_topic_0180012632_section18624154416414>`: API orchestration reduces the number of API calls, cuts down integration costs, and improves efficiency.

Constraints
-----------

-  API orchestration is available only for DataArts DataService Exclusive clusters of version 3.0.6 or later.
-  Before publishing an API workflow, ensure that all common APIs in the workflow have been published.

Introduction to Operators and Workflows
---------------------------------------

On the API workflow orchestration page, you can drag various types of operators to the canvas, connect them to orchestrate a workflow based on specific service logic and processes, configure the operators, and save, debug, and publish the workflow.

API orchestration supports five types of drag-and-drop operators: Entry API, Common API, Conditional Branch, Parallel Processing, and Output Processing. A workflow starts with an Entry API operator and ends with an Output Processing operator, with any combination of Common API, Conditional Branch, and Parallel Processing operators in the middle. A workflow must meet the following requirements:

-  It starts with and contains only one Entry API operator which can have only one downstream branch.

-  It contains at least one Common API operator at the middle layer. The Common API operator has upstream and downstream operators, but can have only one downstream branch.

-  Conditional Branch operators are optional and located at the middle layer. They must have at least two branches and can have a maximum of 20 branches. If multiple branches meet a condition, only the first branch is executed.

   The Output Processing operator cannot be the direct downstream operator of a Conditional Branch operator. Instead, Conditional Branch operators obtain the request parameters or result sets of their upstream operators for condition judgment.

-  Parallel Processing operators are optional and located at the middle layer. They must have at least two branches and can have a maximum of 20 branches. Failure policies must be configured for Parallel Processing operators.

   The Output Processing operator cannot be the direct downstream operator of a Parallel Processing operator. The logic of multiple branches can be executed at the same time without any impact on each other.

-  An API workflow ends with and can have only one Output Processing operator. The direct upstream operator of the Output Processing operator must be a Common API operator, and at least one result mapping must be configured.

-  An API workflow cannot have a ring structure or isolated operators. A maximum of 20 layers are supported.


.. figure:: /_static/images/en-us_image_0000002269122033.png
   :alt: **Figure 1** API workflow orchestration page

   **Figure 1** API workflow orchestration page

.. table:: **Table 1** API workflow operators

   +-----------------------+-------------------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Navigation Path       | Operator                | Mandatory       | Description                                                                                                                                                                                                                                                                                                         |
   +=======================+=========================+=================+=====================================================================================================================================================================================================================================================================================================================+
   | **Triggers**          | **Entry API**           | Yes             | An API workflow starts with the Entry API operator. After the API workflow is published, it can be invoked through the Entry API operator. In the Entry API operator, you need to define the API workflow name, URL, parameter protocol, request method, reviewer, security authentication, and request parameters. |
   |                       |                         |                 |                                                                                                                                                                                                                                                                                                                     |
   |                       |                         |                 | For details about how to configure an Entry API operator, see :ref:`Configuring an Entry API Operator <dataartsstudio_01_0326>`.                                                                                                                                                                                    |
   +-----------------------+-------------------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **API Catalogs**      | **Common API**          | Yes             | Common API operators are used to perform data query operations. Common APIs are APIs you have created. During API orchestration, you can drag a Common API operator from the API catalog, use the operator to obtain data, and transfer request parameters or result sets as variables.                             |
   |                       |                         |                 |                                                                                                                                                                                                                                                                                                                     |
   |                       |                         |                 | For details about Common API operators, see :ref:`Generating an API Using Configuration <dataartsstudio_01_0305>` or :ref:`Generating an API Using a Script or MyBatis <dataartsstudio_01_0306>`.                                                                                                                   |
   +-----------------------+-------------------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Logic Controllers** | **Conditional Branch**  | No              | The Conditional Branch operator obtains the request parameters or result sets of its upstream operator for condition judgment and determines the next branch to be executed based on the defined expression. If the conditions of multiple branches are met, only the first branch is executed.                     |
   |                       |                         |                 |                                                                                                                                                                                                                                                                                                                     |
   |                       |                         |                 | For details about how to configure Conditional Branch operators and expressions, see :ref:`Configuring a Conditional Branch Operator <dataartsstudio_01_0327>`.                                                                                                                                                     |
   +-----------------------+-------------------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | **Parallel Processing** | No              | The Parallel Processing operator can execute multiple branches at the same time. The branches do not affect each other.                                                                                                                                                                                             |
   |                       |                         |                 |                                                                                                                                                                                                                                                                                                                     |
   |                       |                         |                 | For details about how to configure Parallel Processing operators, see :ref:`Configuring a Parallel Processing Operator <dataartsstudio_01_0328>`.                                                                                                                                                                   |
   +-----------------------+-------------------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | **Output Processing**   | Yes             | The Output Processing operator maps the error codes and result sets, and converts the format of an API workflow to determine the format of the returned data.                                                                                                                                                       |
   |                       |                         |                 |                                                                                                                                                                                                                                                                                                                     |
   |                       |                         |                 | For details about how to configure Output Processing operators, see :ref:`Configuring an Output Processing Operator <dataartsstudio_01_0329>`.                                                                                                                                                                      |
   +-----------------------+-------------------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
