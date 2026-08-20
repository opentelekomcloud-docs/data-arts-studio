:original_name: dataartsstudio_01_0339.html

.. _dataartsstudio_01_0339:

Managing API Versions
=====================

Scenario
--------

DataArts DataService allows you to manage APIs by version, and debug and publish APIs of different versions.

You can also track API changes by API version and compare versions. The system retains 10 latest version records.

Prerequisites
-------------

-  API version management is supported only in the exclusive edition.
-  To update an API version, you need to edit a published API and publish it again. An API cannot be edited and the API version cannot be updated if it is in the pending review or execution state after published, unpublished, suspended, or resumed.

Updating an API Version
-----------------------

To update an API version, you need to edit a published API and publish it again.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose **Exclusive**. The **Overview** page is displayed.

3. Choose **API Development** > **APIs**. Ensure that the API you want to update is in **Published** state and click **Edit** in the **Operation** column.

4. On the **Edit API** page, you can modify the basic configuration or data extraction logic of the API, such as the API catalog, description, request method, input parameters, and data extraction method. The API name, request path, protocol, and security authentication cannot be changed.


   .. figure:: /_static/images/en-us_image_0000002269123357.png
      :alt: **Figure 1** Modifying the basic configuration or data extraction logic of the API

      **Figure 1** Modifying the basic configuration or data extraction logic of the API

5. After modifying the API, click **Next**. On the displayed page, set related parameters and test the API.

   You can configure API request parameters in the left pane. See :ref:`Table 1 <dataartsstudio_01_0339__en-us_topic_0287144772_table91001022122714>` for parameter details. The request information sent by the API and the returned result after the API request is invoked are displayed on the right.

   .. _dataartsstudio_01_0339__en-us_topic_0287144772_table91001022122714:

   .. table:: **Table 1** Debugging APIs

      +-----------------------------------+------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                    |
      +===================================+================================================================================================+
      | API Version                       | Only specified API versions in DataArts DataService Exclusive can be debugged.                 |
      |                                   |                                                                                                |
      |                                   | If the API version is not specified, unpublished APIs will be debugged by default.             |
      +-----------------------------------+------------------------------------------------------------------------------------------------+
      | Parameters                        | Query parameters and their values.                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------+
      | Cluster Settings                  | Supported only by Exclusive Edition. Select the instance where the API to be debugged resides. |
      +-----------------------------------+------------------------------------------------------------------------------------------------+

6. After the test is complete, click **OK** to return to the API list. **Edited** is displayed next to the name of the API that you have modified.


   .. figure:: /_static/images/en-us_image_0000002269123361.png
      :alt: **Figure 2** Editing an API

      **Figure 2** Editing an API

7. Publish the edited API again. In the API list, locate the API you have edited, click **More** in the **Operation** column, and select **Publish**. In the displayed dialog box, select a cluster you have debugged.

   You can publish the API to the cluster where the API was published last time. Then the API information in the cluster will be updated. You can also publish the API to another cluster. Then this API has different versions in different clusters.

Viewing and Comparing Versions
------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the navigation pane on the left, choose **Exclusive**. The **Overview** page is displayed.

3. Choose **API Development** > **API Catalogs** or **API Development** > **APIs**.

4. On the API details page, click the **Version Management** tab to view the versions of the API. A maximum of 10 latest versions are retained.

   You can view the details of an API version, or delete or publish a version. You can also select two versions and click **Compare Version** to compare them.


   .. figure:: /_static/images/en-us_image_0000002234243996.png
      :alt: **Figure 3** Managing API versions

      **Figure 3** Managing API versions
