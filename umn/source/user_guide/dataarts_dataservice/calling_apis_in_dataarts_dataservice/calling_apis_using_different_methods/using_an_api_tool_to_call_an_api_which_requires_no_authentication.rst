:original_name: dataartsstudio_01_0358.html

.. _dataartsstudio_01_0358:

Using an API Tool to Call an API Which Requires No Authentication
=================================================================

APIs requiring no authentication can be directly called using an API tool. Authentication information is not required.

.. note::

   It is recommended that the non-authentication mode be used only for testing APIs. If the caller is not a trusted user, there is a risk of data leakage, breakdowns caused by high concurrent access, SQL injection, and others.

This section uses Postman as an example to describe how to use an API tool to call an API which requires no authentication. The procedure is as follows:

#. :ref:`Obtaining API Information <dataartsstudio_01_0358__section1797493715104>`: Prepare key information of the API.
#. :ref:`Calling an API <dataartsstudio_01_0358__section6697113833611>`: Use Postman to call the API.

Prerequisites
-------------

-  An API or API workflow requiring no authentication has been published. The published API is available in DataArts Catalog.

-  Postman has been installed. If it has not been installed, download it from the `Postman official website <https://www.postman.com/>`__ and install it.

Notes and Constraints
---------------------

-  To call an API in DataArts DataService locally, you need to bind an EIP to the DataArts DataService Exclusive cluster when creating the cluster.

-  When an API in DataArts DataService is called, if the total duration of query and response exceeds 60 seconds (default value), a timeout error is reported. In this case, you can optimize the API configuration based on the API calling duration recorded in the access log.

   .. code-block::

      ____________Duration information__________
      duration: 60491ms //Total duration
      url_duration: 0ms //URL matching duration
      auth_duration: 70ms //Authentication duration
      befor_sql_duration: 402ms //Preprocessing duration before SQL execution
      sql_duration: 60001ms //SQL execution duration
      after_sql_duration:18ms //Postprocessing duration after SQL execution

.. _dataartsstudio_01_0358__section1797493715104:

Obtaining API Information
-------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

#. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

#. Obtain the URL, request method, and input parameters of the API to be called.

   In the navigation pane on the left, choose **APIs**. Locate the API to be called, click the API name to access its details page, and record the URL, request method, and input parameters of the API.

   -  URL for calling the API: The exclusive edition supports both private and public IP addresses. To use the public IP address, you need to bind an EIP to the cluster during cluster creation. If you want to call an API in DataArts DataService Exclusive locally, you need to use a public IP address to ensure network connectivity.

   -  Input parameters: In this example, an API with various input parameter locations is created to describe how to enter various input parameters during an API call.


      .. figure:: /_static/images/en-us_image_0000002269196261.png
         :alt: **Figure 1** Recording the URL, request method, and input parameters

         **Figure 1** Recording the URL, request method, and input parameters

.. _dataartsstudio_01_0358__section6697113833611:

Calling an API
--------------

#. Start Postman and add an API request.

#. Configure the API request as follows:

   -  Request method and calling URL: Obtain them by referring to :ref:`Obtaining API Information <dataartsstudio_01_0358__section1797493715104>`. If input parameters include Path and Query parameters, you need to change the **{path}** variable in the API calling URL to the value of the Path parameter, and add the value of the Query parameter to the end of the API calling URL in the following format: ?\ **Query** **parameter name**\ =\ **Query parameter value**, for example, **?query=1** in this example.


      .. figure:: /_static/images/en-us_image_0000002269196245.png
         :alt: **Figure 2** Request method and calling URL

         **Figure 2** Request method and calling URL

   -  **Params**: If the Query parameter has been added to the end of the calling URL in the ?\ **Query** **parameter name**\ =\ **Query parameter value** format, the value of **Query Params** is automatically generated. Otherwise, you need to enter a value.


      .. figure:: /_static/images/en-us_image_0000002234236824.png
         :alt: **Figure 3** Params

         **Figure 3** Params

      If you want to customize the calling result, set the following Query parameters:

      -  (Optional) Pagination configuration: By default, the system assigns pagination data to the APIs created using configuration or a script/MyBatis. If you want to obtain specified pagination data, modify the following parameters. **pageSize** indicates the page size, and **pageNum** indicates the page number.


         .. figure:: /_static/images/en-us_image_0000002234236796.png
            :alt: **Figure 4** Pagination parameters

            **Figure 4** Pagination parameters

         .. note::

            For APIs created using a script/MyBatis with custom pagination configuration, the pagination logic is written to the data acquisition SQL statement during API creation. Therefore, the pagination settings cannot be modified during an API call.

      -  (Optional) Sorting configuration: By default, the system provides the default sorting based on the ranking parameters. By default, the custom ranking mode is ascending. To change the sorting, modify the **pre_order_by** parameter. The value of **pre_order_by** is in either of the following formats: **Ranking parameter name**:ASC (ascending order) or **Ranking parameter name**:DESC (descending order). Separate multiple ranking parameter descriptions by semicolons (;).


         .. figure:: /_static/images/en-us_image_0000002234076968.png
            :alt: **Figure 5** Ranking parameters

            **Figure 5** Ranking parameters

         You can change the value of **pre_order_by** as follows:

         -  Delete an optional ranking parameter. The parameter is no longer used for ranking.
         -  Change the ranking mode of a ranking parameter whose ranking mode is custom to ascending or descending. The ranking parameter is sorted based on the new ranking mode.

         .. note::

            The value of **pre_order_by** cannot be changed in any of the following ways. Otherwise, the change does not take effect or an error is reported during API calling.

            -  If a mandatory ranking parameter is deleted, the parameter is still used for ranking and the deletion does not take effect.
            -  Adjustment of the sequence of ranking parameters will not take effect. The sequence of ranking parameters configured during the creation of an API through configuration, a script, or MyBatis will still be used.
            -  If you change the ranking mode of a ranking parameter whose ranking mode is ascending or descending, the API cannot be called. Such a change is not allowed.

      -  (Optional) Number of returned records: If **Return Total Records** is enabled during API creation, it takes a long time to obtain the total number of data records if the data table corresponding to the API contains a large amount of data. In this case, if you do not want the system to calculate and return the total number of data records during an API call, you can modify the **use_total_num** parameter. The **use_total_num** parameter specifies whether to calculate and return the total number of data records. If its value is **1**, the total number of data records is returned. If its value is not **1**, the total number of data records is not returned.


         .. figure:: /_static/images/en-us_image_0000002269196241.png
            :alt: **Figure 6** Number of returned records

            **Figure 6** Number of returned records

   -  **Headers**: Enter parameter **header** and its value.

      .. note::

         By default, Postman automatically selects **Host** and generates a host value from the URI.


      .. figure:: /_static/images/en-us_image_0000002269116177.png
         :alt: **Figure 7** Headers

         **Figure 7** Headers

   -  **Body**: Select the **raw** format and use braces (**{}**) to enclose a string in "**Body parameter name**":**Body parameter value** format, for example, **{"body":4}** in this example.


      .. figure:: /_static/images/en-us_image_0000002234236788.png
         :alt: **Figure 8** Body

         **Figure 8** Body

#. After configuring the API request, click **Send** to send a request to the server and check the returned result. If **"errCode":"DLM.0"** is returned, the API is successfully called. If the API call fails, rectify the fault based on the error message.

   .. note::

      If the API call fails and message "Could not get any response" is displayed, disable **SSL certificate verification** or proxy as prompted, and try again.


   .. figure:: /_static/images/en-us_image_0000002269196237.png
      :alt: **Figure 9** Calling an API

      **Figure 9** Calling an API
