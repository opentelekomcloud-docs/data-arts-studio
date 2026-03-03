:original_name: dataartsstudio_01_0355.html

.. _dataartsstudio_01_0355:

(Recommended) Using an SDK to Call an API Which Uses App Authentication
=======================================================================

APIs using app authentication can be bound to different apps, which provides the highest security level. APIs using app authentication can be called via SDKs of multiple languages, such as Java, Go, Python, JavaScript, C#, PHP, C++, C and Android, helping you easily and quickly obtain open data.

This section uses the Java SDK as an example to describe how to use an SDK to call an API which uses app authentication. The procedure is as follows:

#. :ref:`Obtaining App and API Information <dataartsstudio_01_0355__section1922472723314>`: Prepare key information of the app and API.
#. :ref:`Obtaining the SDK Package <dataartsstudio_01_0355__section6697113833611>`: Download the SDK package and verify its integrity.
#. :ref:`Calling an API Using an SDK <dataartsstudio_01_0355__section16901551175811>`: Modify the SDK code and run it.

Prerequisites
-------------

-  An API or API workflow using app authentication has been published. The published API is available in DataArts Catalog.
-  An App has been created and the API has been authorized to the app. That is, the API developer has completed the operations in :ref:`Authorizing an API Which Uses App Authentication to Apps <dataartsstudio_01_0333>`, or the API caller has completed the operations in :ref:`Applying for API Authorization <dataartsstudio_01_0334>`.
-  Eclipse 3.6.0 or later has been installed. If not, download it from the `Eclipse official website <https://www.eclipse.org/downloads/>`__ and install it.

Notes and Constraints
---------------------

-  Before calling an API which uses app authentication, you must perform the operations in :ref:`Authorizing an API Which Uses App Authentication to Apps <dataartsstudio_01_0333>` or :ref:`Applying for API Authorization <dataartsstudio_01_0334>`.

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

.. _dataartsstudio_01_0355__section1922472723314:

Obtaining App and API Information
---------------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

#. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

#. .. _dataartsstudio_01_0355__li29496402366:

   Obtain the AppKey and AppSecret of the app authorized by the API. (If multiple apps have been authorized, you only need to obtain information about one of them.)

   In the navigation pane on the left, choose **Apps**. Locate the app to which the API has been authorized, click the app name to access its details page, and record the AppKey and AppSecret.


   .. figure:: /_static/images/en-us_image_0000002269197741.png
      :alt: **Figure 1** Recording the AppKey and AppSecret

      **Figure 1** Recording the AppKey and AppSecret

#. .. _dataartsstudio_01_0355__li999843133811:

   Obtain the URL, request method, and input parameters of the API to be called.

   In the navigation pane on the left, choose **APIs**. Locate the API to be called, click the API name to access its details page, and record the URL, request method, and input parameters of the API.

   -  URL for calling the API: The exclusive edition supports both private and public IP addresses. To use the public IP address, you need to bind an EIP to the cluster during cluster creation. If you want to call an API in DataArts DataService Exclusive locally, you need to use a public IP address to ensure network connectivity.

   -  Input parameters: In this example, an API with various input parameter locations is created to describe how to enter various input parameters during an API call. Static is a static parameter that does not change with the value transferred by the API caller. Therefore, you do not need to set Static when calling an API.


      .. figure:: /_static/images/en-us_image_0000002234238292.png
         :alt: **Figure 2** Recording the URL, request method, and input parameters

         **Figure 2** Recording the URL, request method, and input parameters

.. _dataartsstudio_01_0355__section6697113833611:

Obtaining the SDK Package
-------------------------

#. .. _dataartsstudio_01_0355__en-us_topic_0181028495_li929512162120:

   On the DataArts DataService console, choose **SDKs** in the navigation pane. On the displayed page, download the Java SDK.


   .. figure:: /_static/images/en-us_image_0000002234238300.png
      :alt: **Figure 3** Downloading the SDK

      **Figure 3** Downloading the SDK

#. Verify integrity of the SDK package. In Windows, open the CLI and run the following command to generate the SHA-256 value of the downloaded SDK package. In the command, **D:\\java-sdk.zip** is an example local path and name of the SDK package. Replace it with the actual value.

   .. code-block::

      certutil -hashfile D:\java-sdk.zip SHA256

   The following is an example command output:

   .. code-block::

      SHA-256 hash value of D:\java-sdk.zip
      96fced412700cf9b863cb2d867e6f4edf76480bc679416efab88a9e1912503b9
      CertUtil: -hashfile command executed.

   Compare the SHA-256 value of the downloaded SDK package with that provided in the following table. If they are the same, no tampering or packet loss occurred during the package download.

   .. table:: **Table 1** SDK packages and the corresponding SHA-256 values

      +------------+------------------------------------------------------------------+
      | Language   | SHA-256 Value of the SDK Package                                 |
      +============+==================================================================+
      | Java       | 96fced412700cf9b863cb2d867e6f4edf76480bc679416efab88a9e1912503b9 |
      +------------+------------------------------------------------------------------+
      | Go         | f448645da65b4f765d9569fc97ca45dc3e8f1ce4f79d70c5c43934318521d767 |
      +------------+------------------------------------------------------------------+
      | Python     | 54b4984d91db641d2b1b0e77064c162850cb2511a587f95e2f8b8340e7afa128 |
      +------------+------------------------------------------------------------------+
      | C#         | b66caf856ffccb61fe758872aac08876aa33fb0cf5f4790e3bec163593b2cbae |
      +------------+------------------------------------------------------------------+
      | JavaScript | 43da0b54d6b04d1f5ed7f278c2918c2a63a1ddb8048e2d1c5db60baafb17663c |
      +------------+------------------------------------------------------------------+
      | PHP        | 394c068420a3817f32d5d88b6c1632978f573f2a685e4a1d10c2f698e0f6786e |
      +------------+------------------------------------------------------------------+
      | C++        | abae5473d47594f88dcd5eaa0902dc12cd6f1e3bd63c0b82d9d1fab8b4351f54 |
      +------------+------------------------------------------------------------------+
      | C          | a376573fe8aa3a636a6d123926ddc3dca11748b289b8c2c16a5056830a095acb |
      +------------+------------------------------------------------------------------+
      | Android    | c19175d736f05b1945dab4675df19311834ede0d9b1978b11b50c86687baf85c |
      +------------+------------------------------------------------------------------+

.. _dataartsstudio_01_0355__section16901551175811:

Calling an API Using an SDK
---------------------------

#. Decompress the Java SDK package obtained in :ref:`1 <dataartsstudio_01_0355__en-us_topic_0181028495_li929512162120>` and import the SDK to Eclipse.

#. After the SDK is successfully imported, open the **main.java** file, and modify the content shown in the red box in the following figure.


   .. figure:: /_static/images/en-us_image_0000002234238288.png
      :alt: **Figure 4** Modifying the main.java file

      **Figure 4** Modifying the main.java file

   -  Set the request method and URL for calling the API. You can obtain them from :ref:`5 <dataartsstudio_01_0355__li999843133811>`.

      If input parameters include the path parameter, replace the **{path}** variable in the API calling URL with a specific value, for example, 3 in the following code:

      ::

         request.setMethod("POST");
         request.setUrl("https://xx.xx.xx.xx/getPupilInfo/3");

   -  Set the values of Query, Header, and Body parameters.

      Use double quotation marks and braces (**"{}"**) to enclose the string in "**Body parameter name**":**Body parameter value** format and escape the double quotation marks (**""**) using a backslash (\\).

      ::

         request.addQueryStringParam("query", "1");
         request.addHeader("header", "2");
         request.setBody("{\"body\":4}");

   -  (Optional) By default, the system assigns pagination data to the APIs created using configuration or a script/MyBatis. If you want to obtain specified pagination data, modify the following parameters. **pageSize** indicates the page size, and **pageNum** indicates the page number.

      ::

         request.addQueryStringParam("page_size", "100");
         request.addQueryStringParam("page_num", "1");

      .. note::

         For APIs created using a script/MyBatis with custom pagination configuration, the pagination logic is written to the data acquisition SQL statement during API creation. Therefore, the pagination settings cannot be modified during an API call.

   -  (Optional) By default, the system provides the default sorting based on the ranking parameters. By default, the custom ranking mode is ascending. To change the sorting, modify the following parameters. The value of **pre_order_by** is in either of the following formats: **Ranking parameter name**:ASC (ascending order) or **Ranking parameter name**:DESC (descending order). Separate multiple ranking parameter descriptions by semicolons (;).

      ::

         request.addQueryStringParam("pre_order_by", "id:ASC;age:ASC;score:DESC");

      You can change the value of **pre_order_by** as follows:

      -  Delete an optional ranking parameter. The parameter is no longer used for ranking.
      -  Change the ranking mode of a ranking parameter whose ranking mode is custom to ascending or descending. The ranking parameter is sorted based on the new ranking mode.

      .. note::

         The value of **pre_order_by** cannot be changed in any of the following ways. Otherwise, the change does not take effect or an error is reported during API calling.

         -  If a mandatory ranking parameter is deleted, the parameter is still used for ranking and the deletion does not take effect.
         -  Adjustment of the sequence of ranking parameters will not take effect. The sequence of ranking parameters configured during the creation of an API through configuration, a script, or MyBatis will still be used.
         -  If you change the ranking mode of a ranking parameter whose ranking mode is ascending or descending, the API cannot be called. Such a change is not allowed.

   -  (Optional) If **Return Total Records** is enabled during API creation, it takes a long time to obtain the total number of data records if the data table corresponding to the API contains a large amount of data. In this case, if you do not want the system to calculate and return the total number of data records during an API call, you can modify the following parameter settings. The **use_total_num** parameter specifies whether to calculate and return the total number of data records. If its value is **1**, the total number of data records is returned. If its value is not **1**, the total number of data records is not returned.

      ::

         request.addQueryStringParam("use_total_num", "0");

#. Set AppKey and AppSecret. Coded or plaintext AppKey and AppSecret in code pose significant security risks. You are advised to store them in configuration files or environment variables. This example takes environment variables as an example.

   On Eclipse, choose **Run** > **Run Configurations**. In the displayed dialog box, select **Environment** and add variables **SDK_AK** and **SDK_SK**, whose values correspond to the AppKey and AppSecret obtained in :ref:`4 <dataartsstudio_01_0355__li29496402366>`, respectively. Then click **Apply** and **Run** to run the program.


   .. figure:: /_static/images/en-us_image_0000002269197737.png
      :alt: **Figure 5** Configuring the AppKey and AppSecret

      **Figure 5** Configuring the AppKey and AppSecret

#. After running the program, view the API calling result. **"errCode":"DLM.0"** in the 200 message indicates that the API call is successful. If the API call fails, rectify the fault based on the error message.
