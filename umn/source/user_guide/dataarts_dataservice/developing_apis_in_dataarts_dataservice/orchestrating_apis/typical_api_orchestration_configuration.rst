:original_name: dataartsstudio_01_0330.html

.. _dataartsstudio_01_0330:

Typical API Orchestration Configuration
=======================================

The typical application scenarios of API orchestration are as follows:

-  :ref:`Map or convert the format of a returned message <dataartsstudio_01_0330__en-us_topic_0180012632_section579414314409>` through API orchestration.
-  :ref:`A data request depends on multiple data APIs <dataartsstudio_01_0330__en-us_topic_0180012632_section18624154416414>`: API orchestration reduces the number of API calls, cuts down integration costs, and improves efficiency.

Constraints
-----------

-  API orchestration is available only for DataArts DataService Exclusive clusters of version 3.0.6 or later.
-  Before publishing an API workflow, ensure that all common APIs in the workflow have been published.

.. _dataartsstudio_01_0330__en-us_topic_0180012632_section579414314409:

Developing an API Workflow 1: Mapping or Converting the Format of a Returned Message
------------------------------------------------------------------------------------

To convert the result returned by an API from JSON data into an Excel file, perform the following operations:

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.
#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

3. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

4. Choose **API Development** > **API Orchestration** and click **Create**.


   .. figure:: /_static/images/en-us_image_0000002234080776.png
      :alt: **Figure 1** API orchestration page

      **Figure 1** API orchestration page

5. Drag the Entry API operator to the canvas, click the operator, and configure its parameters.


   .. figure:: /_static/images/en-us_image_0000002269200065.png
      :alt: **Figure 2** Configuring the Entry API operator

      **Figure 2** Configuring the Entry API operator

6. Drag the target Common API operator to the canvas and mount it to the Entry API operator. Click the Common API operator and copy its code, for example, **NormalApi_5274d**.


   .. figure:: /_static/images/en-us_image_0000002269200001.png
      :alt: **Figure 3** Copying code

      **Figure 3** Copying code

7. Drag the Output Processing operator to the canvas and mount it to the Common API operator. Click the Output Processing operator configure its parameters.

   -  Add a result set mapping. Enter the result of the Common API operator for the mapping expression, for example, **${NormalApi_5274d|payload}** and enter the result set name, for example, **Sales records**.
   -  Select **EXCEL** for **Return Format**.


   .. figure:: /_static/images/en-us_image_0000002269119973.png
      :alt: **Figure 4** Configuring the Output Processing operator

      **Figure 4** Configuring the Output Processing operator

8. Save the API workflow, debug it, and publish it to the cluster. After that, the Entry API operator of the API workflow can be invoked to save the data obtained by the common API to an Excel file.

.. _dataartsstudio_01_0330__en-us_topic_0180012632_section18624154416414:

Developing an API Workflow 2: A Data Request Depends on Multiple Data APIs
--------------------------------------------------------------------------

A department of an e-commerce company wants to provide supplier information and sales rating data for users in area1 and provide retailer information for users in other areas.

The following APIs are available: AreaInformation, SupplierInformation, SalesRating, and RetailerInformation. You can create an API workflow that meets the department's demands by performing the following steps:

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.
#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

3.  In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

4.  Choose **API Development** > **API Orchestration** and click **Create**.


    .. figure:: /_static/images/en-us_image_0000002234080776.png
       :alt: **Figure 5** API orchestration page

       **Figure 5** API orchestration page

5.  Drag the Entry API operator to the canvas, click the operator, and configure its parameters.


    .. figure:: /_static/images/en-us_image_0000002234240604.png
       :alt: **Figure 6** Configuring the Entry API operator

       **Figure 6** Configuring the Entry API operator

6.  Drag the AreaInformation API operator in the API catalogs to the canvas and mount it to the Entry API operator. Click the AreaInformation API operator and copy its code, for example, **NormalApi_ff8bd**.


    .. figure:: /_static/images/en-us_image_0000002234240644.png
       :alt: **Figure 7** Copying the code of the AreaInformation operator

       **Figure 7** Copying the code of the AreaInformation operator

7.  Drag the Conditional Branch operator to the canvas, mount it to the AreaInformation operator, and mount the Parallel Processing operator and RetailerInformation operator to the Conditional Branch. The code of the RetailerInformation operator is **NormalApi_de62d**.

    Click the Conditional Branch operator on the canvas and configure its parameters.

    -  For the Parallel Processing operator, set **Condition Type** to **Meets the current condition** and **Expression** to **${NormalApi_ff8bd|payload.data[0].area}**. The expression is used to obtain the field value in the first row and the **area** column in the result set of the AreaInformation API. If the obtained field value is **area1**, the Parallel Processing operator is executed.
    -  For the RetailerInformation operator, set **Condition Type** to **Does not meet other conditions**. If the conditions of the Parallel Processing operator are not met, the RetailerInformation operator is executed.


    .. figure:: /_static/images/en-us_image_0000002234080772.png
       :alt: **Figure 8** Configuring the Conditional Branch operator

       **Figure 8** Configuring the Conditional Branch operator

8.  Drag the SupplierInformation API and SalesRating API operators in the API catalogs to the canvas, and mount them to the Parallel Processing operator. The code of the SupplierInformation operator is **NormalApi_3ad5c** and that of the SalesRating operator is **NormalApi_01e7e**.

    Click the Parallel Processing operator and set **Policy Upon Branch Failure** and **Timeout Duration** for the SupplierInformation and SalesRating operators. (retain their default values.) When the Parallel Processing operator is executed, the SupplierInformation and SalesRating operators are both scheduled.


    .. figure:: /_static/images/en-us_image_0000002234240620.png
       :alt: **Figure 9** Configuring the Parallel Processing operator

       **Figure 9** Configuring the Parallel Processing operator

9.  Drag the Output Processing operator to the canvas and mount it to the three Common API operators. Click the Output Processing operator and add result set mappings.

    Add three mappings to output the results of the three Common API operators. Set the expressions of the mappings to the results of the corresponding Common API operators, for example, **${NormalApi_3ad5c|payload}**, **${NormalApi_01e7e|payload}**, and **${NormalApi_de62d|payload}**, and set the result set names.


    .. figure:: /_static/images/en-us_image_0000002269119993.png
       :alt: **Figure 10** Configuring the Output Processing operator

       **Figure 10** Configuring the Output Processing operator

10. Save the API workflow, debug it, and publish it to the cluster. After that, the Entry API operator of the API workflow can be invoked to return different information for users in different areas.

Related Operations
------------------

-  Editing an API workflow: On the API workflow list page, locate a workflow, and click **Edit** in the **Operation** column. On the displayed page, orchestrate the workflow again or modify it.

-  Viewing API workflow authorization: On the API workflow list page, locate a workflow and click **View** in the **Operation** column to access the API information page, where you can authorize the workflow.

   If the app or IAM authentication mode is used for the Entry API, you must create an app and authorize the app to use the API before invoking the API workflow. The workflow authorization method is basically the same as the API authorization method. For details, see :ref:`Authorizing API Calling <dataartsstudio_01_0336>` or :ref:`Applying for API Authorization <dataartsstudio_01_0334>`.

-  Debugging an API workflow: On the API workflow list page, locate a workflow, click **More** in the **Operation** column, and select **Debug**.

   Add request parameters and click **Test**. The response of the API call is displayed in the result output area on the right. The workflow debugging process is basically the same as the API debugging process. For details, see :ref:`Debugging an API <dataartsstudio_01_0316>`.

-  Publishing an API workflow: On the API workflow list page, locate a workflow, click **More** in the **Operation** column, and select **Publish**.

   An API workflow is available only after it is published. The workflow publishing process is basically the same as the API publishing process. For details, see :ref:`Publishing an API <dataartsstudio_01_0308>`.

-  Unpublishing/Deleting an API workflow: On the API workflow list page, locate a workflow, click **More** in the **Operation** column, and select **Unpublish** to unpublish the workflow. Select a workflow and click **Delete** above the workflow list to delete the workflow.

   If you want to stop a published API workflow from providing services, you can unpublish it. The authorization information will not be retained after the API workflow is unpublished. If you no longer need the suspended API, you can delete it. The deletion cannot be undone. The process of unpublishing/deleting an API workflow is basically the same as that of unpublishing/deleting an API. For details, see :ref:`Unpublishing/Deleting APIs <dataartsstudio_01_0319>`.

-  Suspending/Restoring an API workflow: On the API workflow list page, locate a workflow, click **More** in the **Operation** column, and select **Suspend** or **Restore**.

   To edit or debug a published API workflow, you must suspend the API workflow first. After the API workflow is suspended, its authorization information is retained. You can still edit and debug the API workflow. You can resume the API workflow so that it can continue to provide services. The process of suspending/resuming an API workflow is basically the same as that of suspending/resuming an API. For details, see :ref:`Suspending/Restoring an API <dataartsstudio_01_0318>`.

-  Displaying an API workflow: On the API workflow list page, locate a workflow, click **More** in the **Operation** column, and select **Display**.

   Then you can set the visibility scope of the API workflow in the service catalog. The process of setting the visibility scope of an API workflow is basically the same as that of setting the visibility scope of an API. For details, see :ref:`Displaying an API <dataartsstudio_01_0323>`.

-  Copying an API workflow: On the API workflow list page, locate a workflow, click **More** above the list, and select **Copy**.

   By copying an API workflow, you can obtain an API workflow with the same configuration as the source API workflow. The processing of copying an API workflow is basically the same as that of copying an API. For details, see :ref:`Copying an API <dataartsstudio_01_0322>`.

-  Synchronizing an API workflow to Data Map: On the API workflow list page, locate a workflow, click **More** above the list, and select **Synchronize to Data Map**.

   This allows you to view API workflows in Data Map. The processing of synchronizing an API workflow to Data Map is basically the same as that of synchronizing an API to Data Map. For details, see :ref:`Synchronizing APIs to Data Map <dataartsstudio_01_0321__section1089845413243>`.
