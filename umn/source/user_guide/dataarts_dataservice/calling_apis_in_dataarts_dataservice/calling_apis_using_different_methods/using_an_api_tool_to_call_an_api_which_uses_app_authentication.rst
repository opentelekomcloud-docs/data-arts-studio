:original_name: dataartsstudio_01_0356.html

.. _dataartsstudio_01_0356:

Using an API Tool to Call an API Which Uses App Authentication
==============================================================

APIs using app authentication can be bound to different apps, which provides the highest security level. To use an API tool to call an API which uses app authentication, you need to manually generate authentication information using **demo.html** in the JavaScript SDK package.

This section uses Postman as an example to describe how to use an API tool to call an API which uses app authentication. The procedure is as follows:

#. :ref:`Obtaining App and API Information <dataartsstudio_01_0356__section88414974315>`: Prepare key information of the app and API.
#. :ref:`Obtaining the JavaScript SDK Package <dataartsstudio_01_0356__section1731370453>`: Download the JavaScript package and verify its integrity.
#. :ref:`Generating Authentication Information <dataartsstudio_01_0356__section218417910487>`: Generate authentication information manually using **demo.html** in the JavaScript SDK package.
#. :ref:`Calling an API <dataartsstudio_01_0356__section6697113833611>`: Use Postman to call the API.

Prerequisites
-------------

-  An API or API workflow using app authentication has been published. The published API is available in DataArts Catalog.
-  An App has been created and the API has been authorized to the app. That is, the API developer has completed the operations in :ref:`Authorizing an API Which Uses App Authentication to Apps <dataartsstudio_01_0333>`, or the API caller has completed the operations in :ref:`Applying for API Authorization <dataartsstudio_01_0334>`.
-  The static parameter defined in input parameters of the API has been configured during API authorization.
-  Postman has been installed. If it has not been installed, download it from the `Postman official website <https://www.postman.com/>`__ and install it.

Notes and Constraints
---------------------

-  Before calling an API which uses app authentication, you must perform the operations in :ref:`Authorizing an API Which Uses App Authentication to Apps <dataartsstudio_01_0333>` or :ref:`Applying for API Authorization <dataartsstudio_01_0334>`.

-  If a static parameter is defined in input parameters of the API, the static parameter value must be set during API authorization. Otherwise, an error indicating that the static parameter value is missing will be reported when the API is called using a tool.

-  To call an API in DataArts DataService locally, you need to bind an EIP to the DataArts DataService Exclusive cluster when creating the cluster.

-  The validity period of the authentication information generated using **demo.html** is 15 minutes. When the validity period expires, the authentication information becomes invalid.

-  When an API in DataArts DataService is called, if the total duration of query and response exceeds 60 seconds (default value), a timeout error is reported. In this case, you can optimize the API configuration based on the API calling duration recorded in the access log.

   .. code-block::

      ____________Duration information__________
      duration: 60491ms //Total duration
      url_duration: 0ms //URL matching duration
      auth_duration: 70ms //Authentication duration
      befor_sql_duration: 402ms //Preprocessing duration before SQL execution
      sql_duration: 60001ms //SQL execution duration
      after_sql_duration:18ms //Postprocessing duration after SQL execution

.. _dataartsstudio_01_0356__section88414974315:

Obtaining App and API Information
---------------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

#. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

#. Obtain the AppKey and AppSecret of the app authorized by the API. (If multiple apps have been authorized, you only need to obtain information about one of them.)

   In the navigation pane on the left, choose **Apps**. Locate the app to which the API has been authorized, click the app name to access its details page, and record the AppKey and AppSecret.


   .. figure:: /_static/images/en-us_image_0000002269197741.png
      :alt: **Figure 1** Recording the AppKey and AppSecret

      **Figure 1** Recording the AppKey and AppSecret

#. Obtain the URL, request method, and input parameters of the API to be called.

   In the navigation pane on the left, choose **APIs**. Locate the API to be called, click the API name to access its details page, and record the URL, request method, and input parameters of the API.

   -  URL for calling the API: The exclusive edition supports both private and public IP addresses. To use the public IP address, you need to bind an EIP to the cluster during cluster creation. If you want to call an API in DataArts DataService Exclusive locally, you need to use a public IP address to ensure network connectivity.

   -  Input parameters: In this example, an API with various input parameter locations is created to describe how to enter various input parameters during an API call. Static is a static parameter that does not change with the value transferred by the API caller. Therefore, you do not need to set Static when calling an API.


      .. figure:: /_static/images/en-us_image_0000002234238292.png
         :alt: **Figure 2** Recording the URL, request method, and input parameters

         **Figure 2** Recording the URL, request method, and input parameters

.. _dataartsstudio_01_0356__section1731370453:

Obtaining the JavaScript SDK Package
------------------------------------

#. On the DataArts DataService console, choose **SDKs** in the navigation pane. On the displayed page, download the JavaScript SDK.


   .. figure:: /_static/images/en-us_image_0000002234240260.png
      :alt: **Figure 3** Downloading the JavaScript SDK

      **Figure 3** Downloading the JavaScript SDK

#. Verify integrity of the SDK package. In Windows, open the CLI and run the following command to generate the SHA-256 value of the downloaded SDK package. In the command, **D:\\javascript-sdk.zip** is an example local path and name of the SDK package. Replace it with the actual value.

   .. code-block::

      certutil -hashfile D:\javascript-sdk.zip SHA256

   The following is an example command output:

   .. code-block::

      SHA-256 hash value of D:\javascript-sdk.zip
      43da0b54d6b04d1f5ed7f278c2918c2a63a1ddb8048e2d1c5db60baafb17663c
      CertUtil: -hashfile command executed.

   Compare the SHA-256 value of the downloaded SDK with that in the command example. If they are the same, no tampering or packet loss occurred during the package download.

.. _dataartsstudio_01_0356__section218417910487:

Generating Authentication Information
-------------------------------------

#. Decompress the SDK package, double-click the **demo.html** file, set the following parameters, and click **Send request** to view the returned value:

   -  **Key** and **Secret**: AppKey and AppSecret of the app authorized by the API, which can be obtained by referring to :ref:`Obtaining App and API Information <dataartsstudio_01_0356__section88414974315>`.

   -  **Method** and **Url**: API request method and calling URL, which can be obtained by referring to :ref:`Obtaining App and API Information <dataartsstudio_01_0356__section88414974315>`.

      If input parameters include Path and Query parameters, you need to change the **{path}** variable in the API calling URL to the value of the Path parameter, and add the value of the Query parameter to the end of the API calling URL in the following format: ?\ **Query** **parameter name**\ =\ **Query parameter value**, for example, **?query=1** in this example.

   -  **Headers**: Leave it empty even if it has been defined.

   -  **Body**: Use braces (**{}**) to enclose a string in "**Body parameter name**":**Body parameter value** format, for example, **{"body":4}** in this example.


   .. figure:: /_static/images/en-us_image_0000002269119653.png
      :alt: **Figure 4** Generating authentication information

      **Figure 4** Generating authentication information

#. .. _dataartsstudio_01_0356__li3185590485:

   Record the content of **X-Sdk-Date**, **Authorization**, and **X-Authorization** in the return. In this example, you need to copy the following content:

   .. code-block::

      ...
      X-Sdk-Date: 202********55Z
      ...
      Authorization: SDK-HMAC-SHA256 Access=4e7********d6c, SignedHeaders=host;x-sdk-date, Signature=4bf2********4e2
      X-Authorization: SDK-HMAC-SHA256 Access=4e72********d6c, SignedHeaders=host;x-sdk-date, Signature=4bf2********4e2
      ...

.. _dataartsstudio_01_0356__section6697113833611:

Calling an API
--------------

#. Start Postman and add an API request.

#. Configure the API request as follows:

   -  Request method and calling URL: Obtain them by referring to :ref:`Obtaining App and API Information <dataartsstudio_01_0356__section88414974315>`. The values must be the same as those in :ref:`Generating Authentication Information <dataartsstudio_01_0356__section218417910487>`.


      .. figure:: /_static/images/en-us_image_0000002234240268.png
         :alt: **Figure 5** Request method and calling URL

         **Figure 5** Request method and calling URL

   -  **Params**: If the Query parameter has been added to the end of the calling URL in the ?\ **Query** **parameter name**\ =\ **Query parameter value** format, the value of **Query Params** is automatically generated. Otherwise, you need to enter a value.


      .. figure:: /_static/images/en-us_image_0000002269199717.png
         :alt: **Figure 6** Params

         **Figure 6** Params

      If you want to customize the calling result, set the following Query parameters:

      -  (Optional) Pagination configuration: By default, the system assigns pagination data to the APIs created using configuration or a script/MyBatis. If you want to obtain specified pagination data, modify the following parameters. **pageSize** indicates the page size, and **pageNum** indicates the page number.


         .. figure:: /_static/images/en-us_image_0000002234236796.png
            :alt: **Figure 7** Pagination parameters

            **Figure 7** Pagination parameters

         .. note::

            For APIs created using a script/MyBatis with custom pagination configuration, the pagination logic is written to the data acquisition SQL statement during API creation. Therefore, the pagination settings cannot be modified during an API call.

      -  (Optional) Sorting configuration: By default, the system provides the default sorting based on the ranking parameters. By default, the custom ranking mode is ascending. To change the sorting, modify the **pre_order_by** parameter. The value of **pre_order_by** is in either of the following formats: **Ranking parameter name**:ASC (ascending order) or **Ranking parameter name**:DESC (descending order). Separate multiple ranking parameter descriptions by semicolons (;).


         .. figure:: /_static/images/en-us_image_0000002234076968.png
            :alt: **Figure 8** Ranking parameters

            **Figure 8** Ranking parameters

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
            :alt: **Figure 9** Number of returned records

            **Figure 9** Number of returned records

   -  **Headers**: Enter **X-Sdk-Date**, **Authorization**, **X-Authorization**, and their values recorded in :ref:`2 <dataartsstudio_01_0356__li3185590485>` in sequence, and enter **header** and its value.

      .. note::

         By default, Postman automatically selects **Host** and generates a host value from the URI.


      .. figure:: /_static/images/en-us_image_0000002234080440.png
         :alt: **Figure 10** Headers

         **Figure 10** Headers

   -  **Body**: Select the **raw** format and use braces (**{}**) to enclose a string in "**Body parameter name**":**Body parameter value** format, for example, **{"body":4}** in this example.


      .. figure:: /_static/images/en-us_image_0000002234080464.png
         :alt: **Figure 11** Body

         **Figure 11** Body

#. After configuring the API request, click **Send** to send a request to the server and check the returned result. If **"errCode":"DLM.0"** is returned, the API is successfully called. If the API call fails, rectify the fault based on the error message.

   .. note::

      If the API call fails and message "Could not get any response" is displayed, disable **SSL certificate verification** or proxy as prompted, and try again.


   .. figure:: /_static/images/en-us_image_0000002269196237.png
      :alt: **Figure 12** Calling an API

      **Figure 12** Calling an API
