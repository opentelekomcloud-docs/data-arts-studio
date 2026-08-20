:original_name: dataartsstudio_01_0719.html

.. _dataartsstudio_01_0719:

Creating a Quality Job
======================

Scenario
--------

You can use a quality job to monitor data quality. This section describes how to create a quality job.

Procedure
---------

#. On the DataArts Studio console, locate a workspace and click **DataArts Quality**.

2. Create a rule template.

   a. In the navigation pane on the left, choose **Rule Templates**. System templates are displayed. Rule templates have six dimensions: completeness, uniqueness, timeliness, validity, accuracy, and consistency.
   b. **Optional:** Click **Create** to create a rule template.

      .. note::

         In this example, use a system rule.

3. Create a quality job.

   a. In the navigation pane on the left, choose **Quality Jobs**.

   b. Click **Create**. On the **Create Quality Job** page, set basic information about the quality job.

      |image1|

   c. Click **Next** to go to the **Define Rule** page. Click |image2| on the rule card to configure the rule.

      |image3|

   d. Click **Next** and set alarm parameters.

      |image4|

   e. Click **Next** and set subscription parameters.

      |image5|

   f. Click **Next** and set scheduling parameters.

      |image6|

   g. Click **Submit**.

4. In the quality job list, locate the created job and click **Run** in the **Operation** column.

   a. After the quality job is successfully run, choose **Quality Reports** in the navigation pane on the left.

   b. The **Technical Reports** page is displayed by default.


      .. figure:: /_static/images/en-us_image_0000002269200681.png
         :alt: **Figure 1** Technical report

         **Figure 1** Technical report

   c. Click the **Business Reports** tab and view the business reports.


      .. figure:: /_static/images/en-us_image_0000002269200673.png
         :alt: **Figure 2** Business report

         **Figure 2** Business report

.. |image1| image:: /_static/images/en-us_image_0000002269200665.png
.. |image2| image:: /_static/images/en-us_image_0000002234241244.png
.. |image3| image:: /_static/images/en-us_image_0000002234241260.png
.. |image4| image:: /_static/images/en-us_image_0000002234241252.png
.. |image5| image:: /_static/images/en-us_image_0000002269200685.png
.. |image6| image:: /_static/images/en-us_image_0000002269200677.png
