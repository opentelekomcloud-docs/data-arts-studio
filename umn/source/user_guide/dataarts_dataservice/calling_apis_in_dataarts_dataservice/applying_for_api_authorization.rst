:original_name: dataartsstudio_01_0334.html

.. _dataartsstudio_01_0334:

Applying for API Authorization
==============================

If you are an API developer and want to call an API which uses app or IAM authentication, you must apply for API authorization.

If you have authorized apps to use the API by following the instructions in :ref:`Authorizing an API Which Uses App Authentication to Apps <dataartsstudio_01_0333>`, :ref:`Authorizing an API Which Uses IAM Authentication to Apps <dataartsstudio_01_0337>`, or :ref:`Authorizing an API Which Uses IAM Authentication Through a Whitelist <dataartsstudio_01_0338>`, skip this section.

Notes and Constraints
---------------------

-  In DataArts DataService Exclusive, APIs which use IAM authentication must be authorized through apps or whitelists so that they can be called.
-  You can only authorize an API through an app rather than a whitelist.
-  APIs using the app authentication can be authorized only to apps of the APP type.
-  APIs using the IAM authentication can be authorized only to apps of the IAM type.

Authorizing an API to Apps
--------------------------

An API that uses app or IAM authentication can be called only after it is authorized. Authorization can be performed by an API developer or an API caller. This section uses the latter as an example.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. Choose **API Calling** > **Service Catalogs** to view all the published APIs.

4. Click the name of the API you want to bind to an app.

5. On the page displayed, click **Permission Application**.

6. On the displayed page, set the expiration time, select an app, and click **OK**.

   .. note::

      If **Parameter Location** was set to **Static** for an input parameter during API creation, you must also set a static parameter value. If no value is set for the static parameter, the default value of the API input parameter will be used when the API is called using an SDK, and an error will be reported indicating that the static parameter value is missing when the API is called using a tool.


   .. figure:: /_static/images/en-us_image_0000002234083148.png
      :alt: **Figure 1** Applying for permissions

      **Figure 1** Applying for permissions

7. The authorization takes effect after the submitted request is approved in the review center.

8. After the authorization is complete, view the bound APIs on the app details page.

   .. note::

      -  In the API list, if you no longer access an API through the app, click **Unbind** in the **Operation** column.
      -  To test an API to which the app is bound, choose **More** > **Debug** in the **Operation** column.
      -  To extend the authorization period for the bound API, click **Renew**.
