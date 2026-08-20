:original_name: dataartsstudio_01_0633.html

.. _dataartsstudio_01_0633:

Business Metrics
================

After data survey and requirement analysis, you must implement metrics. A metric is a statistical value that measures the overall characteristic of a target and reflects the business situation in a business activity of an enterprise. A metric consists of its name and value. The metric name and its definition reflect the quality and quantity of the metric. The metric value reflects the quantifiable values of the specified time, location, and condition of the metric.

Business metrics define the purposes and calculation formulas of technical metrics and are not used to perform actual calculation. Business metrics can be associated with technical metrics. Technical metrics implement business metrics and define calculation methods.

Prerequisites
-------------

You have designed a process. For details, see :ref:`Designing Processes <dataartsstudio_01_0631>`.

Creating and Publishing a Business Metric
-----------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Architecture**.

#. On the DataArts Architecture page, choose **Metrics** > **Business Metrics** in the left navigation pane.

#. .. _dataartsstudio_01_0633__li02113119322:

   In the process tree on the left, select a process and click **Create**.

#. On the page displayed, set the parameters and click **Publish**.

   a. Configure basic settings.


      .. figure:: /_static/images/en-us_image_0000002269122629.png
         :alt: **Figure 1** Basic Settings area

         **Figure 1** Basic Settings area

      .. table:: **Table 1** Parameters in the Basic Settings area

         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                |
         +===================================+============================================================================================================================================================================================================================================================+
         | \*Metric Name                     | The name of the business metric to create. Newline characters and the following characters are not allowed: \\ < > % " ' ;                                                                                                                                 |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Code                              | -  The metric code is automatically generated. You can configure the generation rule on the **Configuration Center** page of DataArts Architecture. For details, see :ref:`Encoding Rules <dataartsstudio_01_0621__section66767193176>`.                   |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Alias                             | This parameter is optional.                                                                                                                                                                                                                                |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | \*Process                         | Select the process that the metric belongs to. If no process is available, create one. Refer to :ref:`Designing Processes <dataartsstudio_01_0631>` for details.                                                                                           |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | \*Objective                       | Your purpose of setting the metric.                                                                                                                                                                                                                        |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | \*Metric Definition               | The definition of the metric must be accurately described.                                                                                                                                                                                                 |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Remarks                           | Remarks for the metric to create.                                                                                                                                                                                                                          |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | *Custom metric*                   | If a custom metric is configured on the **Metrics** tab page of the configuration center, the metric is displayed as a parameter on this page. For how to create a custom field, see :ref:`Metric Settings <dataartsstudio_01_0621__section171603263371>`. |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   b. Configure the metric information.


      .. figure:: /_static/images/en-us_image_0000002234083428.png
         :alt: **Figure 2** Metric Information area

         **Figure 2** Metric Information area

      .. table:: **Table 2** Parameters in the Metric Information area

         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                          |
         +===================================+======================================================================================================================================================================================================================+
         | \*Formula                         | The computing logic of the business metric, which guides developers to design atomic and derivative metrics. Business metrics are used to guide the implementation of technical metrics only and are not calculated. |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | \*Statistical Frequency           | The statistical period of a metric, which helps developers set the time limits.                                                                                                                                      |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Statistical Dimension             | You can select an existing dimension from the drop-down list For details on how to create a dimension, see :ref:`Creating Dimensions <dataartsstudio_01_0609>`.                                                      |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Standard & Modifier               | Modifiers are abstract definitions of scenarios and are used to determine the measurement scope.                                                                                                                     |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | \*Refresh Frequency               | The interval for updating a metric. Developers or operators can set the scheduling frequency of derivative metrics based on the metric update frequency.                                                             |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Metric Application Scenario       | The application scenarios of the metric.                                                                                                                                                                             |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Associated Technical Metrics Type | Select the type of the technical metric associated with the business metric. Available options include **Derivative metric**, **Compound metric**, and **Atomic metric**.                                            |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Associated Technical Metrics      | Select a technical metric associated with the business metric.                                                                                                                                                       |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Measurement Object                | The field for measuring a metric.                                                                                                                                                                                    |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Measurement Unit                  | The measurement unit of a metric.                                                                                                                                                                                    |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Configure the management information.


      .. figure:: /_static/images/en-us_image_0000002269122649.png
         :alt: **Figure 3** Management Information area

         **Figure 3** Management Information area

      .. table:: **Table 3** Parameters in Management Information area

         +--------------------+-------------------------------------------------------------------------------+
         | Parameter          | Description                                                                   |
         +====================+===============================================================================+
         | Data Source        | The generator of data.                                                        |
         +--------------------+-------------------------------------------------------------------------------+
         | \*Metric Mgmt Dept | The department that manages the metric.                                       |
         +--------------------+-------------------------------------------------------------------------------+
         | \*Metric Owner     | Metric owner. You can enter the name of an owner or select an existing owner. |
         +--------------------+-------------------------------------------------------------------------------+

#. .. _dataartsstudio_01_0633__li11231131183219:

   In the displayed dialog box, select a reviewer and click **OK** to submit an application.

   .. note::

      If you have been added as a reviewer, you can select **Auto-review** and click **OK**. After the request is approved, the status changes to **Published**.

      If you select multiple reviewers, the status changes to **Published** only after all reviewers have approved the publishing request. If any reviewer rejects the request, the status is **Rejected**.

#. Repeat :ref:`3 <dataartsstudio_01_0633__li02113119322>` to :ref:`5 <dataartsstudio_01_0633__li11231131183219>` to create and publish other business metrics.

#. All the business metrics need reviewing.

   If the applications are approved, the business metrics are created.

   Click the name of a business metric to view its details, relationship diagram, publishing history, and review history.

   In the relationship diagram, you can view the lineage diagram of the business metric.

   In the release history, you can view the differences between historical versions.

Editing a Business Metric
-------------------------

#. On the DataArts Architecture page, choose **Metrics** > **Business Metrics** in the left navigation pane.


   .. figure:: /_static/images/en-us_image_0000002269122665.png
      :alt: **Figure 4** Managing business metrics

      **Figure 4** Managing business metrics

#. In the business metric list, select the target metric and click **Edit** on the right.

#. Edit the business metric information as required.

#. Click **Save** to save the settings. Alternatively, click **Publish** to publish the edited business metric.

Publishing a Business Metric
----------------------------

If a business metric is created but not published, perform the following steps to publish it:

#. On the DataArts Architecture page, choose **Metrics** > **Business Metrics** in the left navigation pane.

#. In the business metric list, select the target metric and click **Publish**.

#. In the dialog box displayed, select a reviewer and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269202693.png
      :alt: **Figure 5** Submit for Publication dialog box

      **Figure 5** Submit for Publication dialog box

Suspending a Business Metric
----------------------------

You can perform the following steps to suspend a published business metric:

#. On the DataArts Architecture page, choose **Metrics** > **Business Metrics** in the left navigation pane.

#. In the business metric list, select the target business metric and click **Suspend** in the **Operation** column.

#. In the dialog box displayed, select a reviewer and click **OK**. The business metric is suspended after the reviewer approves it.


   .. figure:: /_static/images/en-us_image_0000002234083404.png
      :alt: **Figure 6** Apply for Suspension dialog box

      **Figure 6** Apply for Suspension dialog box

Deleting a Business Metric
--------------------------

If a business metric is no longer needed, you can delete it. A business metric in the **Published** state can be deleted only after it is suspended.

#. On the DataArts Architecture page, choose **Metrics** > **Business Metrics** in the left navigation pane.

#. In the business metric list, select the target business metric and choose **More** > **Delete** above the list.


   .. figure:: /_static/images/en-us_image_0000002269202749.png
      :alt: **Figure 7** Deleting a business metric

      **Figure 7** Deleting a business metric

#. In the dialog box displayed, confirm the information and click **Yes**.

Importing/Exporting Business Metrics
------------------------------------

**Importing metrics**: You can import business metrics in batches.

#. On the DataArts Architecture page, choose **Metrics** > **Business Metrics** in the left navigation pane.

#. Above the business metric list, click **More** and select **Import**. In the displayed **Import Business Metric** dialog box, click **Business Metric Template**.


   .. figure:: /_static/images/en-us_image_0000002234243288.png
      :alt: **Figure 8** Importing business metrics

      **Figure 8** Importing business metrics

   .. table:: **Table 4** Parameters for importing business metrics

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================================================================================+
      | Update Existing Data              | Whether to update the existing table if the table to be imported already exists. The system determines whether the table to import exists based on the table code. The import operation can be used to create a table or update an existing table. It does not delete a table. The options are as follows: |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   | -  **No**: If you select this option, the existing tables will not be updated.                                                                                                                                                                                                                             |
      |                                   | -  **Yes**: If you select this option, the existing tables will be updated. If a table is in the **Published** state, you must publish the table again after updating it so that the updated table can take effect.                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | File                              | Select the file to import. You can use the following method to obtain the file to import:                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   | **Downloading the ER modeling template and fill in the template**                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                            |
      |                                   | On the **Import** tab page, click **Business Metric Template** to download the template, fill in the template, and save the settings.                                                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Open the downloaded template, set the parameters in the template, and save the template. The **Description** sheet in the template is for reference only.

   Parameters whose names start with an asterisk (``*``) are mandatory, and other parameters are optional.

   The table below describes the parameters in the **Business Metric** sheet.

   .. table:: **Table 5** parameters in the Business Metric sheet

      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                       | Description                                                                                                                                                                             |
      +=================================+=========================================================================================================================================================================================+
      | \*Process                       | Level-1 process corresponding to the metric                                                                                                                                             |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Name                          | Standard name of the metric, which must be unique.                                                                                                                                      |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Code                            | It is automatically generated by the system.                                                                                                                                            |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Alias                           | Simplified name of the metric used in specific scenarios such as reports                                                                                                                |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Objective                     | Objective of the metric                                                                                                                                                                 |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Metric Definition             | Accurate meaning of the metric that can help related personnel understand the content measured by the metric                                                                            |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Calculation Formula           | Clear rule for calculating the metric data                                                                                                                                              |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Source                     | System from which data comes. If possible, the specific data table name and field should be specified.                                                                                  |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Measurement Unit                | Basic measurement unit of the metric                                                                                                                                                    |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Statistical Period            | Statistical period of the metric                                                                                                                                                        |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Statistical Dimension           | Common statistical dimension. Dimensions are generally hierarchical.                                                                                                                    |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Refresh Frequency             | Minimum frequency at which the metric data is updated                                                                                                                                   |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Statistical Standard & Modifier | Statistical standard and modifier the metric usually uses in addition to the statistical period and dimension. The statistical standard and modifier restrict the scope of metric data. |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Metric Application Scenario     | Important application scenarios of the metric, such as online reports, routine reports, and reporting materials                                                                         |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Remarks                         | Additional information that helps understand and use the metric                                                                                                                         |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Measurement Object              | Field for measuring the metric. If this parameter is not involved, leave it blank.                                                                                                      |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Metric Mgmt Dept              | Department responsible for defining, maintaining, and interpreting the metric and providing metric data.                                                                                |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Metric Owner                  | Metric owner (cloud account name)                                                                                                                                                       |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Related Tech Metric             | Implementation of the business metric in the specifications design                                                                                                                      |
      +---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. View the result on the **Last Import** tab page. If the import is successful, click **Close**. If the import fails, you can view the failure cause, correct the template file, and upload it again.


   .. figure:: /_static/images/en-us_image_0000002269122645.png
      :alt: **Figure 9** Last Import tab page

      **Figure 9** Last Import tab page

**Exporting metrics**: You can export created business metrics.

#. On the DataArts Architecture page, choose **Metrics** > **Business Metrics** in the left navigation pane.

#. On the **Business Metrics** page, select a business metric, click **More**, and select **Export**.


   .. figure:: /_static/images/en-us_image_0000002269122681.png
      :alt: **Figure 10** Exporting a business metric

      **Figure 10** Exporting a business metric

   .. note::

      If a custom metric was created on the **Metrics** tab page in the configuration center, the custom metric is displayed in the exported table.
