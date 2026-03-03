:original_name: dataartsstudio_01_0819.html

.. _dataartsstudio_01_0819:

Configuring Table Permissions (To Be Removed)
=============================================

.. important::

   Data permission capabilities are provided by DataArts Security, and no longer by DataArts Catalog in regions where DataArts Security is available. The data permission functions in DataArts Catalog are available only to existing users.

On the **My Permissions** page, you can view your table and column permissions in the workspace, and apply for or return the permissions.

Workspace admins have the permissions to manage user permissions. An admin can view the resource permissions of all users in the workspace.

Applying for Table or Column Permissions
----------------------------------------

.. note::

   -  The current version supports permissions control only on DLI data tables.
   -  The table or column permissions you applied for take effect only after being approved by reviewers. Therefore, before applying for the permissions, create a reviewer by referring to :ref:`Managing Reviewers <dataartsstudio_01_0820__section143151153934>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

2. Choose **Permissions** > **Data Table Permissions** from the left navigation bar. On the **My Permissions** tab page, click **Apply**.

3. On the page displayed, describe the scenario where the permissions are required, and select the data connection, database, and data table.

4. Select the table or column permissions you want to apply for.

   -  Applying for the permissions of a single table or column

      Select the table or column permissions that you do not have but need to use.

   -  Applying for the permissions of multiple tables or columns

      After selecting multiple tables, select the table or column permissions to be used in the **Permission Details** area.


   .. figure:: /_static/images/en-us_image_0000002234242828.png
      :alt: **Figure 1** Applying for permissions on tables and columns

      **Figure 1** Applying for permissions on tables and columns

5. Click **OK**. Configure a reviewer and click **OK**.

6. Wait for the reviewer to approve the application. After the application is approved, the permissions take effect.

Managing Existing Table Permissions
-----------------------------------

You can manage the table or field permissions you already have, including viewing, editing, and returning permissions.

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

2. Choose **Permissions** > **Table Permissions**. On the **My Permissions** tab page, you can perform the following operations:

   -  Click **View** in the **Operation** column to view the permissions details.
   -  Click **Edit** in the **Operation** column to modify table permissions as needed.
   -  Click **Return** in the **Operation** column to return table permissions as needed.


   .. figure:: /_static/images/en-us_image_0000002269202289.png
      :alt: **Figure 2** Managing table permissions

      **Figure 2** Managing table permissions

Auditing User Permissions
-------------------------

On the **User Permissions** tab page, administrators can view the accounts that have permissions on tables and fields in the same workspace, reclaim the table and field permissions as needed, or grant permissions to users in batches.

.. note::

   Only workspace admins can audit user permissions, including viewing the user list, reclaiming user permissions, or granting permissions to users.

-  Viewing accounts with table permissions and the corresponding asset list

   Choose **Data Table Permissions** > **User Permissions** to view the accounts with applied permissions in the same workspace.


   .. figure:: /_static/images/en-us_image_0000002234083008.jpg
      :alt: **Figure 3** Viewing accounts with table permissions

      **Figure 3** Viewing accounts with table permissions

-  Reclaiming user permissions

   -  Choose **Data Table Permissions** > **User Permissions** and click **Reclaim** under **Operation** to the right of the account to reclaim all its permissions.
   -  On the **User Permissions** tab page, select the check boxes to the left of one or more usernames, and click **Reclaim** in the upper left corner to revoke their permissions in batches.


   .. figure:: /_static/images/en-us_image_0000002269202301.jpg
      :alt: **Figure 4** Reclaiming user permissions

      **Figure 4** Reclaiming user permissions

-  Granting permissions to users


   .. figure:: /_static/images/en-us_image_0000002234242840.jpg
      :alt: **Figure 5** Authorization

      **Figure 5** Authorization

-  Managing user permissions

   Choose **Data Table Permissions** > **User Permissions**, and click the drop-down arrow to the utmost left of an account to display the assets of the user. Click **View**, **Edit**, and **Return** in the **Operation** column to the right of a specific resource as required.


   .. figure:: /_static/images/en-us_image_0000002234082984.png
      :alt: **Figure 6** Managing user permissions

      **Figure 6** Managing user permissions
