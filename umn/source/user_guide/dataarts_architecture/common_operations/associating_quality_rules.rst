:original_name: dataartsstudio_01_0636.html

.. _dataartsstudio_01_0636:

Associating Quality Rules
=========================

After creating and publishing a table, you can associate quality rules with the table. If **Create Data Quality Jobs** is selected for **Model Design Process** on the **Function Settings** tab page of **Configuration Center**, a quality job is automatically created in DataArts Quality after a quality rule is associated and the table is published. If the table has been published, the system automatically updates the corresponding quality job.

Associating a Quality Rule and Viewing a Quality Job
----------------------------------------------------

#. On the DataArts Architecture page, choose **Models** > **ER Modeling** in the left navigation pane.

#. On the page displayed, select the target model. All tables created in the model are listed on the right. You can also expand a topic structure and select an object. All tables of the object are listed on the right.

#. In the table list, select a table and click its name to access the table details page.


   .. figure:: /_static/images/en-us_image_0000002269202541.png
      :alt: **Figure 1** ER model list

      **Figure 1** ER model list

#. In the **Table Field** area, select a field that you want to associate a quality rule with and click **Associate Rule**.


   .. figure:: /_static/images/en-us_image_0000002234243040.png
      :alt: **Figure 2** Associating Quality Rules

      **Figure 2** Associating Quality Rules

   **Anomaly Data Output Settings**: If you select **Generate Anomaly Data**, the anomaly data is stored in the specified database based on the settings.

#. In the dialog box displayed, click **Add Rule**.


   .. figure:: /_static/images/en-us_image_0000002234243064.png
      :alt: **Figure 3** Adding a quality rule

      **Figure 3** Adding a quality rule

   The **Add Rule** dialog box lists all default quality rules supported by DataArts Quality. Select a rule and click **OK**. If these quality rules cannot meet your requirements, you can customize one. In the **Add Rule** dialog box, click **Create** to navigate to DataArts Quality and create a rule on the page displayed. See :ref:`Creating a Data Quality Rule <dataartsstudio_01_0715>`.


   .. figure:: /_static/images/en-us_image_0000002269202569.png
      :alt: **Figure 4** Add Rule dialog box

      **Figure 4** Add Rule dialog box

   After a rule is added, the **Associate Quality Rule** dialog box is displayed. Select a rule from the rule name list, set **Alarm Condition**, and click **OK**.

   -  In the **Alarm Condition** text box, enter an expression. When a quality job is running, the system calculates the result of the alarm condition expression and determines whether to trigger the alarm based on the result of the expression. If the expression result is **true**, the alarm will be triggered. Otherwise, no quality alarm will be triggered.

   -  An alarm condition expression consists of alarm parameters and logical operators.

      The alarm parameters of each rule are displayed as buttons. If you click these buttons, the alarm conditions are expressed in the sequence of alarm parameters, such as *${1}*, *${2}*, and *${3}*. The variable names indicate the alarm parameters. In other words, when setting **Alarm Condition**, use the variable *${1}* to represent the first alarm parameter, *${2}* to represent the second alarm parameter, and so on.


   .. figure:: /_static/images/en-us_image_0000002269202549.png
      :alt: **Figure 5** Setting an alarm triggering condition

      **Figure 5** Setting an alarm triggering condition

#. (Optional) If you want to store anomaly data that does not comply with the preset rules in the exception table, enable **Anomaly Data Output Settings**.


   .. figure:: /_static/images/en-us_image_0000002269202557.png
      :alt: **Figure 6** Enabling Anomaly Data Output Settings

      **Figure 6** Enabling Anomaly Data Output Settings

   Click the pen icon next to **Anomaly Data Output Settings** and enable **Generate Anomaly Data**. The anomaly data will be stored in the specified database based on the settings.


   .. figure:: /_static/images/en-us_image_0000002269122445.png
      :alt: **Figure 7** Anomaly Data Output Settings

      **Figure 7** Anomaly Data Output Settings

   The parameters are as follows:

   -  **Database/Schema**: database or schema that stores anomaly data
   -  **Table Prefix**: prefix of the table that stores anomaly data
   -  **Table Suffix**: suffix of the table that stores anomaly data

   Click |image1| to save the settings.

#. (Optional) By default, the quality rule applies to the entire table. If you want to query data in specified partitions, set the where condition.


   .. figure:: /_static/images/en-us_image_0000002269202505.png
      :alt: **Figure 8** Where condition

      **Figure 8** Where condition

#. View the association result. If the association is successful, click **OK**. If the association fails, find the failure cause, correct it, and associate the quality rule again.


   .. figure:: /_static/images/en-us_image_0000002234083292.png
      :alt: **Figure 9** Association results

      **Figure 9** Association results

#. Go back to the ER model list, locate the table that you just associated with a quality rule. In the **Sync Status** column, move your pointer to |image2| and click **View**.


   .. figure:: /_static/images/en-us_image_0000002234243076.png
      :alt: **Figure 10** Quality job sync status

      **Figure 10** Quality job sync status

#. On the page displayed, click the **Rule Configurations** tab to view the rule you just added.


   .. figure:: /_static/images/en-us_image_0000002234243084.png
      :alt: **Figure 11** Quality rules

      **Figure 11** Quality rules

   If a table is associated with a data standard when it is created, the corresponding quality rule is generated after the table is published. You can also view the rule on the **Quality Jobs** page.

   The following provides an example of the quality rule generated based on the data standard associated with a field:


   .. figure:: /_static/images/en-us_image_0000002234083228.png
      :alt: **Figure 12** Quality rule associated with a field

      **Figure 12** Quality rule associated with a field

   The following provides an example of the quality rule generated based on the data standard associated with a lookup table:


   .. figure:: /_static/images/en-us_image_0000002234243104.png
      :alt: **Figure 13** Quality rules for data standards

      **Figure 13** Quality rules for data standards

.. |image1| image:: /_static/images/en-us_image_0000002234243052.png
.. |image2| image:: /_static/images/en-us_image_0000002234243072.png
