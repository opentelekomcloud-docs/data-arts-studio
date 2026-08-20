:original_name: dataartsstudio_01_0357.html

.. _dataartsstudio_01_0357:

Using an API Tool to Call an API Which Uses IAM Authentication
==============================================================

Before calling an API which uses IAM authentication, call the IAM API for obtaining a user token to obtain the token, which can be used for security authentication.

This section uses Postman as an example to describe how to use an API tool to call an API which uses IAM authentication. The procedure is as follows:

#. :ref:`Obtaining API Information <dataartsstudio_01_0357__section1922472723314>`: Prepare key information of the API.
#. :ref:`Obtaining a Token <dataartsstudio_01_0357__section6697113833611>`: Call the API for obtaining a user token to obtain the token.
#. :ref:`Calling an API <dataartsstudio_01_0357__section6743122154913>`: Use Postman to call the API.

Prerequisites
-------------

-  An API or API workflow using IAM authentication has been published. The published API is available in DataArts Catalog.
-  API authorization has been completed. That is, the API developer has completed the operations in :ref:`Authorizing an API Which Uses IAM Authentication to Apps <dataartsstudio_01_0337>` or :ref:`Authorizing an API Which Uses IAM Authentication Through a Whitelist <dataartsstudio_01_0338>`, or the API caller has completed the operations in :ref:`Applying for API Authorization <dataartsstudio_01_0334>`.

-  Postman has been installed. If it has not been installed, download it from the `Postman official website <https://www.postman.com/>`__ and install it.

Notes and Constraints
---------------------

-  APIs which use IAM authentication authorized to apps of the IAM type can be called only using the token of the current account or those of its users, rather than any other account or user If needed, you can use a whitelist to authorize the APIs to other accounts. For details, see :ref:`Authorizing an API Which Uses IAM Authentication Through a Whitelist <dataartsstudio_01_0338>`.

-  To call an API in DataArts DataService locally, you need to bind an EIP to the DataArts DataService Exclusive cluster when creating the cluster.

-  The validity period of a token is 24 hours. If you use the same token for authentication, cache the token to prevent frequent API calls.

-  When an API in DataArts DataService is called, if the total duration of query and response exceeds 60 seconds (default value), a timeout error is reported. In this case, you can optimize the API configuration based on the API calling duration recorded in the access log.

   .. code-block::

      ____________Duration information__________
      duration: 60491ms //Total duration
      url_duration: 0ms //URL matching duration
      auth_duration: 70ms //Authentication duration
      befor_sql_duration: 402ms //Preprocessing duration before SQL execution
      sql_duration: 60001ms //SQL execution duration
      after_sql_duration:18ms //Postprocessing duration after SQL execution

.. _dataartsstudio_01_0357__section1922472723314:

Obtaining API Information
-------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

#. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

#. Obtain the URL, request method, and input parameters of the API to be called.

   In the navigation pane on the left, choose **APIs**. Locate the API to be called, click the API name to access its details page, and record the URL, request method, and input parameters of the API.

   -  URL for calling the API: The exclusive edition supports both private and public IP addresses. To use the public IP address, you need to bind an EIP to the cluster during cluster creation. If you want to call an API in DataArts DataService Exclusive locally, you need to use a public IP address to ensure network connectivity.

   -  Input parameters: In this example, an API with various input parameter locations is created to describe how to enter various input parameters during an API call.


      .. figure:: /_static/images/en-us_image_0000002269123865.png
         :alt: **Figure 1** Recording the URL, request method, and input parameters

         **Figure 1** Recording the URL, request method, and input parameters

.. _dataartsstudio_01_0357__section6697113833611:

Obtaining a Token
-----------------

#. Start Postman and add an API request.

#. Use an API tool to call the API to obtain the token.

   When calling the API to obtain a user token, you must set **auth.scope** in the request body to **project**.

   .. note::

      In the request, POST https://**IAM endpoint**/v3/auth/tokens is the URL, and Content-Type: application/json is the message header. The content in {} is the request body.

      Configure the bold and italic parameters based on site requirements.

      -  **IAM endpoint** indicates the endpoint of IAM.

         An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. You can obtain endpoints from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

      -  **username** indicates the username, **domainname** indicates the account to which the user belongs, **\*******\*** indicates the login password, and **xxxxxxxxxxxxxxxxxx** indicates the project ID. To obtain the username, account name, and project ID, perform the following steps:

         a. Register with and log in to the management console.
         b. Hover the cursor on the username in the upper right corner and select **My Credentials** from the drop-down list.
         c. On the **API Credentials** page, obtain the account name, account ID, IAM username, and IAM user ID, and obtain the project and its ID from the project list.

   .. code-block:: text

      POST https://IAM endpoint/v3/auth/tokens
      Content-Type: application/json

   .. code-block::

      {
          "auth": {
              "identity": {
                  "methods": [
                      "password"
                  ],
                  "password": {
                      "user": {
                          "name": "username",
                          "password": "********",
                          "domain": {
                              "name": "domainname"
                          }
                      }
                  }
              },
              "scope": {
                  "project": {
                      "id": "xxxxxxxxxxxxxxxxxx"
                  }
              }
          }
      }


   .. figure:: /_static/images/en-us_image_0000002234084656.png
      :alt: **Figure 2** Obtaining a token by calling

      **Figure 2** Obtaining a token by calling

#. Obtain the value of **x-subject-token** in the response header, which is the user token. When calling an API, you can add the token to the request header to obtain the permission to call the API through identity authentication.


   .. figure:: /_static/images/en-us_image_0000002234084648.png
      :alt: **Figure 3** Obtaining a token

      **Figure 3** Obtaining a token

.. _dataartsstudio_01_0357__section6743122154913:

Calling an API
--------------

#. Start Postman and add an API request.

#. Configure the API request as follows:

   -  Request method and calling URL: Obtain them by referring to :ref:`Obtaining API Information <dataartsstudio_01_0357__section1922472723314>`. If input parameters include Path and Query parameters, you need to change the **{path}** variable in the API calling URL to the value of the Path parameter, and add the value of the Query parameter to the end of the API calling URL in the following format: ?\ **Query** **parameter name**\ =\ **Query parameter value**, for example, **?query=1** in this example.


      .. figure:: /_static/images/en-us_image_0000002269203925.png
         :alt: **Figure 4** Request method and calling URL

         **Figure 4** Request method and calling URL

   -  **Params**: If the Query parameter has been added to the end of the calling URL in the ?\ **Query** **parameter name**\ =\ **Query parameter value** format, the value of **Query Params** is automatically generated. Otherwise, you need to enter a value.


      .. figure:: /_static/images/en-us_image_0000002269123857.png
         :alt: **Figure 5** Params

         **Figure 5** Params

      If you want to customize the calling result, set the following Query parameters:

      -  (Optional) Pagination configuration: By default, the system assigns pagination data to the APIs created using configuration or a script/MyBatis. If you want to obtain specified pagination data, modify the following parameters. **pageSize** indicates the page size, and **pageNum** indicates the page number.


         .. figure:: /_static/images/en-us_image_0000002234236796.png
            :alt: **Figure 6** Pagination parameters

            **Figure 6** Pagination parameters

         .. note::

            For APIs created using a script/MyBatis with custom pagination configuration, the pagination logic is written to the data acquisition SQL statement during API creation. Therefore, the pagination settings cannot be modified during an API call.

      -  (Optional) Sorting configuration: By default, the system provides the default sorting based on the ranking parameters. By default, the custom ranking mode is ascending. To change the sorting, modify the **pre_order_by** parameter. The value of **pre_order_by** is in either of the following formats: **Ranking parameter name**:ASC (ascending order) or **Ranking parameter name**:DESC (descending order). Separate multiple ranking parameter descriptions by semicolons (;).


         .. figure:: /_static/images/en-us_image_0000002234076968.png
            :alt: **Figure 7** Ranking parameters

            **Figure 7** Ranking parameters

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
            :alt: **Figure 8** Number of returned records

            **Figure 8** Number of returned records

   -  **Headers**: Enter the value of **x-subject-token** recorded in :ref:`Obtaining a Token <dataartsstudio_01_0357__section6697113833611>` for **X-Auth-Token**, and enter parameter header and its value.

      .. note::

         By default, Postman automatically selects **Host** and generates a host value from the URI.


      .. figure:: /_static/images/en-us_image_0000002234084664.png
         :alt: **Figure 9** Headers

         **Figure 9** Headers

   -  **Body**: Select the **raw** format and use braces (**{}**) to enclose a string in "**Body parameter name**":**Body parameter value** format, for example, **{"body":4}** in this example.


      .. figure:: /_static/images/en-us_image_0000002234244480.png
         :alt: **Figure 10** Body

         **Figure 10** Body

#. After configuring the API request, click **Send** to send a request to the server and check the returned result. If **"errCode":"DLM.0"** is returned, the API is successfully called. If the API call fails, rectify the fault based on the error message.

   .. note::

      If the API call fails and message "Could not get any response" is displayed, disable **SSL certificate verification** or proxy as prompted, and try again.


   .. figure:: /_static/images/en-us_image_0000002269196237.png
      :alt: **Figure 11** Calling an API

      **Figure 11** Calling an API
