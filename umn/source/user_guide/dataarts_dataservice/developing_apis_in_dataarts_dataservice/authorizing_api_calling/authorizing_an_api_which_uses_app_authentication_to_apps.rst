:original_name: dataartsstudio_01_0333.html

.. _dataartsstudio_01_0333:

Authorizing an API Which Uses App Authentication to Apps
========================================================

An app defines the identity of an API caller. For an API that uses app authentication, you must create an app of the APP type and authorize the app to use the API to obtain authentication information for calling the API.

An API using app authentication can be authorized to multiple apps of the APP type, and multiple APIs using app authentication can be authorized to the same app of the APP type. After an API is authorized, the key pair (AppKey and AppSecret) of any authorized app can be used for security authentication when the API is called. There are no limitations on the identity of the API caller.

Notes and Constraints
---------------------

-  APIs that use app authentication can be called only after being authorized to apps.
-  APIs using the app authentication can be authorized only to apps of the APP type.
-  If you authorize apps to call an API without authentication, the system ignores this operation.
-  Only the DARTS Administrator, Tenant Administrator, or workspace administrator can reset the AppSecret of an app of the APP type.
-  The APPSecret can be reset only once within one minute. You can view the reset records on the event management page.
-  If the AppSecret is reset, authorized APIs cannot be called. Exercise caution when performing this operation.

Creating an App of the APP Type
-------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. Choose **API Calling** > **Apps**. On the page displayed, click **Create**. The **Create App** dialog box is displayed. Set the parameters listed in :ref:`Table 1 <dataartsstudio_01_0333__en-us_topic_0179716875_table195413315428>`.

   .. _dataartsstudio_01_0333__en-us_topic_0179716875_table195413315428:

   .. table:: **Table 1** App information

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                         |
      +===================================+=====================================================================================================================================================================================================================================================================================+
      | App Name                          | Name of the app to create                                                                                                                                                                                                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Select **APP**. APIs using the APP authentication mode can be authorized only to applications of the APP type.                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                     |
      |                                   | -  **IAM**: APIs using IAM authentication can be authorized to apps of this type. The name of an app of the IAM type is fixed at the a cloud platform account. Only one such app can be created for each DataArts Studio instance and is visible to all workspaces in the instance. |
      |                                   | -  **APP**: APIs using app authentication can be authorized to apps of this type. You can authorize APIs using different app authentication modes to different apps to improve data security.                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the app to create                                                                                                                                                                                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

4. Click **OK**.

   After the app is created, its name and ID are displayed in the application list.

5. Click the app name to view the **AppKey** and **AppSecret** on the displayed app details page. You can reset **AppSecret**.

   .. note::

      If the **AppSecret** is reset, authorized APIs cannot be called. Exercise caution when performing this operation.


   .. figure:: /_static/images/en-us_image_0000002269115461.png
      :alt: **Figure 1** App details page

      **Figure 1** App details page

Authorizing an API Which Uses App Authentication to Apps of the APP Type
------------------------------------------------------------------------

An API that uses app authentication can be called only after it is authorized to apps. Authorization can be performed by an API developer or an API caller. This section uses the former as an example.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. Choose **API Development** > **APIs**.

4. Locate the row that contains an API which uses app authentication, click **More** in the **Operation** column, and select **View Authorization**. On the **Complete Information** tab page, click **Assign Authorization**.

5. In the **Authorize Apps** dialog box, set **Expires** and **Cluster**, select apps, and click **OK**.

   .. note::

      If **Parameter Location** was set to **Static** for an input parameter during API creation, you must also set a static parameter value. If no value is set for the static parameter, the default value of the API input parameter will be used when the API is called using an SDK, and an error will be reported indicating that the static parameter value is missing when the API is called using a tool.


   .. figure:: /_static/images/en-us_image_0000002234076248.png
      :alt: **Figure 2** Authorize Apps

      **Figure 2** Authorize Apps

6. After the authorization is complete, view the bound APIs on the app details page.

   .. note::

      -  In the API list, if you no longer access an API through the app, click **Unbind** in the **Operation** column.
      -  To test an API to which the app is bound, choose **More** > **Debug** in the **Operation** column.
      -  To extend the authorization period for the bound API, click **Renew**.

Related Operations
------------------

Authorizing an API to multiple apps: On the **APIs** page, select APIs, click **Batch Operation** above the list, and select **Authorize**.

.. note::

   You cannot authorize APIs of different authentication modes to apps simultaneously.


.. figure:: /_static/images/en-us_image_0000002269195549.png
   :alt: **Figure 3** Batch operation

   **Figure 3** Batch operation
