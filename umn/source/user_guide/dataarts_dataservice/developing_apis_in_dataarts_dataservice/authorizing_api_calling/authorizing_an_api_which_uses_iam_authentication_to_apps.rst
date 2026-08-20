:original_name: dataartsstudio_01_0337.html

.. _dataartsstudio_01_0337:

Authorizing an API Which Uses IAM Authentication to Apps
========================================================

APIs which use IAM authentication support two authorization modes: app of the IAM type and whitelist. The former can only authorize APIs to the current account, while the latter can authorize APIs to any account. You can choose either mode based on the application scenario.

-  API authorization through apps of the IAM type: An app of the IAM type is the current cloud account. Only one such app can be created for each DataArts Studio instance. Therefore, authorizing an API which uses IAM authentication to an app of the IAM type is authorizing the API to the current account. After authorization, you can obtain the tokens of the current account and its users from IAM. The tokens can be used for security authentication during API calls.
-  API authorization through a whitelist: A cloud account whitelist can be added for an API which uses IAM authentication. Accounts in the whitelist can use the API. After authorization, you can obtain the tokens of the authorized account and its users from IAM. The tokens can be used for security authentication during API calls.

This section describes how to authorize an API to the current account through an app of the IAM type.

Notes and Constraints
---------------------

-  APIs which use IAM authentication authorized to apps of the IAM type can be called only using the token of the current account or those of its users, rather than any other account or user If needed, you can use a whitelist to authorize the APIs to other accounts. For details, see :ref:`Authorizing an API Which Uses IAM Authentication Through a Whitelist <dataartsstudio_01_0338>`.
-  APIs using the IAM authentication can be authorized only to apps of the IAM type.
-  If you authorize apps to call an API without authentication, the system ignores this operation.
-  Only one app of the IAM type can be created for each DataArts Studio instance. The app name is fixed at the a cloud platform account and cannot be changed.
-  In DataArts DataService Exclusive, APIs which use IAM authentication must be authorized through apps or whitelists so that they can be called.

Creating an App of the IAM Type
-------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. Choose **API Calling** > **Apps**. On the page displayed, click **Create**. The **Create App** dialog box is displayed. Set the parameters listed in :ref:`Table 1 <dataartsstudio_01_0337__en-us_topic_0179716875_table195413315428>`.

   .. _dataartsstudio_01_0337__en-us_topic_0179716875_table195413315428:

   .. table:: **Table 1** App information

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                         |
      +===================================+=====================================================================================================================================================================================================================================================================================+
      | App Name                          | App name, which is fixed at the a cloud platform account and cannot be changed.                                                                                                                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Select **IAM**. APIs using the IAM authentication mode can be authorized only to apps of the IAM type.                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                     |
      |                                   | -  **IAM**: APIs using IAM authentication can be authorized to apps of this type. The name of an app of the IAM type is fixed at the a cloud platform account. Only one such app can be created for each DataArts Studio instance and is visible to all workspaces in the instance. |
      |                                   | -  **APP**: APIs using app authentication can be authorized to apps of this type. You can authorize APIs using different app authentication modes to different apps to improve data security.                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the app to create                                                                                                                                                                                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

4. Click **OK**.

   After the app is created, its name and ID are displayed in the application list.

Authorizing an API Which Uses IAM Authentication to the Current Account
-----------------------------------------------------------------------

An API that uses IAM authentication can be called only after it is authorized. Authorization can be performed by an API developer or an API caller. This section uses the former as an example.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. Choose **API Development** > **APIs**.

4. Locate the row that contains an API which uses IAM authentication, click **More** in the **Operation** column, and select **View Authorization**. On the **Complete Information** tab page, click **Assign Authorization**.

5. In the **Authorize Apps** dialog box, set **Expires** and **Cluster**, select IAM apps, and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002234239584.png
      :alt: **Figure 1** Authorize Apps

      **Figure 1** Authorize Apps

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
   :alt: **Figure 2** Batch operation

   **Figure 2** Batch operation
