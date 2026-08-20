:original_name: dataartsstudio_01_1182.html

.. _dataartsstudio_01_1182:

Diagnosing Data Security Risks
==============================

Data security diagnosis can help you diagnose data security capabilities and provide rectification suggestions and solutions for you based on the diagnosis result. In this way, you can quickly establish a basic data security system to ensure data security and reliability.

Constraints
-----------

-  Currently, only the security of the MRS data source can be diagnosed.
-  The timeout duration of a scanning task for security diagnosis is one hour.
-  For the data permission control diagnosis item, the workspace administrator and security administrator only collect statistics of users, but not of user group members.


Diagnosing Data Security Risks
------------------------------

Data security diagnosis supports three diagnosis items: sensitive data protection, data permission control, and data source protection. For details, see :ref:`Figure 1 <dataartsstudio_01_1182__fig19526102655018>`.

.. _dataartsstudio_01_1182__fig19526102655018:

.. figure:: /_static/images/en-us_image_0000002269203853.png
   :alt: **Figure 1** Data security diagnosis

   **Figure 1** Data security diagnosis

You are advised to scan data at least once a month to ensure data security and reliability. The procedure of diagnosing data security risks is as follows:

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the navigation pane on the left, choose **Data Security Diagnosis**.


   .. figure:: /_static/images/en-us_image_0000002234244404.png
      :alt: **Figure 2** Data Security Diagnosis

      **Figure 2** Data Security Diagnosis

#. Click the **Sensitive Data Protection**, **Data Permission Control**, or **Data Source Protection** tab, and click **Scan** or **Rescan**.

#. After the scan is complete, identify risky items based on the scan result and handling suggestions and click **Handle Risk** to ensure data security and reliability.

   You are advised to handle medium and high security risks as soon as possible. The following figure shows the risk level and diagnosis result of a check item on the **Sensitive Data Protection** page.


   .. figure:: /_static/images/en-us_image_0000002234084572.png
      :alt: **Figure 3** Security diagnosis result

      **Figure 3** Security diagnosis result
