:original_name: dataartsstudio_01_1019.html

.. _dataartsstudio_01_1019:

Managing Masking Policies
=========================

In business activities, some enterprise departments need to analyze data for operations. In this case, data must be accessible to these departments even if it is sensitive. To meet this requirement and prevent data leakage, you can create data masking policies to mask sensitive data.

This section describes how to manage the masking policies for static masking tasks.

Prerequisites
-------------

-  A sensitive data identification rule has been created. For details, see :ref:`Creating Identification Rules <dataartsstudio_01_1011>`.
-  A built-in or custom masking algorithm has been created. For details, see :ref:`Managing Masking Algorithms <dataartsstudio_01_1035>`.

.. _dataartsstudio_01_1019__en-us_topic_0000001676159901_section9720164374612:

Creating a Data Masking Policy
------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. Choose **Masking Policies** from the left navigation bar, and click **Create** in the upper part of the displayed page.


   .. figure:: /_static/images/en-us_image_0000002234244060.png
      :alt: **Figure 1** Creating a data masking policy

      **Figure 1** Creating a data masking policy

#. In the displayed dialog box, set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1019__en-us_topic_0000001676159901_table029714191274>` and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002269203485.png
      :alt: **Figure 2** Creating a data masking policy

      **Figure 2** Creating a data masking policy

   .. _dataartsstudio_01_1019__en-us_topic_0000001676159901_table029714191274:

   .. table:: **Table 1** Parameters

      +-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                 | Description                                                                                                                                                                         |
      +===========================================+=====================================================================================================================================================================================+
      | \*Policy Name                             | The name of the policy to be created. Policy names can include only letters, numbers, and underscores (_) and cannot exceed 64 characters.                                          |
      +-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                               | A description of the policy to be created, which can contain a maximum of 255 characters.                                                                                           |
      +-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Status                                  | If the status switch is turned on, the policy is available. If the status switch is turned off, the policy cannot be used.                                                          |
      +-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Recognition Rules and Masking Algorithm | Sensitive data identification rule and the corresponding masking algorithm                                                                                                          |
      |                                           |                                                                                                                                                                                     |
      |                                           | -  \*\ **Recognition Rules**: Select a data identification rule. For details, see :ref:`Creating Identification Rules <dataartsstudio_01_1011>`.                                    |
      |                                           | -  **Description**: Enter a description of the rule.                                                                                                                                |
      |                                           | -  \*\ **Algorithm Type**: Select an algorithm type. For details, see :ref:`Table 1 <dataartsstudio_01_1035__en-us_topic_0000001637778038_table19374161110172>`.                    |
      |                                           | -  \*\ **Masking Algorithm**: Select an algorithm of the selected type. For details, see :ref:`Table 1 <dataartsstudio_01_1035__en-us_topic_0000001637778038_table19374161110172>`. |
      |                                           |                                                                                                                                                                                     |
      |                                           | .. note::                                                                                                                                                                           |
      |                                           |                                                                                                                                                                                     |
      |                                           |    Before using the following masking algorithms, you must configure keys:                                                                                                          |
      |                                           |                                                                                                                                                                                     |
      |                                           |    -  HMAC-SHA256 hash algorithm                                                                                                                                                    |
      |                                           |    -  DWS column encryption algorithm                                                                                                                                               |
      |                                           |                                                                                                                                                                                     |
      |                                           |    For more restrictions on different masking algorithms, see :ref:`Managing Masking Algorithms <dataartsstudio_01_1035>`.                                                          |
      +-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Related Operations
------------------

-  Editing a masking policy: On the **Masking Policies** page, locate a policy and click **Edit** in the **Operation** column.

-  Setting the masking policy status: A masking policy is enabled by default. If a data masking policy is disabled, it cannot be used by static data masking tasks.

   To change the status of a data masking policy, click |image1| or |image2| to enable or disable the policy.

   .. note::

      Masking policies used by static masking tasks cannot be disabled.

-  Deleting masking policies: On the **Masking Policies** page, locate a policy and click **Delete** in the **Operation** column. To delete multiple policies, select them and click **Delete** above the list.

   Policies used by static masking tasks cannot be deleted. To delete such policies, modify the reference relationship first.

   .. note::

      The deletion operation cannot be undone. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000002269203509.png
.. |image2| image:: /_static/images/en-us_image_0000002234084212.png
