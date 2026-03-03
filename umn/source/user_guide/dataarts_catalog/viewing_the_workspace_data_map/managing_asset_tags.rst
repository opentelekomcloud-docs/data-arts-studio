:original_name: dataartsstudio_01_0810.html

.. _dataartsstudio_01_0810:

Managing Asset Tags
===================

Tags can be defined and associated with technical assets for better asset management. For example, you can tag a table as the SDI source data layer or DWI data integration layer.

Tags are keywords used to identify the business meanings of technical assets. They help you classify and describe technical assets for easy search.

Tags and Classifications
------------------------

Tags are highly related keywords that help you classify and describe assets for easy retrieval.

Classification is the process of categorizing assets by category, level, or nature. Classification is top-down. Assets are classified according to certain standards.

The table below lists the differences between tags and classifications.

.. table:: **Table 1** Differences between tags and classifications

   +------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Item             | Category                                                                                         | Tag                                                                   |
   +==================+==================================================================================================+=======================================================================+
   | Exclusiveness    | Yes                                                                                              | None                                                                  |
   +------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | **Relationship** | Dependent                                                                                        | Relevant (associated)                                                 |
   +------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Creation         | Pre-event planning                                                                               | Any time                                                              |
   +------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Cost             | High                                                                                             | Low                                                                   |
   +------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | **Source**       | For details, see :ref:`Creating a Data Classification (To Be Removed) <dataartsstudio_01_0822>`. | For details, see :ref:`Managing Asset Tags <dataartsstudio_01_0810>`. |
   +------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+

.. _dataartsstudio_01_0810__en-us_topic_0159221300_section694485119415:

Managing a Tag
--------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

2. Choose **Data Map** > **Tag Management** from the left navigation bar.
3. Click **Create** to create a tag.

   -  **Tag Name**: Tag names can include only letters, numbers, and underscores (_). They cannot start with underscores (_) or exceed 100 characters.
   -  **Description**: Up to 255 characters are allowed.

4. Select a tag and click **Delete** to delete the tag.
5. Click **Edit** to modify the description of a tag.

Identifying Technical Assets: Adding Tags
-----------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

2. Choose **Data Map** > **Data Catalog** and click the **Technical Assets** tab.
3. Enter a keyword in the search box, and click the search icon. The search results are listed below the search box.

4. Select the technical asset that you want to add a tag to and click **Add Identifier** in the upper right corner. In the **Add Identifier** dialog box, select **Tags** for **Type**.


   .. figure:: /_static/images/en-us_image_0000002269116409.png
      :alt: **Figure 1** Adding an identifier

      **Figure 1** Adding an identifier

5. Set the parameters and click **OK**.

   .. note::

      You can add a new tag or select an existing tag. Existing tags are created by following instructions in :ref:`Managing a Tag <dataartsstudio_01_0810__en-us_topic_0159221300_section694485119415>`.
