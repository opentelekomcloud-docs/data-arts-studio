:original_name: dataartsstudio_01_0338.html

.. _dataartsstudio_01_0338:

Authorizing an API Which Uses IAM Authentication Through a Whitelist
====================================================================

APIs which use IAM authentication support two authorization modes: app of the IAM type and whitelist. The former can only authorize APIs to the current account, while the latter can authorize APIs to any account. You can choose either mode based on the application scenario.

-  API authorization through apps of the IAM type: An app of the IAM type is the current cloud account. Only one such app can be created for each DataArts Studio instance. Therefore, authorizing an API which uses IAM authentication to an app of the IAM type is authorizing the API to the current account. After authorization, you can obtain the tokens of the current account and its users from IAM. The tokens can be used for security authentication during API calls.
-  API authorization through a whitelist: A cloud account whitelist can be added for an API which uses IAM authentication. Accounts in the whitelist can use the API. After authorization, you can obtain the tokens of the authorized account and its users from IAM. The tokens can be used for security authentication during API calls.

This section describes how to authorize an API to an account through a whitelist.

Notes and Constraints
---------------------

-  In DataArts DataService Exclusive, APIs which use IAM authentication must be authorized through apps or whitelists so that they can be called.
-  Only APIs using IAM authentication can be authorized through a whitelist.

Authorizing an API to an Account Through a Whitelist
----------------------------------------------------

An API that uses IAM authentication can be called only after it is authorized.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. Choose **API Development** > **APIs**.

4. Locate the row that contains the API to be authorized to another cloud account, click **More** in the **Operation** column, and select **View Authorization**.

5. Click the **Whitelist Info** tab and click **Create**.

6. In the displayed dialog box, set the tenant name, tenant ID, and authorization expiration time, select a cluster, and click **OK**.

   To obtain the tenant name and tenant ID, log in using the account to be authorized or a user of the account and perform the following steps (the tenant name and ID are the account name and ID, respectively):

   a. Register with and log in to the management console.
   b. Hover the cursor on the username in the upper right corner and select **My Credentials** from the drop-down list.
   c. On the **API Credentials** page, obtain the account name, account ID, IAM username, and IAM user ID, and obtain the project and its ID from the project list.


   .. figure:: /_static/images/en-us_image_0000002234085600.png
      :alt: **Figure 1** Creating a whitelist

      **Figure 1** Creating a whitelist

7. After the authorization is successful, you can view the authorized accounts on the **Whitelists** page.

   .. note::

      If you do not want to authorize the API to an account, click **Delete** in the **Operation** column of the row that contains the tenant name.

Related Operations
------------------

Adding a whitelist for multiple APIs: On the **APIs** page, select APIs, click **Batch Operation** above the API list, and click **Add Whitelist**.

.. note::

   You can add a whitelist only for multiple APIs that use IAM authentication.


.. figure:: /_static/images/en-us_image_0000002269195549.png
   :alt: **Figure 2** Batch operation

   **Figure 2** Batch operation
