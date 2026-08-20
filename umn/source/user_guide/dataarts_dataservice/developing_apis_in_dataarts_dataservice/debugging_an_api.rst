:original_name: dataartsstudio_01_0316.html

.. _dataartsstudio_01_0316:

Debugging an API
================

Scenarios
---------

You can debug an API on the management console by adding HTTP header parameters and body parameters.

.. note::

   -  APIs whose backend paths contain environment variables cannot be debugged.
   -  APIs bound to a signature key cannot be debugged.
   -  If a request throttling policy has been bound to an API, the policy does not take effect when you debug the API.

Prerequisites
-------------

An API has been created.

Procedure
---------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. Choose **API Development** > **APIs**.

4. Use either of the following methods to debug an API:

   -  Locate the row that contains the target API, and choose **More** > **Debug**.

   -  Click the name of the target API, and click **Test** on the displayed API details page.

      You can configure API request parameters in the left pane. See :ref:`Table 1 <dataartsstudio_01_0316__table91001022122714>` for parameter details. The request information sent by the API and the returned result after the API request is invoked are displayed on the right.

      .. _dataartsstudio_01_0316__table91001022122714:

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

      .. note::

         The information displayed on the debugging page varies according to the request type.

5. After request parameters are added, click **Debug**.

   The API calling response information is displayed in the command output area in the right pane.

   -  If the API is successfully called, HTTP status code 200 and response information are returned.
   -  If no result is returned within 60 seconds (default value), a timeout error is reported.
   -  If the debugging fails, the HTTP status code 4\ *xx* or 5\ *xx* is returned.

6. You can send different requests using varied parameters and values to verify the API.

   .. note::

      To modify the API parameters, click **Edit** in the upper right corner. The API editing page is displayed.

Related Operations
------------------

-  Debugging APIs: On the DataArts DataService Exclusive console, choose **API Management** > **APIs** in the navigation pane on the left. In the right pane, select APIs, click **Batch Operation** above the list, and select **Debug**. On the displayed page, import the Excel file with the modified API debugging parameters.


   .. figure:: /_static/images/en-us_image_0000002269195549.png
      :alt: **Figure 1** Batch operation

      **Figure 1** Batch operation

-  Publishing an API: After debugging an API, you can publish it so that it can be called by API callers. For details, see :ref:`Publishing an API <dataartsstudio_01_0308>`.
